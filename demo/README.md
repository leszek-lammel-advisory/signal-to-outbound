# The 10-minute demo

You run one signal workflow from start to finish for a made-up company. Your AI does the work. Your job is to check it.

## The case

**Rampwise** (made up) gets newly hired SDRs at B2B software companies to their first booked meetings faster. It runs a 4-week ramp program: AI role-play calls built from the customer's own ICP and objections, weekly coaching, and a dashboard for the SDR manager.

- **Sells to:** Heads of Sales Development, SDR or BDR managers, and VPs of Sales at B2B software companies with 50 to 500 employees in Germany, Austria and Switzerland (DACH).
- **The signal:** the company posted an SDR or BDR job for the DACH market in the last 30 days.
- **What the signal means:** a new SDR starts in a few weeks. Until they ramp, the seat costs salary and books few meetings. Someone has to onboard them, usually the SDR manager.
- **Second signal that makes it stronger:** the SDR leader started in the role in the last 6 months, so they are building the team their way.

In Mateusz's terms this is "signal-based at scale": a large market where only the companies with a reason to buy now are worth a message.

## Pick your path

### Path A: Claude or ChatGPT with Clay

1. Create a free Clay account at clay.com if you don't have one. The trial is enough: a full demo run uses about 12 to 25 credits.
2. Connect Clay to your AI:
   - **Claude (claude.ai or the desktop app):** Settings, then Connectors. Find Clay, connect it and sign in to Clay.
   - **ChatGPT:** find Clay in the apps directory, connect it, then mention `@Clay` in your chat.
   - **Claude Code:** run `/plugin marketplace add clay-run/agent-plugins`, then `/plugin install clay@clay-plugins`, then `/clay:setup`.
3. Check it works: ask "Which Clay workspace am I connected to?"
4. Paste [prompt-with-clay.md](prompt-with-clay.md).

You don't build any Clay tables. The connector searches Clay's company, people and job data and runs research for you, and the results come back in the chat.

### Path B: Claude or ChatGPT without Clay

Paste [prompt-no-tools.md](prompt-no-tools.md). Web search must be on. It finds fewer companies than Clay, because it reads job boards one by one, but the flow is identical.

### Path C: Claude Code or Codex

Clone this repo, open the folder and type `run the demo`. [AGENTS.md](../AGENTS.md) picks Path A if Clay is connected and Path B if not.

### Nothing works

Open [practice-companies.csv](practice-companies.csv). It has 20 companies from our run with the job postings already found. Give it to any chatbot together with [prompt-no-tools.md](prompt-no-tools.md), starting from step 3.

## What you should see

A table with one row per company:

| Company | Signal and link | Verdict | Person to contact | First message |
|---|---|---|---|---|

Plus a short list of the companies that were dropped, and why.

## Your job while it runs

Pick three rows and open the job links yourself.

- Is the role really in DACH?
- Is it still open?
- Is it recent?
- Does the person you'd contact own SDR onboarding at that company?

Mark every row where the AI was wrong. That's the most important thing you'll learn today. Our own run is in [last-run.md](last-run.md).
