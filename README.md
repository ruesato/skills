# ruesato-plugins

A [Claude Code](https://code.claude.com) plugin marketplace.

This repository is an **index only** — it contains no plugin code. Each plugin
lives in its own repository and is referenced here by a pinned tag.

## Install

```
/plugin marketplace add ruesato/plugins
/plugin install lastcall@ruesato-plugins
```

## Plugins

| Plugin | Version | Source | What it does |
|---|---|---|---|
| `lastcall` | v0.1.1 | [ruesato/agent-skills-lastcall](https://github.com/ruesato/agent-skills-lastcall) | Close out an agentic work session: meters tokens, time, and cost from transcripts, summarizes what actually landed, and gates every durable action behind your approval. Ships `/lastcall` and `/tally`. |

## Adding a plugin

1. Publish the plugin in its own repo with `.claude-plugin/plugin.json` at the root.
2. Tag a release (`v0.1.0`).
3. Add an entry to `.claude-plugin/marketplace.json` with a `github` source pinned to that tag.
4. Bump the entry's `version` on every release — clients do not see updates otherwise.
