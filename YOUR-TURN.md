# Your turn: 20 minutes

After the 10-minute demo, do it for your own product. No product of your own? Keep using Rampwise from the demo and pick a different signal.

**Claude Code or Codex:** type `my turn` and [AGENTS.md](AGENTS.md) walks you through the same steps.

## 0 to 4 minutes: pick your signal

Paste this into your AI and attach [signals/library.csv](signals/library.csv):

```text
I sell: [what your product does, in one or two sentences]
Buyers: [titles, type and size of company, region]
One real customer result: [or "none yet"]
How many companies could buy it: [roughly: hundreds, thousands, tens of thousands]

Read the attached buying-signal library.
Pick the 2 signals most likely to mean a company needs my product NOW.
For each one tell me:
- why, in one sentence, using the "[signal] usually means [change], and [part of my product] helps with that" format;
- pitch or touchpoint for my product;
- how fresh it has to be;
- how you would find 10 companies with it this week (with Clay, and without).
Then name one signal from the library that looks relevant but isn't, and why.
```

If you placed yourself on Mateusz's quadrant during his part (what you sell, and how big your market is), add that as one more line.

Pick one signal.

## 4 to 12 minutes: run it

**In the same chat as the demo,** paste this:

```text
Now run the same six steps for my product and this signal: [the signal you picked].
Write the search, the check, the people search and the messages for my product and buyers.
Show me the search before you run it. Use 5 to 10 companies.
In the check, also note any tool the posting names that already does what I sell.
```

**In a new chat,** paste a demo prompt ([with Clay](demo/prompt-with-clay.md), or version B of [the one without](demo/prompt-no-tools.md#version-b-search-live)), replace THE SELLER and THE SIGNAL with yours, and add the four lines above at the top. The AI rewrites the search, the check and the people search to match. It did in our test.

Keep it to 10 companies or fewer. It's enough to learn from and it saves trial credits.

## 12 to 18 minutes: check and write

1. Open three evidence links yourself. Mark every row where the AI was wrong. Look for the real posting date (page source, `datePosted`) and for any tool they already use for what you sell. In our test, a job post named the competing tool the company already uses, and the AI pitched them anyway.
2. For the rows that hold up, run [the signal-to-message prompt](copy/signal-to-message-prompt.md), or ask your AI to rewrite its messages using it.
3. Run [the swap test](copy/README.md#the-swap-test) on your best message.

## 18 to 20 minutes: bring one to the discussion

Write down three things:

- **Your best message** and the signal behind it.
- **One thing the AI got wrong** that you'd have sent if you hadn't checked.
- **Would you automate this signal?** Why, or why not yet.
