# Setup: 3 minutes

Today you build one outbound motion end to end: from a buying signal to a list of real companies with a ready-to-send email for each, plus a graph of your workflow. Set up now, while we talk. You build after Mateusz's talk, in [BUILD.md](BUILD.md).

## 1. Open your AI

- **Have a Clay trial?** Use [claude.ai](https://claude.ai) with the Clay connector on: Settings, Connectors, Clay, Connect. When Claude asks to use a Clay tool, click **Always allow**, or every step stops and waits for you.
- **No Clay?** Use Claude or ChatGPT with web search on.
- **Claude Code or Codex?** Clone this repository, open it and type `start`.

## 2. Paste the setup prompt and send it

It checks your tools with one free test, tells you what you'll build, and ends with four questions. Answer them after Mateusz's talk.

````text
You are my setup assistant for the "Outreach workflows" workshop at GTM Tech Week Berlin.
Today I build one outbound motion end to end: from a buying signal to a list of real companies with a
ready-to-send email for each, plus a graph of the workflow. Right now we only set up: do not search for
companies, research or write anything beyond the four steps below.

1. Tools. Say in one line which I have: the Clay connector (tools such as search-companies,
   add-company-data-points, search-contacts), web search, or neither.

2. Test. Run one small free test and show the result in two lines.
   - Clay connector: one company search for software companies headquartered in Germany with 51 to 500
     employees, limit 3. Only the search: no data points, no contacts, no tables. It costs 0 credits.
     Show the results as text; do not call render-search-results.
   - Web search, no Clay: one search for a Sales Development Representative job in Berlin posted this
     month. Show one result with its link.
   - Neither: say so.
   Then say "Setup OK" or the one thing to fix:
   - Clay tools missing in claude.ai: Settings, Connectors, Clay, Connect, then start a new chat.
   - A permission prompt: click Always allow, or every step will stop and wait for me.
   - No web search: turn it on for this chat, or use ChatGPT with search.
   If the Clay test fails twice, tell me we'll continue with web search only.
   Then open our signal library, which we use when we build:
   https://leszek-lammel-advisory.github.io/signal-to-outbound/signals/library.md
   Say in one line how many signals it lists, or that it didn't open.

3. Today. In three short lines, tell me what I'll have at the end:
   a workflow from one signal to a ready-to-send list, run by you on 5 to 10 real companies;
   a picture of that workflow with the tools' logos;
   a CSV with each company, the person, the evidence and a signal email.

4. End with exactly this, then stop and wait:

   Pick one of each to build an outbound campaign:
   1. Value proposition: what you sell and the outcome it gets. (Your messaging canvas, ICP & messaging session)
   2. Group of target accounts: which companies, what size, where. (Your ICP, RevOps foundations session)
   3. Target persona: the job titles that buy it. (Your messaging canvas)
   4. Campaign idea: why these accounts, why now, and the signal if you have one. (Designing a lead gen
      campaign, and Timing & buying signals)
   Answer these after Mateusz's talk. Add your canvas lines if you have them: what usually goes wrong,
   proof (real numbers or "none"), desired outcome, objection, lead magnet.
   No campaign? Type: use the example

If I type "use the example", answer the four picks with this made-up campaign and say we're ready to build:
1. Rampwise, a 4-week ramp program that gets newly hired SDRs to their first booked meetings faster:
   AI role-play calls built from the customer's own buyers and objections, weekly coaching, a dashboard.
2. B2B software companies headquartered in Germany, Austria or Switzerland, 50 to 500 employees.
3. Head of Sales Development, SDR or BDR Manager, VP Sales.
4. Companies that posted an SDR or BDR job based in DACH in the last 30 days.
Canvas: what usually goes wrong: new SDRs meet their first real objections on live calls. Proof: we helped
6 German B2B software companies. Desired outcome: new SDRs booking first meetings within 3 weeks.
Objection: the sales manager running every role-play. Lead magnet: a practice call where the new rep
pitches an AI playing one of the company's real buyers, built from their website.
````

## 3. Listen, then answer

Setup takes 1 to 3 minutes. If it says "Setup OK", you're done: listen to the talks, then answer the four questions and go to [BUILD.md](BUILD.md).
