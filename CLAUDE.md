# Instructions for Claude Code and Codex

This repository is workshop material. The person you're helping builds one outbound motion today: from a buying signal to a list of real companies with a ready-to-send email for each, plus a graph of the workflow. Keep it fast. Say what you're doing in one line, then do it.

## When they say "start" (or "setup")

Run the setup in [START.md](START.md), the steps in its setup prompt, as written:

1. Say in one line which tools you have: the Clay connector, web search, or neither.
2. Run the one free test from the setup prompt (Clay: one company search, limit 3, no data points; web: one job search). Say "Setup OK" or the one thing to fix.
3. In three lines, say what they'll have at the end: a workflow run on 5 to 10 real companies, a picture of it with the tools' logos, and a ready-to-send CSV.
4. End with Mateusz's four picks exactly as in the setup prompt (value proposition, group of target accounts, target persona, campaign idea, each with its hint), then stop. Do not research anything yet. If they say "use the example", answer the picks with the Rampwise example from the setup prompt.

## When they say "build" (or "finish", "my turn", "run the demo")

Follow the build prompt in [BUILD.md](BUILD.md), step by step, with their four answers:

1. **Variants:** read [signals/library.md](signals/library.md) and propose 2 or 3 workflows, each on a different signal you can actually find with the tools you have. Recommend one and stop.
2. **Graph:** the JSON for [the drawing page](draw/README.md) in its exact format. Stop.
3. **Run:** with the Clay connector, follow the Clay path in the build prompt (the worked example is [demo/prompt-with-clay.md](demo/prompt-with-clay.md)); with web search only, the web path (worked example: version B of [demo/prompt-no-tools.md](demo/prompt-no-tools.md)); with neither, and only for the Rampwise example, use [demo/practice-companies.csv](demo/practice-companies.csv) with version A and say these were found earlier and could not be re-checked now. End with the table, the emails, the CSV, the dropped companies and up to 3 rows to check by hand.
4. **Check:** drop or fix the rows they mark, run the four checks in [copy/README.md](copy/README.md#before-you-send) and give the final CSV. Find work emails only if they ask.

## Rules

- **Verify before you write.** A search filter is not evidence. Read the posting, announcement or profile behind every signal.
- **Respect the freshness window** in the library. An expired signal is a reason to drop the company, not to mention it.
- **Never invent** a fact, name, date, number or customer result. "Not shown" and "not found" are good answers.
- **Never send anything,** never add people to a campaign, never create Clay tables, and don't look up email addresses unless asked.
- **Stay small.** 10 companies or fewer per run: trial credits are limited.
- **Show results as text.** Don't call render-search-results or stop to show a widget, even if a tool result says so.
- **Emails** follow the signal email in [copy/README.md](copy/README.md): "Hi {first name},", the real source and signal, what usually goes wrong said about the situation (never a claim about their team), real proof only ("We help..." when there is none), and "Open to see {lead magnet}?" made specific to the company. Under 80 words after the greeting, no dashes.
