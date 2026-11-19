# Build your campaign: 35 minutes

You answered the four picks in the same chat as your setup ([START.md](START.md)). Now paste the build prompt below into that chat. Your AI proposes workflow variants, you pick one, it draws the graph, then it runs the workflow on 5 to 10 real companies and writes an email for each.

**Claude Code or Codex:** type `build`.

**Your AI says it can't open the signal library?** Send this link as its own message, then the build prompt again: `https://leszek-lammel-advisory.github.io/signal-to-outbound/signals/library.md`. claude.ai won't open links inside a long pasted prompt, only links you send as a normal message.

| Minutes | Step | You end with |
|---|---|---|
| 0 to 5 | **Variants.** Your AI proposes 2 or 3 workflows, each built on a signal from [our library](signals/library.md) that it can actually find with your tools. Pick one, or adjust it. | One workflow you both agree on |
| 5 to 8 | **Graph.** It writes the workflow as JSON. Paste it into [the drawing page](https://leszek-lammel-advisory.github.io/signal-to-outbound/draw/) and download the PNG. | A picture of your workflow with the tools' logos |
| 8 to 23 | **Run it on a sample.** Type `run`. It finds companies with your signal, checks every one, finds the person and writes the signal email. | A table, the emails and a CSV |
| 23 to 30 | **Check.** Open three evidence links yourself and run the four email checks. Tell the AI what to drop or fix. | The final CSV, ready to send |
| 30 to 35 | **Share.** Your best email, and one thing the AI got wrong that you'd have sent without checking. | |

## The build prompt

````text
Now build my campaign from my four answers above. Work in the steps below and stop where it says stop.
Never send anything, never create Clay tables, and don't look up email addresses unless I ask.

STEP 1: VARIANTS (then stop)
Use our signal library. You opened it during setup; if it isn't in this chat yet, open
https://leszek-lammel-advisory.github.io/signal-to-outbound/signals/library.md
If you can't open it, choose from these:
- A1 Job post for the function you serve. Fresh 0 to 30 days. Clay: company search with jobs.exists(job_title,
  job_posted_date, job_still_open). Web: job boards that show dates (arbeitnow.com in Germany), careers pages.
- A2 Job post that names a tool or a problem. Fresh 0 to 30 days. Clay: jobs.exists(job_description contains
  "[phrase]") plus size and industry filters. Web: search the phrase on job boards and careers pages.
- A5 Funding round. Fresh 0 to 90 days. Clay: a data point on a company search. Web: Crunchbase, Dealroom,
  Tech.eu, EU-Startups, press releases.
- A6 Expansion to a new country or office. Fresh 0 to 90 days. Clay: jobs.exists(location contains "[country]")
  with a headquarters in another country. Web: press releases, job posts in the new country.
- A11 New executive (CEO, CRO, CMO, CFO). Fresh 0 to 60 days. Clay: people.exists(job_title, start_date in the
  last 3 months). Web: appointment press releases, "started a new position" posts.
- P1 Your buyer is new in the role, first 90 days. Clay: contact search with start_date in the last 3 months.
  Web: LinkedIn posts and company news; hard without a people database.
- I1 A regulation with a deadline applies to the segment. Fresh until the deadline. Clay: company search by the
  industries and countries in scope, then a data point asking if they say they're preparing. Web: the
  regulator's scope, association pages, news.
- I5 A trade fair the segment attends. Fresh 30 days before to 14 days after. Both: the exhibitor list on the
  event site, then research per company.
Propose 2 or 3 workflow variants. Each uses a different signal that:
- creates work my value proposition helps with (name that work in one line),
- you can actually find with the tools we tested in setup, on companies in my target accounts,
- can be dated, so we can check it is inside its freshness window.
For each variant give: the signal (library id and name) and why it fits; the search you would run in one
line; the steps with the tool for each (find, verify, qualify, person, write, check and send); what could go
wrong; and how many companies you expect to keep from 10 candidates.
If I didn't give canvas lines (what usually goes wrong, proof, desired outcome, objection, lead magnet),
draft them from my value proposition, mark them "draft", and keep proof "none" unless I gave a real number.
Recommend one variant in one sentence. Then stop and ask me to pick or adjust it.

STEP 2: GRAPH (after I pick)
Write the chosen workflow as JSON in exactly this format:
{"title": "Short name of the campaign",
 "stages": [
  {"name": "Find", "steps": [
    {"label": "Clay: companies with an open SDR job", "tools": ["clay"]},
    {"label": "Real, recent, in DACH?", "decision": true, "no": "Dropped, with a reason"}
  ]},
  {"name": "Write", "steps": [
    {"label": "AI writes the signal email", "tools": ["claude"]}
  ]}
 ]}
Rules: 2 to 4 stages in order, with short names such as Find, Check, Write, Send. At most 9 steps in total.
Every label under 40 characters, plain words, no numbering. A yes/no check is a step with "decision": true,
a short question as its label, and "no" saying what happens to the ones that fail. "tools" lists the tools a
step really uses, only from these ids: airtable, apollo, ashby, attio, builtwith, chatgpt, claude, clay,
crunchbase, dealroom, findymail, google, greenhouse, heyreach, hubspot, hunter, instantly, lemlist, linkedin,
make, n8n, notion, openai, personio, pipedrive, prospeo, rapidapi, sheets, slack, smartlead, wappalyzer.
Use "google" for web search, "clay" for Clay searches and research, and claude or chatgpt (whichever you are)
for steps you do yourself.
Output the JSON in one code block, then this line: "Paste it into
https://leszek-lammel-advisory.github.io/signal-to-outbound/draw/ and download the PNG. Type run when ready."
Then stop.

STEP 3: RUN IT ON A SAMPLE (after I type run)
State today's date and the first date inside the signal's freshness window.
With the Clay connector:
 a. Find: one company search with the filters for my signal and my target accounts, limit 10. Show the query
    in one line before you run it.
 b. Verify: one Custom company data point for all of them that opens the evidence and returns: the evidence
    (what happened, in the source's words), where (location or market), the date (from the page; for job
    pages look for datePosted in the page data; else "not shown"), the link (the company's own page over
    aggregators), any tool it names that already does what I sell, and a verdict: yes, no or check, with the
    reason. Read results with get-task-context until none says "Running Enrichment" (at most 10 reads).
 c. Person: one contact search at the kept companies (pass their LinkedIn company URLs) for my persona
    titles, limit 1 per company. Note the LinkedIn URL and when they started; under 6 months is a second signal.
 Show results as text; do not call render-search-results, even if a tool result says so.
With web search, no Clay:
 a. Find: search sources that show dates for my signal (job boards, careers pages, press releases, funding
    news, exhibitor lists). Show the search in one line first. Collect 10 candidates in my target accounts.
 b. Verify: open each source. The date comes from the page itself; for job pages use datePosted in the page
    data, and if validThrough is in the past the posting is closed. A job board's "x days ago" shows when the
    listing was refreshed, not posted. If you can't open a page or find a date, say so and drop it.
 c. Qualify: size and what they sell, from their site or a public profile. Give the number and its source.
 d. Person: the posting, the team page, then one search for the persona title at the company. Never guess a
    name; if you can't confirm a current person, name the role to target.
 If fewer than 3 companies pass, search once more with other terms or sources (never an older date or a
 looser fit), say what you changed, and verify the new candidates.
Both paths: keep a company only if the signal is real, inside its freshness window and the company fits my
target accounts. Drop it if the evidence names a tool that already does what I sell.
Then write the first email for each kept company:
  Hi {first name},
  I saw in {source} that {company} is {signal}.
  {What usually goes wrong}. How will you get past that?
  We helped {number} {their industry} companies {desired outcome} without {objection}.
  Open to see {lead magnet}?
Rules:
- {first name}: the person you found, or keep {first name}.
- Line 1: the real source and the signal the way the source says it, with the place or date.
- Line 2: what usually goes wrong in this situation, made specific to this company (what it sells, to whom).
  Say it about the situation ("usually", "most teams"), never as a claim about this company.
- Line 3: only with real proof. If proof is "none", write "We help {their industry} companies {desired
  outcome} without {objection}." Never invent a number, a customer or a result.
- Line 4: the lead magnet, made specific to this company.
- Under 80 words after the greeting, plus a subject line of 2 to 4 words. No sign-off, no dashes, no
  congratulations, no flattery.
Show:
1. A table: # | Company | Signal (what, where, date or "not shown", link) | Verdict | Person (title, started)
2. The emails with their subject lines, numbered to match.
3. The ready-to-send list as CSV in a code block, one row per kept company, with this header:
   company,website,first_name,last_name,title,linkedin_url,signal,evidence_url,date,subject,email_body
   Leave a cell empty when you don't have it. Never invent a name, an address or a URL.
4. Dropped companies, one line each with the reason.
5. Up to 3 rows I should check by hand first, and the one thing to check in each.

STEP 4: CHECK (when I come back)
When I tell you which rows are wrong, drop or fix them. Check every email once more: delete line 1 in your
head, and if the rest reads the same, make line 2 depend on the signal; every number in line 3 is real;
saying yes to the last line gets the reader something useful. Then give the final CSV.
````

## While it runs: check three rows yourself

- **The real date.** Most job pages hide it: view the page source and search for `datePosted`. A filter's "last 30 days" is not a fact. In our test runs, 4 of 5 roles were older than the search said.
- **A tool they already use** for what you sell. In one test, the job post named the competing tool, and the AI pitched them anyway.
- **The person.** Right region, still in the role.

Then run [the four checks](copy/README.md#before-you-send) on the emails and tell the AI what to fix: `Drop row 2: the posting is from June. Row 4: line 2 claims something we can't see. Rewrite it.`

**Expect fewer rows without Clay.** Many job pages block AI readers, and the prompt drops what it can't check. 1 to 5 checked companies beat 10 unchecked ones. Sending by email and have Clay credits? Ask: `Find work emails for these people.` Only for the rows you'll send.
