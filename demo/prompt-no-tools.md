# Demo prompt: no extra tools

Copy everything inside the box into Claude or ChatGPT with web search turned on.

````text
You are helping me run one buying-signal workflow end to end, using only web search.
Do not send anything. Show your results in this chat.

THE SELLER (made up, for practice)
Rampwise gets newly hired SDRs at B2B software companies to their first booked meetings faster:
a 4-week ramp program with AI role-play calls built from the customer's own ICP and objections,
weekly coaching, and a dashboard for the SDR manager.
Buyers: Head of Sales Development, SDR or BDR Manager, VP Sales.
Example result (made up): a Berlin HR-tech company cut SDR ramp time from 4 months to 7 weeks.

THE SIGNAL
The company posted an SDR or BDR job for the DACH market in the last 30 days.
What it means: a new SDR starts soon, and until they ramp the seat costs money and books few meetings.

STEPS
1. Find 6 to 8 B2B software companies headquartered in Germany, Austria or Switzerland, with 50 to 500
   employees, that have an open SDR or BDR job for the DACH market. Search job boards and applicant
   tracking systems, for example:
   - site:jobs.ashbyhq.com "Sales Development Representative" (Berlin OR Munich OR DACH)
   - site:jobs.personio.de OR site:jobs.personio.com "Sales Development Representative"
   - site:job-boards.greenhouse.io "Business Development Representative" Germany
   - site:join.com "Sales Development Representative"
   - "Sales Development Representative" DACH SaaS on LinkedIn Jobs or StepStone

2. Verify each one. Open the posting. Write down the job title, the location, the posting date if shown,
   and the URL. Keep it only if the role is in DACH or covers the DACH market and is still open.
   If you cannot open the page or cannot find a date, say so instead of guessing.

3. Check fit. Confirm from the company's website or LinkedIn page that it sells B2B software and has
   roughly 50 to 500 employees. Drop the rest and say why.

4. Find the person. Search for the Head of Sales Development, SDR Manager or VP Sales at each company,
   for example: site:linkedin.com/in "SDR Manager" "<company name>".
   If you cannot confirm a current person, name the role to target instead. Never guess a name.

5. Write the first message for each company. Rules:
   - Two short lines and one direct question. Under 50 words.
   - Line 1 names the specific posting (role and market). Line 2 says what it likely means for them,
     and how Rampwise helps with that, in plain words.
   - The question is easy to answer with yes, no or a name.
   - Use only facts you found or the seller facts above. No invented numbers, no flattery.

6. Show the result as a table:
   Company | Signal (role, location, date, link) | Verdict | Person or role | First message
   Then list the dropped companies with the reason.
   Then tell me which 3 rows I should check by hand first, and why.
````

## If web search finds too little

Upload [practice-companies.csv](practice-companies.csv) and add this line to the prompt: "Use the companies in the attached file instead of step 1, and re-check the links in step 2."
