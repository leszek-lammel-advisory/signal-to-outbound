# Demo prompt: no extra tools

Two versions. Both need web search turned on.

- **Version B, for your own campaign.** It searches the web live. In a normal chat expect 1 to 5 companies that pass: many job pages block AI readers, and the prompt drops anything it can't check instead of guessing. A short list you checked beats a long one you didn't.
- **Version A, to practise on the example.** It starts from 20 companies we found earlier for the made-up Rampwise campaign ([practice-companies.csv](practice-companies.csv)), so you spend your time checking and writing, not searching. Attach the file, then paste the prompt. Use it if you have no campaign yet, or if version B finds too few.

## Version A: check our list again, live

````text
You are helping me run one buying-signal workflow end to end, using web search and reading web pages.
Do not send anything. Show your results in this chat.

MY CAMPAIGN (this example is made up: replace it with your campaign from today's sessions, or keep it to practise)
I sell: Rampwise, a 4-week ramp program that gets newly hired SDRs at B2B software companies to their
first booked meetings faster: AI role-play calls built from the customer's own buyers and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales at B2B software companies.
The signal: the company posted an SDR or BDR job in the last 30 days that is based in Germany, Austria or Switzerland, or requires German.
From the messaging canvas:
- What usually goes wrong: new SDRs meet their first real buyer objections on live calls.
- Proof (real numbers only, or "none"): we helped 6 German B2B software companies.
- Desired outcome: new SDRs booking their first meetings within 3 weeks.
- Objection: the sales manager running every role-play.
- Lead magnet: a practice call where the new rep pitches an AI playing one of the company's real buyers,
  built from their website.


STEPS
Start by stating today's date. Count 30 days back from it.

1. Read the attached practice-companies.csv. Take the rows where verdict is "yes" or "check".
   The verdict and reason columns are earlier answers: check everything again.

2. Verify each one. Open the posting_url. Is the role still open, and where is it based?
   - For the date, use what the page shows. If it shows nothing, use posting_date_shown and say so.
   - A job board's "x days ago" label often shows when the listing was refreshed, not posted. Don't trust it.
   - LinkedIn links usually can't be opened: mark those "not verified" instead of guessing.
   Keep the company only if the role is still open, based in DACH or requires German, and was posted in the last 30 days.

3. Check fit. Drop any company with more than 500 employees (employees_clay) or that doesn't sell B2B software.

4. Find the person. Check the posting for who the role reports to, then do one search for the company's
   sales development or sales leader. If you cannot confirm a current person, name the role instead.
   Never guess a name. Note their LinkedIn URL if you find it.

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

6. Show the result:
   - A table: # | Company | Role, location, date (source) | Link | Employees | Person or role
   - Then the messages, numbered to match the table, each written out as it would be sent: the greeting on its own line.
   Then the ready-to-send list as CSV in a code block, one row per company you kept, with these columns:
   company,website,first_name,last_name,title,linkedin_url,signal,evidence_url,date,subject,email_body
   Leave a cell empty when you don't have it. Never invent a name, an address or a URL.
   - Then the dropped companies with the reason.
   - Then up to 3 rows I should check by hand first, and the one thing to check in each.
````

## Version B: search live

````text
You are helping me run one buying-signal workflow end to end, using only web search and reading web pages.
Do not send anything. Show your results in this chat.

MY CAMPAIGN (this example is made up: replace it with your campaign from today's sessions, or keep it to practise)
I sell: Rampwise, a 4-week ramp program that gets newly hired SDRs at B2B software companies to their
first booked meetings faster: AI role-play calls built from the customer's own buyers and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales at B2B software companies.
The signal: the company posted an SDR or BDR job in the last 30 days that is based in Germany, Austria or Switzerland, or requires German.
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
Start by stating today's date. Count 30 days back from it.

1. Find 12 candidate companies (about half will fail the date check): B2B software, headquartered in
   Germany, Austria or Switzerland, roughly 50 to 500 employees. Start with this job board, which opens
   without a login:
   - https://www.arbeitnow.com/?search=sales%20development%20representative
   - https://www.arbeitnow.com/?search=business%20development%20representative
   Only if that gives fewer than 12 candidates, search the web for:
   "Sales Development Representative" (m/w/d) Berlin OR München OR Hamburg OR Köln OR Wien OR Zürich
   and keep only results that show a date.
   Skip companies headquartered outside DACH, even if the job is in Berlin.

2. Verify each one. Open the posting. Write down the job title, the location, the posting date and the URL.
   - Use the date on the employer's own job page. If it has none, use a job board's date and name the board.
   - On arbeitnow, ignore the "x days ago" label: it changes when the listing is refreshed.
     Use datePosted from the job page's data. If you cannot see datePosted, mark the date "unverified".
   - If you cannot open the page or find a date, say so instead of guessing.
   Keep the company only if the role is still open and was posted in the last 30 days.

3. Check fit. Confirm that it sells B2B software and has roughly 50 to 500 employees, using the posting,
   the company's careers or about page, or its Crunchbase, Built In or Welcome to the Jungle profile
   (LinkedIn usually can't be read). Write the number and its source. If sources disagree, give the range
   and list it under rows to check by hand. Drop the rest and say why.
   If fewer than 3 companies are left, search once more with other search terms or another job board
   (never an older date or a looser fit), say what you changed, and run steps 2 and 3 on the new candidates.

4. Find the person. Check the posting for who the role reports to, then do one search for the company's
   sales leader. If the company is itself hiring that manager, say so.
   If you cannot confirm a current person, name the role to target instead. Never guess a name.

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

6. Show the result:
   - A table: # | Company | Role, location, date (source) | Link | Employees (source) | Person or role
   - Then the messages, numbered to match the table, each written out as it would be sent: the greeting on its own line.
   Then the ready-to-send list as CSV in a code block, one row per company you kept, with these columns:
   company,website,first_name,last_name,title,linkedin_url,signal,evidence_url,date,subject,email_body
   Leave a cell empty when you don't have it. Never invent a name, an address or a URL.
   - Then the dropped companies with the reason.
   - Then up to 3 rows I should check by hand first, and the one thing to check in each.
   If fewer than 6 companies pass, show those and say how many you checked. Do not loosen the rules to reach 6.
````

## What to expect from version B

In a test on 19 November with about 25 searches and page reads, it found 5 good companies out of 12 checked. Half of the postings that looked fresh on the job board had been posted in September: the "x days ago" label showed when the listing was refreshed. Names were rarely found, so most rows end with a role to target.

With a participant's own campaign (a made-up localisation service for online shops entering new markets), the same day, it kept 1 company out of 12 checked: 11 of its 22 page reads were blocked or gone (Personio pages, rate limits, closed postings), and it dropped those rows instead of guessing. The one email it wrote followed the template and offered to rewrite one of the shop's own product pages for the new market. Narrow signals find fewer companies; that is why version A exists.
