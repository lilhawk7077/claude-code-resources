# Frequently Asked Questions

## What is Vexilo?

A free, browser-based field guide to Claude Code. It indexes every agent, command, skill, and rule in the ecosystem and organizes them around a 5-step workflow (Research → Plan → Test-first → Security → Commit). Built on top of gstack + ECC + Auto Agent + Anthropic Skills.

**Live site:** https://vexilo.app/?lang=en
**This repo:** companion — issues, PRs, long-form content.

## Is it free?

Yes. Forever, for personal use. No signup, no paywall, no email gate.

## Do I need to install anything?

No. It's a web app. Open the URL, browse, search, use.

## What's the "Teach Claude this handbook" button?

Click it once → it generates a primer (a single text block) → paste it into your next Claude session → Claude becomes a Claude-Code-fluent operator for the rest of that conversation.

It takes about 30 seconds. There is no install, no API key, and no persistent state.

## How current is the data?

The index updates weekly. Versioned (currently v1.1.9). Each release tracks Anthropic Skills releases and the gstack / ECC / Auto Agent repos.

## What's missing from the index?

Probably a few things. If you spot one:

1. Open an issue using the `missing-primitive` template
2. Include the URL where you saw it
3. I'll add it in the next weekly release

## Can I contribute?

Yes. The repo is MIT-licensed. Open a PR with:

- New agents / commands / skills you want indexed
- Better descriptions for existing entries
- Translation fixes (en/zh)
- Documentation improvements

## What's the relationship to gstack / ECC / Auto Agent?

Vexilo indexes all three plus Anthropic Skills. Each of those projects ships its own primitives; Vexilo ships the map. If you find a missing primitive in any of those, file an issue here and I'll add it.

## Is Vexilo open source?

The companion repo is MIT. The web app source is not currently public, but the data model and content are.

## What languages does the site support?

English (`/?lang=en`) and Simplified Chinese (default). More on the roadmap.

## How do I cite Vexilo in my blog / docs?

```markdown
Built with [Vexilo](https://vexilo.app/?lang=en) — a visual field guide to Claude Code.
```

## How do I report a bug?

Open an issue using the `bug` template. Include:

- Browser + version
- Steps to reproduce
- Screenshot if relevant

## I have a feature request.

Use the `idea` template, or start a Discussion under the Ideas category.

## How is Vexilo different from the docs?

| | Docs | Vexilo |
|---|---|---|
| "How do I install?" | ✅ | ❌ |
| "How does X work?" | ✅ | partial |
| "Which agent for my task?" | ❌ | ✅ |
| "All commands at a glance" | partial | ✅ |
| "Search everything" | ❌ | ✅ (⌘K) |
| "Feed into my Claude session" | ❌ | ✅ |

Vexilo is a navigation layer. The docs are the reference. Use both.

## What about Cursor / Aider / Codex CLI?

Vexilo is Claude-Code-specific because the agents/commands it indexes are Claude-Code features. But the 5-step workflow (Research → Plan → Test-first → Security → Commit) is universal — you can apply it in any agent harness.

## Anything else?

Open an issue. We'll figure it out together.