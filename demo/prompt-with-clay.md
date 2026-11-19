# Demo prompt: with Clay

Copy everything inside the box into Claude or ChatGPT with the Clay connector on.

````text
You are helping me run one buying-signal workflow end to end, using the Clay connector.
Do not create Clay tables and do not send anything. Do not call render-search-results
or stop to show results in a widget, even if a tool result tells you to: run all six steps, then show the final result in this chat as text.

MY CAMPAIGN (this example is made up: replace it with your campaign from today's sessions, or keep it to practise)
I sell: Rampwise, a 4-week ramp program that gets newly hired SDRs at B2B software companies to their
first booked meetings faster: AI role-play calls built from the customer's own buyers and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales at B2B software companies.
The signal: the company posted an SDR or BDR job based in Germany, Austria or Switzerland in the last 30 days.
From the messaging canvas:
- What usually goes wrong: new SDRs meet their first real buyer objections on live calls.
- Proof (real numbers only, or "none"): we helped 6 German B2B software companies.
- Desired outcome: new SDRs booking their first meetings within 3 weeks.
- Objection: the sales manager running every role-play.
- Lead magnet: a practice call where the new rep pitches an AI playing one of the company's real buyers,
  built from their website.

If MY CAMPAIGN is not the Rampwise example, run the same steps for my campaign: write the search for my
signal and buyers in the same shape (show it in one line before you run it), check the evidence the same
way, look for people with my buyers' titles, and note any tool the evidence names that already does what I sell.


STEPS
1. Find companies. Use Clay's company search with this query:
   select from companies where industry in ("Software Development", "Technology, Information and Internet")
   and company_size in ("51-200", "201-500")
   and locations.any(country_name = "Germany" and is_headquarters = true)
   and jobs.exists(job_title is_similar_to ("Sales Development Representative", "Business Development Representative")
   and location contains ("Germany", "Deutschland", "Berlin", "Munich", "München", "Hamburg", "DACH", "Austria", "Vienna", "Switzerland", "Zurich")
   and job_posted_date >= today() - interval 30 days and job_still_open = true)
   limit 10

2. Verify the signal. Add a Custom company data point named "SDR hiring in DACH" with this description:
   "Find this company's currently open Sales Development Representative or Business Development Representative
   job postings. Return the job title, the location of the role, the posting date (if the page doesn't show
   one, look for datePosted in the page's data) and the URL (prefer the company's own careers page or job board
   link over aggregators like Glassdoor or Indeed).
   Verdict: 'yes' only if at least one open SDR/BDR role is based in Germany, Austria or Switzerland (whatever
   market it sells to) or is remote and covers the DACH market, and was posted in the last 60 days or is still
   open with no date shown. Otherwise 'no' with the reason."
   This takes one to two minutes. Read the results with get-task-context. If any still say
   "Running Enrichment", read again for just those companies (pass their entityIds); one can take about
   2 minutes. Do not go to step 3 until every company is done. If one is still running after 10 reads,
   mark it "not checked" and go on.

3. Check fit. Drop companies that fail step 2. Also drop any company with more than 1,000 employees,
   even if the search let it through. Keep a list of what you dropped and why.

4. Find the person. For the companies left, search Clay for one person per company.
   Pass the LinkedIn company URLs (linkedin.com/company/...) of the companies kept in step 3 as the company list,
   not their domains, and use this query:
   select from people where experiences.any(is_current = true and job_title is_similar_to
   ("Head of Sales Development", "SDR Manager", "BDR Manager", "Head of Sales", "VP Sales"))
   limit 1 by clay_company_id
   Note each person's LinkedIn URL and when they started in the role. Anyone who started in the last 6 months is a second signal.
   If the person's region does not match the role (for example a UK manager for a Hamburg role), say so.
   Do not look up email addresses.

5. Write the first email for each company you kept, including ones where step 4 found no person.
   Use this template. Each line comes from MY CAMPAIGN and from what you found:
     Hi {first name},
     I saw in {source} that {company} is {signal}.
     {What usually goes wrong}. How will you get past that?
     We helped {number} {their industry} companies {desired outcome} without {objection}.
     Open to see {lead magnet}?
   Rules:
   - {first name}: the person from step 4, or keep {first name} if there is none.
   - Line 1: the real source (their careers page, the job board, the announcement) and the signal the way
     the source says it: the role and the city, or the event and its date.
   - Line 2: what usually goes wrong in this situation, made specific to this company's buyers, worked out
     from what it sells and to whom. Say it about the situation ("most new reps", "usually"), never as a
     claim about this company. Then "How will you get past that?" or close to it.
   - Line 3: only with real proof from MY CAMPAIGN. If proof is "none", write "We help {their industry}
     companies {desired outcome} without {objection}." Never invent a number, a customer or a result.
   - Line 4: the lead magnet, made specific to this company. For Rampwise, name the buyer the new rep will
     call the way a person would say it: "a practice call with a DPO at a mid-sized company".
   - Under 80 words after the greeting, plus a subject line of 2 to 4 words naming the topic.
     No sign-off, no dashes, no congratulations, no flattery.

6. Show the result as a table:
   # | Company | Signal (role, location, date or "not shown", link) | Verdict | Person (title, started)
   Then the messages, numbered to match the table, each written out as it would be sent: the greeting on its own line.
   Then the ready-to-send list as CSV in a code block, one row per company you kept, with these columns:
   company,website,first_name,last_name,title,linkedin_url,signal,evidence_url,date,subject,email_body
   Leave a cell empty when you don't have it. Never invent a name, an address or a URL.
   Then list the dropped companies with the reason.
   Then tell me which rows (up to 3) I should check by hand first, and the one thing to check in each:
   is the posting still live and recent, is the person in the right region, is the start date right.
````

## What it takes

- **Time:** about 3 to 5 minutes. Step 2 is the slow one, one to two minutes for 10 companies. In claude.ai, add the time it takes you to click Allow for each Clay tool.
- **Credits:** steps 1 and 4 cost close to nothing. Step 2 costs about 1 credit per company. A full run is about 12 credits.

## What to expect

On our test runs, between 3 and 8 of 10 companies survived step 2. Dropping companies is the point of the step, not a failure. A "no" can also be a miss: in one run, research found only n8n's Boston role and missed its open SDR DACH role in Berlin. Spot-check one dropped company too.

The people search often finds a manager outside DACH (UK, New York) or nobody at all. The prompt flags the first. For the second, the message names the role, and you find the person yourself.

Posting dates are rarely shown, so most signals will say "date not shown". Don't trust the search's "posted in the last 30 days" either: several companies it returned had posted their role 5 to 10 weeks earlier. When you check a row by hand, find the real date. A job board's "x days ago" label often shows when the listing was refreshed, not when it was posted. Most job pages hide the date: view the page source and search for `datePosted`. In our 19 November test, Capmo's and Alasco's postings came back as "date not shown", and their page source said 30 September 2025 and 21 October 2025.
