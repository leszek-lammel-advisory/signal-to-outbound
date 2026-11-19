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

## Run 6, 19 November: new message rules in claude.ai

The first messages from runs 3 to 5 all ended with a question like "Who owns that hire's onboarding?" and reused one second line for every company, because the prompt asked for a question "they can answer with yes, no or a name" and gave no offer. The prompts now open with "Hi {first name},", ask for a second line built from what the company sells and to whom, and end with an offer the reader can say yes to.

- **Result:** 10 companies found, 6 kept, a person found at 5. The run took about 5 minutes.
- **Permission clicks:** the AI read the research results about 27 times while it ran, and claude.ai asked for permission each time. Click **Always allow** for Clay.
- **Messages:** every one named who the new rep will be calling and offered a practice call with that buyer. Two of them:

> Hi {first name},
>
> You started as DataGuard's Head of Sales in August and are now hiring an SDR and a BDR in Munich. Two reps learning compliance buyers at once is a heavy ramp; Rampwise trains both on AI role-plays built from your ICP, with weekly coaching. Want a free practice call with an IT security lead facing an ISO 27001 audit?

> Hi {first name},
>
> Saw Haiilo is hiring a Business Development Representative in Hamburg. Your new Hamburg rep will likely be selling the intranet to internal comms and HR leaders, and Rampwise's AI role-plays let them rehearse those conversations before their first live call. Want a free practice call with a Head of Internal Communications for the new hire's first week?

- **Still to check by hand:** three of the five people were in another region than the role (UK, Manchester, New York), and the AI flagged each one.

## Run 7, 19 November: copy rules rebuilt on our copy library

The copy notes, the prompts and the 30 library angles now follow the outbound copy library we use for client campaigns: name what changed, offer something useful for the work it creates, and end with a next step that names what they get. Two fresh agents tested it without seeing how it was written.

- **The demo without tools:** 4 companies kept from the practice file, each message offered a practice call with that company's own buyer (an embedded software lead, an IT lead preparing for ISO 27001, a head of apprentice training, a head of procurement) and ended "Want me to build it?". None claimed onboarding was a problem.
- **The prompt on three made-up briefs:** a French launch named in a job post got a sample translation of one of their product pages, tied to the launch date in the posting. A funding round that didn't say what the money was for was used only to choose whom to write to, and became a plain offer with no invented need. A posting that named the call recording tool the company already uses was skipped.

## Run 8, 19 November: the Clay demo in claude.ai with the rebuilt copy rules

- **Result:** 10 companies found, 7 kept, a person found at 5. About 3 minutes. Only 4 permission prompts this time, because every check finished on the first read. It can still be about 30, so click **Always allow** for Clay.
- **Messages:** all 7 opened "You're hiring...", named what the company sells, offered a practice call with a buyer specific to that company, and ended "Want me to build it?" or "Want me to set one up for them?". None claimed onboarding was a problem. Two of them:

> Hi {first name},
>
> You're hiring a Business Development Representative in Munich to sell your security and compliance platform. I can set up a practice call where the new rep talks to an AI playing an IT lead at a mid-sized company working toward ISO 27001, built from your website. Want me to build it?

> Hi {first name},
>
> You're hiring a Sales Development Representative on-site in Berlin to bring voice documentation to care facilities. I can set up a practice call where the new rep talks to an AI playing the director of a nursing home group, built from your website. Want me to set one up for them?

- **What the copy can't fix:** no posting date was found for any of the 7. Three of them are postings we had already found to be old or re-posted in runs 2 to 5 (Capmo, Alasco, Peec AI). A well-written message about a stale signal is still a stale message: open the links and find the real date before you send.

## Run 9, 19 November: the signal email from the ICP & messaging session

The prompts now write the signal email from the morning's ICP & messaging session (Woodpecker), filled from a `MY CAMPAIGN` block, and end with a ready-to-send CSV.

**With Clay, in claude.ai, the Rampwise example.** About 3 minutes, 6 permission prompts. 10 companies found, 6 kept, a person found at 4. Two of those people had started in the role in the last 6 months, a second signal. Every email followed the template, with line 2 specific to that company's buyers:

> Subject: Munich SDR ramp
>
> Hi {first name},
>
> I saw on your careers page that DataGuard is hiring a Sales Development Representative in Munich.
> New SDRs usually hear their first 'our auditor covers that' from a CISO on a live call. How will you get past that?
> We helped 6 German B2B software companies get new SDRs booking first meetings within 3 weeks without the sales manager running every roleplay.
> Open to see a practice call with a CISO at a mid-sized company facing NIS2?

> Hi {first name},
>
> I saw on your job board that RobCo is hiring a Sales Development Representative in Munich.
> New SDRs usually hear 'robots don't pay off for us' from a plant manager on their first live calls. How will you get past that?
> We helped 6 German B2B software companies get new SDRs booking first meetings within 3 weeks without the sales manager running every roleplay.
> Open to see a practice call with a plant manager at a mid-sized metalworking company?

What still needs you:

- **No posting dates.** Clay found none for the 6, and two of them (Alasco, Peec AI) are postings we already know are old or re-posted. Check `datePosted` before you send.
- **The wrong person.** At one company the person found runs sales for North America from New York; the role is in Düsseldorf. The run flagged it under rows to check by hand.
- **Line 3 is the same in every email.** That's expected when the proof is fixed. It's the one line to make true for your own company.
- **Two evidence links** pointed at a jobs overview or a different country's careers page, not the posting itself.

**Without Clay, version B, a participant's own campaign** (a made-up localisation service for online shops entering new markets): 1 company kept out of 12 checked, in about 7 minutes. 11 of 22 page reads were blocked or gone, and the prompt dropped those rows instead of guessing. The email followed the template and offered to rewrite one of the shop's own product pages for the new market. So: without Clay, expect a short list, and use version A to practise if yours comes back empty.

## Run 10, 19 November: the new setup and build prompts, no Clay, a participant's own campaign

We tested [START.md](../START.md) and [BUILD.md](../BUILD.md) with web search only and a made-up campaign: a service that registers and files EU VAT and OSS for German and Austrian online shops (20 to 200 employees) selling into other EU countries, for a Head of Finance or founder. Proof: none.

- **Setup:** the web search test returned dated Berlin SDR postings with links, so "Setup OK". The library opened from its raw GitHub link.
- **Variants:** A2 (a finance job post that names OSS or cross-border VAT), A6 (expansion to a new EU country) and I1 (an e-invoicing deadline). A2 was picked because job pages carry a date.
- **Graph:** the JSON passed the drawing page's format: 4 stages, 7 steps, two decisions, only known tool ids.
- **Run:** two job board searches, 8 candidates opened, **1 kept**: a Berlin direct-to-consumer health brand whose finance posting (datePosted 22 Oct) lists "Umsatzsteuer (inklusive OSS)" with the tax advisor. No person could be confirmed, so the row names the role. The email:

> Subject: OSS at FORTĒA
>
> Hi {first name},
>
> I saw on arbeitnow that FORTĒA is hiring a Finance Manager in Berlin to handle Umsatzsteuer, including OSS, with your tax advisor.
> Shops selling through Shopify and Amazon usually find the OSS filings grow faster than the finance team. How will you get past that?
> We help direct-to-consumer brands file EU VAT and OSS on time without a full-time tax hire.
> Open to see which EU countries your sales already make you file in, mapped on one page?

What the 7 dropped rows show:

- **Two "fresh" labels were refresh dates.** A board showed "14 hours" for a posting from 28 September and "1 day" for one from June 2025. Only datePosted in the page data told the truth.
- **One posting named the tool that already does the job** (a VAT compliance tool next to DATEV). The rule to drop it worked.
- **One posting had expired** two days earlier (validThrough). BUILD.md now tells the AI to check it.
- **Fit:** one company with 630+ employees, one headquartered in Denmark, one HR platform, one internship post that never mentions VAT.

So: a narrow signal on job boards yields 1 or 2 companies in 15 minutes. Two of the dropped shops (one selling in 19 European countries, one preparing a Swiss market entry) would have fitted the A6 expansion variant better. That is what the variants step is for: ask your AI which signal gives the most checkable companies with your tools, not only which one fits best.

## People

For the 10 companies in run 1, the people search found a sales development leader at 8. The strongest accounts had a second signal: the leader had started in the role recently. SoSafe's Senior SDR Manager started in October 2026, and Peec AI's Head of Sales EMEA in September 2026.

One mismatch worth catching: at Parloa, the contact found manages BDRs for Western Europe, while the open role covers Poland and Eastern Europe. The right person may be someone else.

We left out names on purpose. Your AI will show them to you.

## Example first messages

These are from run 7, before we switched to the signal email (run 9 shows the current format). They follow the signal pattern in [the copy notes](../copy/README.md#3-the-signal-pattern-change-to-practical-help): the change, what Rampwise can give, the next step. After the greeting, that's Mateusz's two lines and one question. Rampwise and its offer are made up.

**SoSafe**, three SDR roles for DACH:

> Hi {first name},
>
> You have three SDR roles open for DACH.
>
> Before their first real calls, I can set up a practice call where the new reps pitch an AI playing a CISO at a German Mittelstand company, built from your website.
>
> Want me to build it?

**DataGuard**, an SDR and a BDR in Munich:

> Hi {first name},
>
> You're hiring an SDR and a BDR in Munich.
>
> I can set up a practice call where each of them pitches an AI playing a data protection officer at a mid-sized company, built from your website, before their first real call.
>
> Want me to build them?

**Tacto**, a BDR in Munich:

> Hi {first name},
>
> You're hiring a Business Development Representative in Munich.
>
> Before the new rep's first live call, I can set up a practice call where they pitch an AI playing a head of procurement at a mid-sized German manufacturer, built from your website.
>
> Want me to build it?

What they leave out on purpose: congratulations, what a new hire "usually" means, and any claim that onboarding is a problem. The company knows what a new rep needs. The offer carries the message.

## Cost

Our trial workspace started with about 1,495 credits. Run 1 cost about 12 credits in total:

- company search: 0;
- research: about 1 per company;
- people search: close to 0;
- one work email lookup: about 0.6 credits, found in about 15 seconds.
