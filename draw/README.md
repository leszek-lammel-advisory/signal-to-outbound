# Draw your workflow

You built an outbound campaign in Claude or ChatGPT. This page turns it into a picture with your tools' logos, ready to download as a PNG.

## How to use it

1. Open the page: https://leszek-lammel-advisory.github.io/signal-to-outbound/draw/ (works once the repo is public with GitHub Pages on). Until then, download this repo and open `draw/index.html` in your browser. It needs no internet connection.
2. Copy the prompt below (the page has a Copy button) and paste it into the same chat where you built your campaign.
3. Paste the JSON your AI gives you into the box on the page. It draws as soon as you paste.
4. Click **Download PNG**.

## The prompt

```text
Describe the outbound workflow from this chat as a diagram, in JSON. Use exactly this format:

{"title": "Short name of the campaign",
 "stages": [
  {"name": "Find", "steps": [
    {"label": "Clay: companies with an open SDR job", "tools": ["clay"]},
    {"label": "Real, recent, in DACH?", "decision": true, "no": "Dropped, with a reason"}
  ]},
  {"name": "Write", "steps": [
    {"label": "AI writes the signal email", "tools": ["claude"]}
  ]}
 ]}

Rules:
- Describe the workflow we actually ran in this chat. If we only planned one, describe that.
- 2 to 4 stages in order, with short names such as Find, Check, Write, Send.
- At most 9 steps in total. Every label under 40 characters, plain words, no numbering.
- A yes/no check is a step with "decision": true. Its label is a short question, and "no" says what happens to the ones that fail (under 40 characters). The yes path is simply the next step.
- "tools" lists the tools a step really used, only from these ids: airtable, apollo, ashby, attio, builtwith, chatgpt, claude, clay, crunchbase, dealroom, findymail, google, greenhouse, heyreach, hubspot, hunter, instantly, lemlist, linkedin, make, n8n, notion, openai, personio, pipedrive, prospeo, rapidapi, sheets, slack, smartlead, wappalyzer. Use "google" for web search, "clay" for Claygent and Clay searches, and claude or chatgpt (whichever you are) for steps you did yourself, such as research, judging or writing. Leave "tools" out when none of the ids fits.
- Output only the JSON, in one code block, with nothing before or after it.
```

## The format

```json
{"title": "Companies hiring SDRs in DACH",
 "stages": [
  {"name": "Find", "steps": [
    {"label": "Clay: software firms with an SDR job", "tools": ["clay"]},
    {"label": "Real, recent, in DACH?", "decision": true, "no": "Dropped, with a reason"}
  ]},
  {"name": "Send", "steps": [
    {"label": "Email or LinkedIn", "tools": ["instantly", "linkedin"]}
  ]}
 ]}
```

- `title`: shown above the graph.
- `stages`: the columns, left to right. Each has a `name` and a list of `steps`.
- A step has a `label` and, optionally, `tools`: up to 3 logo ids from the list in the prompt.
- A decision is a step with `"decision": true`. It is drawn as a diamond. The arrow to the next step is the "yes" path, and `no` is the box below it.

The page forgives small mistakes: a code block around the JSON, text before it, trailing commas, curly quotes, tool names in capitals. A tool id it does not know simply shows no logo, and the page tells you which ones. More than 7 steps get scaled down to fit the width.

## What's in this folder

`index.html` is the whole tool in one file. The logos are embedded inside it, so it works from GitHub Pages, from a downloaded file, or offline. The same logos are in [../logos/](../logos/) as separate PNG files.
