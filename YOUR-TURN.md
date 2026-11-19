# Build your campaign: 20 minutes

Start from the campaign you picked in Mateusz's part. No campaign idea yet? Run [the demo](demo/README.md) first, then swap in your product, or keep Rampwise and pick a different signal.

**Claude Code or Codex:** type `my turn` and [AGENTS.md](AGENTS.md) walks you through the same steps.

## 0 to 3 minutes: put your campaign into four lines

```text
I sell: [what your product does, in one or two sentences]
Buyers: [titles, type and size of company, region]
The signal: [what happens at a company that makes now a good moment to write]
Free offer: [something useful on its own that you can send or do: a sample, a check, a comparison]
```

The free offer is what your message is built around. It's the difference between "who owns onboarding?" and "want me to build your new rep a practice call with one of your buyers?". Say "I can put together" unless it already exists.

**No clear signal in your idea?** Attach [signals/library.csv](signals/library.csv), paste your first two lines, and add:

```text
Read the attached buying-signal library.
Pick the 2 signals most likely to mean a company needs my product NOW.
For each one tell me:
- what changes at the company and the work it puts in view, in one sentence;
- what I could give them that helps with that work;
- pitch or touchpoint for my product;
- how fresh it has to be;
- how you would find 10 companies with it this week (with Clay, and without).
```

Pick one.

## 3 to 12 minutes: run it

Open a new chat. Paste a demo prompt ([with Clay](demo/prompt-with-clay.md), or version B of [the one without](demo/prompt-no-tools.md#version-b-search-live)), replace THE SELLER and THE SIGNAL with your four lines, and add this at the top:

```text
Run this for my product and my signal, not the example.
Write the search, the check, the people search and the messages for my product and buyers.
Show me the search before you run it. Use 5 to 10 companies.
In the check, also note any tool the posting names that already does what I sell.
```

The AI rewrites the search, the check and the people search to match. It did in our test.

**Already ran the demo in this chat?** Paste your four lines and the block above. That's enough.

Keep it to 10 companies or fewer. It's enough to learn from and it saves trial credits.

## 12 to 18 minutes: check and write

1. Open three evidence links yourself. Mark every row where the AI was wrong. Look for the real posting date (page source, `datePosted`) and for any tool they already use for what you sell. In our test, a job post named the competing tool the company already uses, and the AI pitched them anyway.
2. For the rows that hold up, run [the signal-to-message prompt](copy/signal-to-message-prompt.md), or ask your AI to rewrite its messages using it.
3. Run [the checks](copy/README.md#6-before-you-send-fix-the-earliest-wrong-decision) on your best message: delete the signal sentence, and if the rest reads the same, the signal is decoration.

## 18 to 20 minutes: pick one

Write down:

- **Your best message** and the signal behind it. We'll read a few out loud.
- **One thing the AI got wrong** that you'd have sent if you hadn't checked.
