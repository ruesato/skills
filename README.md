# ruesato-plugins

A [Claude Code](https://code.claude.com) plugin marketplace.

This repository is an **index only** — it contains no plugin code. Each plugin
lives in its own repository and is referenced here by a pinned tag.

## Install

```
/plugin marketplace add https://github.com/ruesato/plugins.git
/plugin install lastcall@ruesato-plugins
```

Every repository here is public, so this needs no GitHub account, SSH key, or
`gh` login. Use the full `https://` URL rather than the `ruesato/plugins`
shorthand: GitHub `owner/repo` shorthand clones over SSH by default, which
fails for anyone without a key on their machine. (The alternative is to set
`CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1`, but that is a per-machine setting each
user would have to apply.)

## Plugins

| Plugin | Version | Source | What it does |
|---|---|---|---|
| `lastcall` | v0.1.2 | [ruesato/agent-skills-lastcall](https://github.com/ruesato/agent-skills-lastcall) | Close out an agentic work session: meters tokens, time, and cost from transcripts, summarizes what actually landed, and gates every durable action behind your approval. Ships `/lastcall` and `/tally`. |
| `floreo` | v1.2.1 | [ruesato/agent-skill-floreo](https://github.com/ruesato/agent-skill-floreo) | Turn agent-created content into beautiful, self-contained HTML documents optimized for human reading. Ships `/floreo`, `/floreo:draft`, `/floreo:setup`, and `/floreo:unsetup`. |

## Adding a plugin

1. Publish the plugin in its own repo with `.claude-plugin/plugin.json` at the root.
2. Tag a release (`v0.1.0`).
3. Add an entry to `.claude-plugin/marketplace.json` with a `url` source pinned
   to that tag — a full `https://` clone URL, not a `github`/`owner-repo` source.
   The `github` source type clones over SSH, so it locks out anyone without a
   key even when the repository is public.
4. Bump the entry's `version` on every release — clients do not see updates otherwise.
