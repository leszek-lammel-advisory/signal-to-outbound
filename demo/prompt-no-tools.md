# Demo prompt: no extra tools

Copy everything inside the box into Claude or ChatGPT with web search turned on.

````text
You are helping me run one buying-signal workflow end to end, using only web search and reading web pages.
Do not send anything. Show your results in this chat.

THE SELLER (made up, for practice)
Rampwise gets newly hired SDRs at B2B software companies to their first booked meetings faster:
a 4-week ramp program with AI role-play calls built from the customer's own ICP and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales.

THE SIGNAL
The company posted an SDR or BDR job in the last 30 days that is based in Germany, Austria or Switzerland,
or requires German.
What it means: a new SDR starts soon, and until they ramp the seat costs money and books few meetings.

STEPS
Start by stating today's date. Count 30 days back from it.

1. Find 6 to 8 candidate companies: B2B software, headquartered in Germany, Austria or Switzerland,
   roughly 50 to 500 employees. Start with job boards that show dates and open without a login:
   - https://www.arbeitnow.com/?search=sales%20development%20representative
   - https://www.arbeitnow.com/?search=business%20development%20representative
   Then search the web for: "Sales Development Representative" (m/w/d) Berlin OR München OR Hamburg OR Köln OR Wien OR Zürich
   Skip companies headquartered outside DACH, even if the job is in Berlin.

2. Verify each one. Open the posting. Write down the job title, the location, the posting date and the URL.
   - Use the date on the employer's own job page. If it has none, use a job board's date and name the board.
   - Many companies use Ashby. For those, https://api.ashbyhq.com/posting-api/job-board/<company> lists every
     open job with its publish date (the <company> part is the same as in their jobs.ashbyhq.com link).
   - If every job on the employer's board shows the same date, say it may only be a board update.
   - If you cannot open the page or find a date, say so instead of guessing.
   Keep the company only if the role is still open and was posted in the last 30 days.

3. Check fit. Confirm that it sells B2B software and has roughly 50 to 500 employees, using the posting,
   the company's careers or about page, or its Crunchbase, Built In or Welcome to the Jungle profile
   (LinkedIn usually can't be read). Write the number and its source. Drop the rest and say why.

4. Find the person. Check the posting for who the role reports to, then the company's team page,
   funding press releases and Crunchbase. If the company is itself hiring that manager, say so.
   If you cannot confirm a current person, name the role to target instead. Never guess a name.

5. Write the first message for each company, in English. Rules:
   - Three lines: two short sentences and one direct question. Under 50 words in total.
   - Line 1 names the specific posting (role and city or market). Line 2 says what it likely means for them,
     and how Rampwise helps with that, in plain words.
   - The question is easy to answer with yes, no or a name.
   - Use only facts you found or the seller facts above. No invented numbers, no results, no flattery.

6. Show the result:
   - A table: # | Company | Role, location, date (source) | Link | Employees (source) | Person or role
   - Then the messages, numbered to match the table.
   - Then the dropped companies with the reason.
   - Then up to 3 rows I should check by hand first, and the one thing to check in each.
   If fewer than 6 companies pass, show those and say how many you checked. Do not loosen the rules to reach 6.
````

## What to expect

Web search alone is slower and finds less than Clay. In our test it took a lot of searching to get 7 good companies, and most early hits were stale, closed or too big. If you have fewer than 3 companies after 5 minutes, switch to the practice file below.

## If web search finds too little

Upload [practice-companies.csv](practice-companies.csv) and add this line to the prompt: "Use the companies in the attached file instead of step 1, and re-check the links and dates in step 2."
