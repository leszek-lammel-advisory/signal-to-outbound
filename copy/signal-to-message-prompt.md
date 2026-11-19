# Prompt: from signal to message

Paste this into Claude or ChatGPT. Fill in the three blocks in capitals. It works for one company or for a table of them. The method behind it is in [the copy notes](README.md).

````text
You write the first outbound message to one person, based on one buying signal.
A message is worth sending only if the reader gets something useful from it.
If the signal doesn't connect to something useful I can offer, say so and write nothing.

MY PRODUCT
What it does (one or two sentences):
Who buys it (titles, type and size of company, region):
What I can give a prospect that is useful on its own (a sample, a list, a practice run, a comparison, a quote),
and whether I already have it or would prepare it:
One real customer result I'm allowed to use (or "none"):

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
5. Pattern. Usually "change to practical help": the change, what I can give, the next step.
   If the signal is too weak to carry the message but the fit is real, write a direct offer instead
   and say so. If my customer result matches their situation, you may add it in one sentence.
6. Write the whole message.
   - Start with "Hi {first name},".
   - Sentence 1: the change or the task they stated, specific enough to recognise. No congratulations.
   - Sentence 2: what I can give them, with the one detail that makes it useful to them
     (whose buyer, which market, built from what). Leave obvious implications unsaid: they know
     what a new hire or a new office means.
   - The question: the next step, naming what they get or decide ("Want me to send it?",
     "If I put together ... for ..., would that be useful?").
     Never ask who owns something, who they report to, whether a hire is on their team,
     whether they are "exploring" something, or for "a quick chat".
   - LinkedIn: aim for under 60 words after the greeting. Email: under 90 words, plus a plain
     subject line naming the topic. Don't cut the link between the change and the offer to hit a number.
   - No dashes, no flattery, no "I hope this finds you well".
7. Review it as the reader, and fix the earliest wrong decision, not the wording:
   - Delete sentence 1. If the rest reads exactly the same, the signal is decoration: back to step 3.
   - Does any sentence claim something about their team that can't be seen from outside? Back to step 1.
   - Could they say yes and get something useful? If the question only routes me or asks them
     to explain their situation for my benefit, back to step 4.
   - Every fact comes from the signal, the evidence or my product block.

OUTPUT
What happened: [one sentence]
The work it puts in view: [one sentence]
What I can give: [one sentence, marked "have" or "can prepare"]
Pattern: [change to practical help, or which other, and why]
Message:
[the message]
````

## Running it on a list

Add this line at the top and paste your table (company, signal, evidence, date, person) underneath:

```text
Do this for every row below. Show the results as a table: company | what happened | what I can give | message. List the skipped rows separately with the reason.
```
