# Prompt: from signal to message

Paste this into Claude or ChatGPT. Fill in the three blocks in capitals. It works for one company or for a table of them. The method behind it is in [the copy notes](README.md).

````text
You write the first outbound message to one person, based on one buying signal.
A message is worth sending only if the reader gets something useful from it.
If the signal doesn't connect to something useful I can offer, say so and write nothing.

MY PRODUCT
What it does (one or two sentences):
Who buys it (titles, type and size of company, region):
From my messaging canvas:
- What usually goes wrong for them:
- Proof (real numbers I can use: how many companies, which industry; or "none"):
- Desired outcome:
- Objection (what usually stops them saying yes):
- Lead magnet (what I can show or send, and whether it exists or I'd build it):

THE SIGNAL
What happened (use the posting's or announcement's own words where you can):
Evidence (link):
Date (or "not shown"):

THE PERSON
Name, title, company:
When they started in this role (or "not known"):

STEPS
1. What happened. Write it in one sentence, keeping who did what, where and when.
   A plan is not a done thing. A job title alone is not a project.
2. Freshness and fit. Skip, with the reason, if the signal is older than 90 days, the evidence
   doesn't support it, or the evidence shows they already use something that does what I sell.
3. The work it puts in view. What work does this change create for this person? Use only what the
   evidence says (a market, a responsibility, a product, a location, a deadline).
   If the event could mean several things (a new leader might change territories, inherit accounts
   or change nothing), don't pick one. Find the detail that decides it, or use the event only to
   choose whom to write to.
   Never diagnose: no "you must be struggling", no "your team is stretched".
4. What I can contribute. What can I give this person that helps with that work? Make it specific to
   them: their buyers, their market, their posting. Say "I have" only for something that exists;
   otherwise "I can put together". If nothing I offer helps with that work, stop:
   "skip: no useful contribution".
5. Pattern. Usually the signal email below. If the signal is too weak to carry the message but the fit is
   real, drop line 1, write a direct offer instead and say so.
6. Write the signal email:
     Hi {first name},
     I saw in {source} that {company} is {signal}.
     {What usually goes wrong}. How will you get past that?
     We helped {number} {their industry} companies {desired outcome} without {objection}.
     Open to see {lead magnet}?
   - Line 1: the real source and the signal the way the source says it. No congratulations.
   - Line 2: what usually goes wrong in this situation, made specific to their buyers or market. Say it about
     the situation ("most", "usually"), never as a claim about this company.
   - Line 3: only with real proof from my product block. If proof is "none", write "We help {their industry}
     companies {desired outcome} without {objection}." Never invent a number, a customer or a result.
   - Line 4: the lead magnet, made specific to this company. "I have" only if it exists, otherwise "we'd build".
   - Under 80 words after the greeting, plus a subject line of 2 to 4 words. No dashes, no flattery.
7. Review it as the reader, and fix the earliest wrong decision, not the wording:
   - Delete line 1. If the rest reads exactly the same, the signal is decoration: back to step 3.
   - Does line 2 claim something about their team that can't be seen from outside? Rewrite it about the situation.
   - Could they say yes and get something useful? If the question only routes me or asks them
     to explain their situation for my benefit, back to step 4.
   - Every fact comes from the signal, the evidence or my product block.

OUTPUT
What happened: [one sentence]
The work it puts in view: [one sentence]
What I can give: [one sentence, marked "have" or "can prepare"]
Pattern: [signal email, or a direct offer, and why]
Email:
[subject line and the email]
````

## Running it on a list

Add this line at the top and paste your table (company, signal, evidence, date, person) underneath:

```text
Do this for every row below. Show the results as a table: company | what happened | what I can give | message. List the skipped rows separately with the reason.
```
