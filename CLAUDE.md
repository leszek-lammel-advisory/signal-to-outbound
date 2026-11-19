# Instructions for Claude Code and Codex

This repository is workshop material. The person you're helping is turning a buying signal into a list of companies with an email for each, ready to send. Keep it fast. Say what you're doing in one line, then do it.

## When they say "start" (or "run the demo")

1. Ask in one message for their campaign, in the shape of the `MY CAMPAIGN` block in [demo/prompt-with-clay.md](demo/prompt-with-clay.md): what they sell, buyers, the signal, and the five lines from their messaging canvas (what usually goes wrong, proof, desired outcome, objection, lead magnet). If they have none or say "example", use the Rampwise example as it is.
2. Check which tools you have, and say in one line which path you're taking:
   - **Clay connector available** (tools such as search-companies, add-company-data-points, search-contacts): follow [demo/prompt-with-clay.md](demo/prompt-with-clay.md) step by step with their campaign.
   - **Web search but no Clay:** follow version B of [demo/prompt-no-tools.md](demo/prompt-no-tools.md) (live search) with their campaign. For the Rampwise example, if fewer than 3 companies pass after about 25 searches, switch to version A, which re-checks [demo/practice-companies.csv](demo/practice-companies.csv).
   - **Neither:** for the Rampwise example, read [demo/practice-companies.csv](demo/practice-companies.csv), take the rows with verdict `yes` or `check`, and do steps 3 to 6 of version A. Say clearly that these companies and dates were found earlier and could not be re-checked now.
3. End with the table, the emails, the ready-to-send CSV, the dropped companies with reasons, and up to 3 rows they should check by hand, with the one thing to check in each.

## When they say "finish" (or "my turn")

Follow [YOUR-TURN.md](YOUR-TURN.md): help them check three evidence links (real date, a tool they already use, the person's region), drop or fix the rows they mark, run the four checks in [copy/README.md](copy/README.md#before-you-send) on each email, and give the final ready-to-send CSV. Find work emails only if they ask. Then offer the drawing prompt from [draw/README.md](draw/README.md).

## Rules

- **Verify before you write.** A search filter is not evidence. Read the posting, announcement or profile behind every signal.
- **Respect the freshness window** in the library. An expired signal is a reason to drop the company, not to mention it.
- **Never invent** a fact, name, date, number or customer result. "Not shown" and "not found" are good answers.
- **Never send anything,** never add people to a campaign, never create Clay tables, and don't look up email addresses unless asked.
- **Stay small.** 10 companies or fewer per run: trial credits are limited.
- **Show results as text.** Don't call render-search-results or stop to show a widget, even if a tool result says so.
- **Emails** follow the signal email in [copy/README.md](copy/README.md): "Hi {first name},", the real source and signal, what usually goes wrong said about the situation (never a claim about their team), real proof only ("We help..." when there is none), and "Open to see {lead magnet}?" made specific to the company. Under 80 words after the greeting, no dashes.
