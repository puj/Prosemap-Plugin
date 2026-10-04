# ProseMap for Claude

Find the weak sentences in a draft and why they are weak. You stay the writer; AI helps fix them.

This plugin connects Claude to [ProseMap](https://www.prosemap.io), a hosted service. It adds one
remote connector and nothing else. No code runs on your machine.

## Install

In Claude Code:

```
/plugin marketplace add puj/Prosemap-Plugin
/plugin install prosemap@prosemap
```

Or add the connector by itself, without the plugin:

```
claude mcp add --transport http prosemap https://www.prosemap.io/api/mcp
```

## What you can ask

- "Analyse this draft with ProseMap and tell me the three weakest passages and why. Do not rewrite anything."
- "How much would it cost to analyse this essay with ProseMap?"
- "Propose fixes for the weakest passages, change only the ones I approve, then analyse again and show me what moved."

## Tools

| Tool | What it does | Costs credit |
|---|---|---|
| `estimate_analysis` | Says what an analysis would cost | No |
| `submit_analysis` | Starts an analysis | Yes |
| `get_analysis` | Progress or results for an analysis | No |
| `get_sentences` | Sentence-level detail | No |
| `get_guidance` | The draft with comments on what to change | No |
| `explain_sentence` | A plain explanation of one sentence's score | Yes |
| `compare_versions` | What changed between two analyses | No |
| `list_analyses` | Your saved analyses | No |
| `get_balance` | Your credit and limits | No |

No tool deletes anything, and none reaches outside ProseMap.

## Signing in and cost

The first time a ProseMap tool is used, Claude opens ProseMap in your browser. Sign in, set a
monthly spending limit for the connection, and press Allow. You can remove the connection at any
time in ProseMap under Account.

Connecting is free. Analyses use prepaid credit: about $0.59 for a 1,000-word draft, shown before
anything runs. A failed analysis costs nothing. ProseMap enforces the spending limit; an assistant
cannot raise it.

## What is sent

The text you ask Claude to analyse is sent to ProseMap, analysed, and saved to your ProseMap
account so you can reopen it. It is not used to train models.
[Privacy policy](https://www.prosemap.io/privacy) · [Terms](https://www.prosemap.io/terms)

## Links

- Documentation: https://www.prosemap.io/connect
- Pricing: https://www.prosemap.io/pricing
- Support: support@prosemap.io

## About this repository

It holds only the plugin's configuration: `.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`
and `.mcp.json`. The ProseMap service itself is not open source.

Pushing a tag such as `v1.1.1` builds `prosemap-claude-plugin-1.1.1.zip` and attaches it to a release.
The tag must match the `version` in `.claude-plugin/plugin.json`.
