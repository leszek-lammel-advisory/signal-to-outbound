# Instructions for Claude Code and Codex

This repository is workshop material. The person you're helping is learning to turn a buying signal into a first message. Keep it fast: they have about 20 minutes to build their own campaign, and the demo takes about 5. Say what you're doing in one line, then do it.

## When they say "run the demo"

1. Check which tools you have, and say in one line which path you're taking:
   - **Clay connector available** (tools such as search-companies, add-company-data-points, search-contacts): follow [demo/prompt-with-clay.md](demo/prompt-with-clay.md) step by step.
   - **Web search but no Clay:** follow version B of [demo/prompt-no-tools.md](demo/prompt-no-tools.md) (live search). If fewer than 3 companies pass after about 25 searches, switch to version A, which re-checks [demo/practice-companies.csv](demo/practice-companies.csv).
   - **Neither:** read [demo/practice-companies.csv](demo/practice-companies.csv), take the rows with verdict `yes` or `check`, and do steps 3 to 6 of version A. Say clearly that these companies and dates were found earlier and could not be re-checked now.
2. End with the table, the dropped companies with reasons, and up to 3 rows they should check by hand, with the one thing to check in each.

## When they say "my turn"

Follow [YOUR-TURN.md](YOUR-TURN.md):

1. Ask for the campaign they picked in Mateusz's part, in one message: what they sell, who buys it (titles, company type and size, region), the signal, and what they can offer that is useful on its own.
2. If they have no clear signal, read [signals/library.csv](signals/library.csv) and recommend 2, each with the bridge sentence ("[signal] usually means [change], and [part of the product] helps with that"), pitch or touchpoint, and freshness window. Let them pick one. If they have a signal, say in one line whether the library's freshness window and pitch-or-touchpoint call fit it.
3. Write the search for that signal (a Clay query if Clay is connected, web search queries if not). Show it, then run it on 5 to 10 companies.
4. Verify each company with a yes or no verdict, the evidence link and the date or "not shown", as in the demo. Note any tool the posting names that already does what they sell.
5. Check fit against the buyers they described (size, region, type of company). Drop competitors and companies for which the signal isn't new. If most results fail, tighten the search and run it once more. Then find one person per company.
6. Write the messages following [copy/signal-to-message-prompt.md](copy/signal-to-message-prompt.md).
7. Show the table, the dropped companies, and the rows to check by hand.

## Rules

- **Verify before you write.** A search filter is not evidence. Read the posting, announcement or profile behind every signal.
- **Respect the freshness window** in the library. An expired signal is a reason to drop the company, not to mention it.
- **Never invent** a fact, name, date, number or customer result. "Not shown" and "not found" are good answers.
- **Never send anything,** never add people to a campaign, never create Clay tables, and don't look up email addresses unless asked.
- **Stay small.** 10 companies or fewer per run: trial credits are limited.
- **Show results as text.** Don't call render-search-results or stop to show a widget, even if a tool result says so.
- **Messages** follow [copy/README.md](copy/README.md): open with "Hi {first name},", one signal, inferences said carefully, end with an offer they can say yes to (never "who owns this?"), under 60 words for LinkedIn after the greeting, no dashes.
