# Our last run

We ran the Rampwise demo through the official Clay connector on a fresh Clay trial on 18 and 19 November 2026. Here's what came back, including what went wrong.

## Run 1, 18 November: a vague question gives wrong answers

- **Search:** Clay's company search for German software companies (51 to 500 employees) with an SDR or BDR job posted in the last 30 days returned 10 companies. Cost: 0 credits.
- **Research question:** "the most recent open SDR or BDR posting: title, date, location, URL". Cost: about 1 credit per company.
- **What came back:** mostly roles outside Germany (London, New York, Prague, Barcelona, Manchester, China) and one posting dated January 2025.

The question asked for the *most recent* posting, not the one *in Germany*, so the research answered the wrong question. At n8n it found a London role. On 19 November, with a better question, it found an SDR DACH role in Berlin at the same company.

**Lesson:** the research step answers exactly what you ask. Put the conditions that matter (market, recency, still open) into the question itself, and ask for a yes/no verdict with a reason.

## Run 2, 19 November: a precise question

- **Search:** the same query, limit 25. It returned 20 companies.
- **Research question:** the one now in [prompt-with-clay.md](prompt-with-clay.md), which asks for DACH roles, recency and a verdict.

**11 of 20 passed, 9 failed.** The full list is in [practice-companies.csv](practice-companies.csv).

| Result | Companies | Why |
|---|---|---|
| Passed | TASKING, Parloa, DataGuard, SoSafe, simpleclub, Tacto, Peec AI, PCG | Open SDR or BDR role in DACH |
| Passed, but check by hand | Shiftmove, n8n, voize | Shiftmove's posting was dated January 2025 in run 1, so it may be always open. n8n has about 1,388 employees, far above the size filter. voize's role is "remote" with no market stated |
| Failed: role outside DACH | AlfaDocs (Milan), Uberall (Spain), Adjust (China), Buynomics (US, UK, Spain, Poland), Flip (US), innoscripta (UK, France, US) | The search matched the job title, not the location |
| Failed: no open role found | Alasco, Usercentrics, Haiilo | The posting may have closed after the search data was collected |

Three things to notice:

1. **A filter is not a fact.** "Posted in the last 30 days" and "51 to 500 employees" were both in the query, and both let through companies that don't match. Company sizes and job dates in any database lag reality.
2. **The same question can give a different answer a day later.** Research is a search, not a lookup. Keep the evidence link so a human can check it.
3. **About half survives.** Plan for it. If you need 100 good accounts, start with 200.

## Run 3, 19 November: testing the prompt end to end

A fresh agent ran the whole Clay prompt as a participant would, limit 10. All steps worked on the first try, and the research step took about a minute for 10 companies. Only 3 of 10 companies passed.

- **6 failed on location.** The search filtered on the company's headquarters, not on where the job was. The roles were in New York, China, the US East Coast, Manchester and France.
- **1 failed on size.** n8n has about 1,388 employees, but Clay's size bucket said 51 to 200. The fit step caught it.
- **No posting dates.** All 10 said "date not shown", so the freshness check could only ask whether the role was still open.
- **Results moved again.** Haiilo had no open role in run 2 and one in Hamburg in run 3. Parloa's role was in Berlin in run 2 and in New York in run 3.

**Fix:** the query in [prompt-with-clay.md](prompt-with-clay.md) now also filters on the job's location. In a test search it removed 5 of the 6 out-of-market companies and brought in 5 new ones in DACH. A full rerun with the fixed prompt passed 8 of 10. The remaining problems were in the people step: a manager in the UK or New York for a German role at 3 companies, nobody found at 3, and one company matched to a different company with a similar domain (fixed by searching people by LinkedIn company URL instead of domain).

## Run 4, 19 November: no Clay, web search only

A second fresh agent ran [prompt-no-tools.md](prompt-no-tools.md) with web search only.

- **The first version of the prompt found almost nothing.** Searches like `site:jobs.ashbyhq.com` were ignored by the search engine and returned aggregators, dead links and big US companies. Most early hits were stale, closed or too big.
- **One job board made it work.** arbeitnow.com lists German job posts with dates and opens without a login. From there the agent found 7 companies that held up, most of them not in Clay's results at all: Superchat, Kertos, Peec AI, vivenu, Packmatic, Kubermatic, amber.
- **It found the dates Clay couldn't.** Several companies Clay's search returned as "posted in the last 30 days" had posted their role much earlier. Checked on the companies' own Ashby job boards: SoSafe on 16 October, n8n's DACH role on 23 September, voize on 4 September.

**Fix:** the prompt now starts from arbeitnow, uses Ashby's public job feed for dates, and stops instead of loosening the rules when too few companies pass.

**Lesson:** "still open" is not "fresh". A role posted 10 weeks ago and still open is a weaker signal, and possibly one they can't fill. Find the real date before you write "you're hiring".

## Run 5, 19 November: a participant's test in claude.ai

We pasted the Clay prompt into a fresh claude.ai chat, as a participant would. It took 4 minutes, including about 90 seconds when Claude was waiting for a permission click hidden under the results table. 8 of 10 companies passed. n8n (1,388 employees) and Haiilo (role posted 78 days earlier) were dropped. Clay found a sales leader at 5 of the 8.

Then we opened three links. Capmo and Alasco were marked "date not shown", but their page source said `datePosted` 30 September 2025 and 21 October 2025: over a year old. DataGuard's page shows no date at all. So 2 of the 3 postings we checked were roles that stay open all year, not new hires.

**Lesson:** a missing date is not a recent date. Look in the page source before you believe a posting is new.

We then ran version A of the no-Clay prompt in a fresh chat with the practice file. It took under 3 minutes and read 21 pages. Only 3 of 11 companies were kept, each with a point to check, because most roles were older than they looked. One surprise: Peec AI's own Ashby board says its SDR role was published on 5 November, but the same posting (same ID) appears on Antler's job board as posted on 30 June. The 5 November date was a re-post. **Even the company's own job board can show a re-post date.**

The same test ran the own-product exercise for a made-up compliance tool. 3 of 10 companies held up, and one job post named the competing tool the company already uses. The AI pitched them anyway. The prompts now ask it to look for that.

## People

For the 10 companies in run 1, the people search found a sales development leader at 8. The strongest accounts had a second signal: the leader had started in the role recently. SoSafe's Senior SDR Manager started in October 2026, and Peec AI's Head of Sales EMEA in September 2026.

One mismatch worth catching: at Parloa, the contact found manages BDRs for Western Europe, while the open role covers Poland and Eastern Europe. The right person may be someone else.

We left out names on purpose. Your AI will show them to you.

## Example first messages

These follow Mateusz's rule of two lines and one direct question. Rampwise and its result are made up.

> Hi {first name}, you took over SDR at SoSafe in October and there are three SDR roles open for DACH right now. We run the first 30 days of ramp for new SDRs, so their manager isn't the one onboarding them. Who's ramping the new hires?

> Hi {first name}, DataGuard has an SDR and a BDR role open in Munich. Two new reps usually means two people booking very little for the first months. Is the ramp plan for them already set?

> Hi {first name}, you joined Peec AI in September and there's an SDR role open in Berlin. The first SDR under a new sales lead usually starts without a written ramp plan. Do you have one yet?

## Cost

Our trial workspace started with about 1,495 credits. Run 1 cost about 12 credits in total:

- company search: 0;
- research: about 1 per company;
- people search: close to 0;
- one work email lookup: about 0.6 credits, found in about 15 seconds.
