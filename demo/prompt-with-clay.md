# Demo prompt: with Clay

Copy everything inside the box into Claude or ChatGPT with the Clay connector on.

````text
You are helping me run one buying-signal workflow end to end, using the Clay connector.
Do not create Clay tables and do not send anything. Do not stop to display search results
in a widget: run all six steps, then show the final result in this chat as text.

THE SELLER (made up, for practice)
Rampwise gets newly hired SDRs at B2B software companies to their first booked meetings faster:
a 4-week ramp program with AI role-play calls built from the customer's own ICP and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales.

THE SIGNAL
The company posted an SDR or BDR job for the DACH market in the last 30 days.
What it means: a new SDR starts soon, and until they ramp the seat costs money and books few meetings.

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
   job postings. Return the job title, the location of the role, the posting date if shown, and the URL
   (prefer the company's own careers page or job board link over aggregators like Glassdoor or Indeed).
   Verdict: 'yes' only if at least one open SDR/BDR role is based in Germany, Austria or Switzerland or covers
   the DACH market, and was posted in the last 60 days or is still open with no date shown.
   Otherwise 'no' with the reason."
   This takes about a minute. Read the results with get-task-context. If any still say
   "Running Enrichment", wait 30 seconds and read again. Do not go to step 3 until every company is done.

3. Check fit. Drop companies that fail step 2. Also drop any company with more than 1,000 employees,
   even if the search let it through. Keep a list of what you dropped and why.

4. Find the person. For the companies left, search Clay for one person per company.
   Pass the companies' domains from step 1 as the company list, and use this query:
   select from people where experiences.any(is_current = true and job_title is_similar_to
   ("Head of Sales Development", "SDR Manager", "BDR Manager", "Head of Sales", "VP Sales"))
   limit 1 by clay_company_id
   Note when each person started in the role. Anyone who started in the last 6 months is a second signal.
   If the person's region does not match the role (for example a UK manager for a Hamburg role), say so.
   Do not look up email addresses.

5. Write the first message for each company. Rules:
   - Three lines: two short sentences and one direct question. Under 50 words in total, in English.
   - Line 1 names the specific posting (role and market). Line 2 says what it likely means for them,
     and how Rampwise helps with that, in plain words.
   - The question is easy to answer with yes, no or a name.
   - Use only facts you found or the seller facts above. No invented numbers, no results, no flattery.
   - If the person started recently, you may use that instead of the posting.

6. Show the result as a table:
   Company | Signal (role, location, date or "not shown", link) | Verdict | Person (title, started) | First message
   Then list the dropped companies with the reason.
   Then tell me which rows (up to 3) I should check by hand first, and the one thing to check in each:
   is the posting still live and recent, is the person in the right region, is the start date right.
````

## What it takes

- **Time:** about 2 to 3 minutes. Step 2 is the slow one, about a minute for 10 companies.
- **Credits:** steps 1 and 4 cost close to nothing. Step 2 costs about 1 credit per company. A full run is about 12 credits.

## What to expect

On our test runs, between a third and a half of the companies survived step 2. That's the point of the step, not a failure.

Posting dates are rarely shown, so most signals will say "date not shown". Don't trust the search's "posted in the last 30 days" either: several companies it returned had posted their role 5 to 10 weeks earlier. When you check a row by hand, find the real date. For companies on Ashby, `https://api.ashbyhq.com/posting-api/job-board/<company>` lists every open job with its publish date.
