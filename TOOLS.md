# Tools for each step

Today you run everything by hand in a chat. This page is for later: what to use when you want the same workflow to run every day.

**Start by hand.** Run one signal manually for a couple of weeks, about 20 companies a week. Automate it only once you know the signal gets replies.

## One tool per job

| Job | With <img src="logos/clay.png" width="20" height="20" alt=""> Clay | Without Clay |
|---|---|---|
| Find companies with a signal | <img src="logos/clay.png" width="20" height="20" alt=""> Clay company search: job posts, new hires, headcount growth, tech stack, funding | Your AI with web search; careers pages and job boards (<img src="logos/ashby.png" width="20" height="20" alt=""> Ashby, <img src="logos/greenhouse.png" width="20" height="20" alt=""> Greenhouse, <img src="logos/personio.png" width="20" height="20" alt=""> Personio, <img src="logos/linkedin.png" width="20" height="20" alt=""> LinkedIn Jobs, StepStone); <img src="logos/crunchbase.png" width="20" height="20" alt=""> Crunchbase or <img src="logos/dealroom.png" width="20" height="20" alt=""> Dealroom for funding; <img src="logos/builtwith.png" width="20" height="20" alt=""> BuiltWith or <img src="logos/wappalyzer.png" width="20" height="20" alt=""> Wappalyzer for tech stack |
| Verify the signal | A Custom data point (<img src="logos/clay.png" width="20" height="20" alt=""> Clay's research agent reads the source) | Your AI opens and reads the source page |
| Check fit | <img src="logos/clay.png" width="20" height="20" alt=""> Clay company data (size, industry, location), plus a Custom data point for anything else | <img src="logos/linkedin.png" width="20" height="20" alt=""> LinkedIn company page and website, read by your AI |
| Find the person | <img src="logos/clay.png" width="20" height="20" alt=""> Clay people search | <img src="logos/linkedin.png" width="20" height="20" alt=""> LinkedIn Sales Navigator, or LinkedIn search through your AI |
| Find the email | <img src="logos/clay.png" width="20" height="20" alt=""> Clay's email waterfall (it tries several providers in turn) | An email finder such as <img src="logos/prospeo.png" width="20" height="20" alt=""> Prospeo, <img src="logos/findymail.png" width="20" height="20" alt=""> Findymail, <img src="logos/hunter.png" width="20" height="20" alt=""> Hunter or <img src="logos/apollo.png" width="20" height="20" alt=""> Apollo |
| Write the message | Your AI in chat, or an AI column in a <img src="logos/clay.png" width="20" height="20" alt=""> Clay table | Your AI with [the signal-to-message prompt](copy/signal-to-message-prompt.md) |
| Approve before sending | A <img src="logos/slack.png" width="20" height="20" alt=""> Slack message with the signal, the link and the draft | Same |
| Send email | <img src="logos/instantly.png" width="20" height="20" alt=""> Instantly, <img src="logos/smartlead.png" width="20" height="20" alt=""> Smartlead or <img src="logos/lemlist.png" width="20" height="20" alt=""> lemlist | Same |
| Send on <img src="logos/linkedin.png" width="20" height="20" alt=""> LinkedIn | <img src="logos/heyreach.png" width="20" height="20" alt=""> HeyReach or <img src="logos/lemlist.png" width="20" height="20" alt=""> lemlist | Same |
| Track replies and deals | Your CRM: <img src="logos/hubspot.png" width="20" height="20" alt=""> HubSpot, <img src="logos/attio.png" width="20" height="20" alt=""> Attio, <img src="logos/pipedrive.png" width="20" height="20" alt=""> Pipedrive | Same |
| Run it on a schedule | <img src="logos/clay.png" width="20" height="20" alt=""> Clay scheduled sources and webhooks | <img src="logos/n8n.png" width="20" height="20" alt=""> n8n or <img src="logos/make.png" width="20" height="20" alt=""> Make, or a scheduled <img src="logos/claude.png" width="20" height="20" alt=""> Claude Code or <img src="logos/openai.png" width="20" height="20" alt=""> Codex agent |

## At scale, with Clay

```mermaid
flowchart LR
    A["Clay source<br/>runs daily<br/>(job posts or new hires)"] --> B["Clay table<br/>remove companies<br/>already contacted"]
    B --> C["Custom data point<br/>verifies the signal"]
    C -- no --> X[Dropped with reason]
    C -- yes --> D["Fit check<br/>size, industry,<br/>country"]
    D --> E["People search<br/>and email<br/>waterfall"]
    E --> F["AI column<br/>writes the<br/>first message"]
    F --> G["Slack<br/>human approves"]
    G --> H["Instantly or<br/>HeyReach"]
    H --> I["CRM"]
```

## At scale, without Clay

```mermaid
flowchart LR
    A["n8n or a scheduled<br/>agent runs daily"] --> B["Job board, funding<br/>or news source"]
    B --> C["Sheet or database<br/>remove companies<br/>already contacted"]
    C --> D["LLM with web search<br/>verifies the signal<br/>and checks fit"]
    D -- no --> X[Dropped with reason]
    D -- yes --> E["People and<br/>email finder"]
    E --> F["LLM writes the<br/>first message"]
    F --> G["Slack<br/>human approves"]
    G --> H["Instantly or<br/>HeyReach"]
    H --> I["CRM"]
```

## What changes at scale

- **Dedupe first.** Signals repeat: the same company posts the same job every month. Check against everyone you've already contacted before you spend anything on research.
- **Keep the evidence link with the row.** The person approving needs it, and so does whoever reads the reply.
- **Watch the drop rate.** If more than half the companies fail verification, fix the search, not the verification.
- **Rewrite nothing by hand at scale.** If you keep editing the same thing in the drafts, change the prompt.
