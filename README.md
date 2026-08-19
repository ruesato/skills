# ruesato-plugins

A [Claude Code](https://code.claude.com) plugin marketplace.

This repository is an **index only** — it contains no plugin code. Each plugin
lives in its own repository and is referenced here by a pinned tag.

## Install

```
/plugin marketplace add ruesato/plugins
/plugin install lastcall@ruesato-plugins
```

Every repository here is public, so no GitHub account, SSH key, or `gh` login
is needed.

### If adding the marketplace fails to authenticate

Some Claude Code versions clone `owner/repo` shorthand over SSH rather than
HTTPS, which fails on a machine with no GitHub SSH key. If the first command
reports an authentication error or `Permission denied (publickey)`, add the
marketplace by its full HTTPS URL instead:

```
/plugin marketplace add https://github.com/ruesato/plugins.git
```

Setting `CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1` fixes the shorthand the same way,
for every marketplace and plugin on that machine.

The `/plugin install` step is unaffected either way: every plugin listed here
is pinned to an explicit `https://` clone URL, so installs never fall back to
SSH.

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
