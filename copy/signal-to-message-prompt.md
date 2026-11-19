# Prompt: from signal to message

Paste this into Claude or ChatGPT. Fill in the three blocks in capitals. It works for one company or for a table of them.

````text
You write the first outbound message to one person, based on one buying signal.
Your job is to connect the signal to what my product does. If there is no honest connection, say so and write nothing.

MY PRODUCT
What it does (one or two sentences):
Who buys it (titles, type and size of company, region):
The problem it solves, in the buyer's words:
One real customer result (or "none yet"):
What I can offer that is useful on its own (a sample, a comparison, a short audit), if anything:

THE SIGNAL
What happened:
Evidence (link):
Date (or "not shown"):

THE PERSON
Name, title, company:
When they started in this role (or "not known"):

STEPS
1. Decode. In one sentence: what does this signal usually mean for a company like this one?
   What changes for this person in the next 1 to 3 months?
2. Check freshness and fit. If the signal is older than 90 days, the evidence doesn't support it, or the evidence
   shows they already use a tool that does what my product does, stop and say "skip" with the reason.
3. Bridge. Name the one part of my product that helps with exactly that change.
   If nothing fits, stop and say "skip: no honest connection".
4. Choose: pitch (the signal is itself a reason to buy, so name the problem and the offer)
   or touchpoint (the signal is a reason to talk, so ask about their situation and offer something useful, no pitch).
5. Write. Start with "Hi {first name},". Then two short lines and one direct question, under 60 words after the greeting:
   - Line 1: the signal, specific (what, where, when).
   - Line 2: what it likely means for them, said carefully ("usually", "often"), and how my product helps.
   - The question: for a pitch, offer the useful thing from my product block, made specific to them
     ("Want me to send ...?", "If I put together ... for [their situation], would that be useful?").
     For a touchpoint, offer something useful about the change itself, with no pitch.
     If I have nothing useful to offer, ask about the change in a way only they can answer.
   - Never end with "who owns this?", "who should I talk to?", "is that on your team?" or a request for a call.
   For email, you may instead use: "Hi {first name}," / "Saw [observation]." / "We help [type of company] [outcome]. [Real result]." / "Worth sending over [useful asset]?" under 80 words.
6. Check before you show it:
   - Every fact is from the signal, the evidence or my product block. No invented numbers, names or results.
   - Swap test: would this message still make sense sent to a company WITHOUT this signal? If yes, rewrite line 2.
   - The question: could they say yes and get something useful? If it only asks them to route you
     or explain their situation for your benefit, rewrite it.
   - No congratulations, no flattery, no dashes, no "I hope this finds you well".

OUTPUT
Decode: [one sentence]
Bridge: [signal] usually means [change], and [part of product] helps with that.
Pitch or touchpoint: [which, and why]
Message:
[the message]
````

## Running it on a list

Add this line at the top and paste your table (company, signal, evidence, date, person) underneath:

```text
Do this for every row below. Show the results as a table: company | decode | pitch or touchpoint | message. List the skipped rows separately with the reason.
```
