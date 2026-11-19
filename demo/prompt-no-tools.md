# Demo prompt: no extra tools

Two versions. Both need web search turned on.

- **Version A, start here in Claude or ChatGPT.** It starts from 20 companies we found earlier ([practice-companies.csv](practice-companies.csv)), so you spend your time checking and writing, not searching. Attach the file, then paste the prompt.
- **Version B, if you finish early or use Claude Code or Codex.** It searches live. In a normal chat it takes many searches to find 4 or 5 good companies.

## Version A: check our list again, live

````text
You are helping me run one buying-signal workflow end to end, using web search and reading web pages.
Do not send anything. Show your results in this chat.

THE SELLER (made up, for practice)
Rampwise gets newly hired SDRs at B2B software companies to their first booked meetings faster:
a 4-week ramp program with AI role-play calls built from the customer's own ICP and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales.
Free offer: one practice call for the new rep before their first real call. The AI plays one of the
customer's real buyers, built from the customer's website.

THE SIGNAL
The company posted an SDR or BDR job in the last 30 days that is based in Germany, Austria or Switzerland,
or requires German.
What it means: a new SDR starts soon and has to learn this company's buyers. Rampwise can help with
exactly that work: a practice call with one of those buyers before the first real call. The posting
shows the hire, not a problem. Who the buyers are differs by company.

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
   Never guess a name.

5. Write the first message for each company you kept, in English. Rules:
   - Start with "Hi {first name}," using the first name of the person from step 4, or keep {first name} if there is none.
   - Then two sentences and one question, under 60 words after the greeting, in English. No sign-off.
     The pattern: the change, what Rampwise can give them, the next step.
   - Sentence 1 names the posting: the role, the city or market, and what the posting says the rep will do or sell,
     in its own words where you can. Write to them as "you" ("you're hiring", "your posting"), not by their
     company name. No congratulations. A new sales leader only decides whom you write to:
     leave their start date out.
   - Sentence 2 says what Rampwise can prepare for this company: the practice call, naming the buyer the new
     rep will be calling the way a person would say it ("a CFO at a mid-sized retailer"), worked out from what
     the company sells and to whom. Rampwise would build it, so "I can set up", not "I have".
     Each company gets its own sentence 2 because its buyer is different.
   - Don't explain what a new hire means for them or claim a problem you can't see ("new reps usually learn
     on live calls", "onboarding takes your time"). They know.
   - The question names what they get ("Want me to build it?", "Want me to set one up for them?").
     Never ask who owns something, who someone reports to, whether a hire is on their team, whether they
     are exploring something, or for "a quick chat".
   - Use only facts you found or the seller facts above. No invented numbers, no results, no flattery.

6. Show the result:
   - A table: # | Company | Role, location, date (source) | Link | Employees | Person or role
   - Then the messages, numbered to match the table, each written out as it would be sent: the greeting on its own line.
   - Then the dropped companies with the reason.
   - Then up to 3 rows I should check by hand first, and the one thing to check in each.
````

## Version B: search live

````text
You are helping me run one buying-signal workflow end to end, using only web search and reading web pages.
Do not send anything. Show your results in this chat.

THE SELLER (made up, for practice)
Rampwise gets newly hired SDRs at B2B software companies to their first booked meetings faster:
a 4-week ramp program with AI role-play calls built from the customer's own ICP and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales.
Free offer: one practice call for the new rep before their first real call. The AI plays one of the
customer's real buyers, built from the customer's website.

THE SIGNAL
The company posted an SDR or BDR job in the last 30 days that is based in Germany, Austria or Switzerland,
or requires German.
What it means: a new SDR starts soon and has to learn this company's buyers. Rampwise can help with
exactly that work: a practice call with one of those buyers before the first real call. The posting
shows the hire, not a problem. Who the buyers are differs by company.

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

4. Find the person. Check the posting for who the role reports to, then do one search for the company's
   sales leader. If the company is itself hiring that manager, say so.
   If you cannot confirm a current person, name the role to target instead. Never guess a name.

5. Write the first message for each company, in English. Rules:
   - Start with "Hi {first name}," using the first name of the person from step 4, or keep {first name} if there is none.
   - Then two sentences and one question, under 60 words after the greeting, in English. No sign-off.
     The pattern: the change, what Rampwise can give them, the next step.
   - Sentence 1 names the posting: the role, the city or market, and what the posting says the rep will do or sell,
     in its own words where you can. Write to them as "you" ("you're hiring", "your posting"), not by their
     company name. No congratulations. A new sales leader only decides whom you write to:
     leave their start date out.
   - Sentence 2 says what Rampwise can prepare for this company: the practice call, naming the buyer the new
     rep will be calling the way a person would say it ("a CFO at a mid-sized retailer"), worked out from what
     the company sells and to whom. Rampwise would build it, so "I can set up", not "I have".
     Each company gets its own sentence 2 because its buyer is different.
   - Don't explain what a new hire means for them or claim a problem you can't see ("new reps usually learn
     on live calls", "onboarding takes your time"). They know.
   - The question names what they get ("Want me to build it?", "Want me to set one up for them?").
     Never ask who owns something, who someone reports to, whether a hire is on their team, whether they
     are exploring something, or for "a quick chat".
   - Use only facts you found or the seller facts above. No invented numbers, no results, no flattery.

6. Show the result:
   - A table: # | Company | Role, location, date (source) | Link | Employees (source) | Person or role
   - Then the messages, numbered to match the table, each written out as it would be sent: the greeting on its own line.
   - Then the dropped companies with the reason.
   - Then up to 3 rows I should check by hand first, and the one thing to check in each.
   If fewer than 6 companies pass, show those and say how many you checked. Do not loosen the rules to reach 6.
````

## What to expect from version B

In a test on 19 November with about 25 searches and page reads, it found 5 good companies out of 12 checked. Half of the postings that looked fresh on the job board had been posted in September: the "x days ago" label showed when the listing was refreshed. Names were rarely found, so most rows end with a role to target.
