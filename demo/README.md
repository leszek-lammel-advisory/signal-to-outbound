# The demo

You run one signal workflow from start to finish for a made-up company. Your AI does the work. Your job is to check it.

## The case

**Rampwise** (made up) gets newly hired SDRs at B2B software companies to their first booked meetings faster. It runs a 4-week ramp program: AI role-play calls built from the customer's own ICP and objections, weekly coaching, and a dashboard for the SDR manager.

- **Sells to:** Heads of Sales Development, SDR or BDR managers, and VPs of Sales at B2B software companies with 50 to 500 employees in Germany, Austria and Switzerland (DACH).
- **The signal:** the company posted an SDR or BDR job based in Germany, Austria or Switzerland in the last 30 days.
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
5. Claude asks before each Clay tool it uses. Click **Always allow** for Clay. With **Allow once** you'll click about 30 times: while the research runs, the AI checks the results every few seconds, and each check asks again. If it says "running a command" for over a minute and nothing new appears, scroll down or click that line: it's usually waiting for your click.

You don't build any Clay tables. The connector searches Clay's company, people and job data and runs research for you, and the results come back in the chat.

### Path B: Claude or ChatGPT without Clay

Attach [practice-companies.csv](practice-companies.csv) and paste **version A** of [prompt-no-tools.md](prompt-no-tools.md). Web search must be on. It starts from 20 companies we found earlier and checks them again live, so your time goes into checking and writing, not searching. Finished early? Try **version B**, which searches live. It's slow in a chat: in our test it took about 25 searches to find 5 good companies.

### Path C: Claude Code or Codex

Clone this repo, open the folder and type `run the demo`. [AGENTS.md](../AGENTS.md) picks Path A if Clay is connected and a live web search if not.

### Nothing works

Open [practice-companies.csv](practice-companies.csv) and the links in it yourself. It has 20 companies from our runs with the job postings already found. Do the steps by hand: is the role open, where, since when; who would you write to; what would you say.

## What you should see

- A table with one row per company: the job found (role, location, date or "not shown", link) and the person or role to contact.
- A first message for each company.
- The companies that were dropped, and why.
- Up to 3 rows to check by hand, with the one thing to check in each.

## Your job while it runs

Pick three rows and open the job links yourself.

- Is the role really in DACH?
- Is it still open?
- Is it recent? Find the real date: the search's "posted in the last 30 days" is often wrong, and most job pages hide the date. View the page source (Cmd+Option+U on a Mac, Ctrl+U on Windows) and search for `datePosted`. In our 19 November test, 2 of the 3 postings we opened said "date not shown" in the table and were over a year old in the source.
- Does the person you'd contact own SDR onboarding at that company?

Mark every row where the AI was wrong. That's the most important thing you'll learn today. Our own run is in [last-run.md](last-run.md).
