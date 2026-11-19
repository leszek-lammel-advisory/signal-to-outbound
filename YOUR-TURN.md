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

Where you sit on Mateusz's quadrant (what you sell, and how big your market is) matters here. Add it to the prompt.

Pick one signal.

## 4 to 12 minutes: run it

Take a demo prompt ([with Clay](demo/prompt-with-clay.md), or version B of [the one without](demo/prompt-no-tools.md#version-b-search-live)) and change two blocks:

1. **THE SELLER:** your product, from the prompt above.
2. **THE SIGNAL:** the signal you picked, and what it means.

Then add this line before STEPS:

```text
Before step 1, write the search for this signal and show it to me. Use it on 5 to 10 companies only.
```

Keep it to 10 companies or fewer. It's enough to learn from and it saves trial credits.

## 12 to 18 minutes: check and write

1. Open three evidence links yourself. Mark every row where the AI was wrong.
2. For the rows that hold up, run [the signal-to-message prompt](copy/signal-to-message-prompt.md), or ask your AI to rewrite its messages using it.
3. Run [the swap test](copy/README.md#the-swap-test) on your best message.

## 18 to 20 minutes: bring one to the discussion

Write down three things:

- **Your best message** and the signal behind it.
- **One thing the AI got wrong** that you'd have sent if you hadn't checked.
- **Would you automate this signal?** Why, or why not yet.
