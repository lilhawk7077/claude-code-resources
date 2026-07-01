---
title: "Why the 'Teach Claude this handbook' button is my favorite UX pattern of 2026"
date: 2026-07-01
author: Alex
tags: [claude-code, ux, ai]
description: "One button. 30 seconds. Zero install. The shortest path between 'I just installed Claude Code' and 'Claude knows Claude Code.'"
---

# Why the "Teach Claude this handbook" button is my favorite UX pattern of 2026

The button on the top-right of https://vexilo.app/?lang=en does one thing: click it, and the site generates a primer (a single text block) that you paste into your next Claude session. From that moment, Claude knows which agents exist, which commands chain together, and which skills to invoke for which tasks.

30 seconds of setup. Zero install. No API key.

This post is about why I think this is a powerful UX pattern and where else it could be applied.

## The pattern in 5 sentences

1. The user has a context their AI doesn't know about.
2. There exists a structured representation of that context (the index).
3. The user can convert that structured representation into a single text blob in one click.
4. They paste the blob into the AI's input.
5. The AI now has the context for the rest of the session.

The trick is that step 3 happens client-side, with no API call. The conversion is a string concatenation, not an LLM inference.

## Why this works

Three reasons.

**1. Latency is zero.** No "loading…" state. No "thinking…". Click, paste, done.

**2. Cost is zero.** No tokens burned. No API quota. The primer is just text.

**3. Trust is high.** The user sees exactly what's being pasted. No hidden prompt injection. No opacity.

Compare this to "fine-tune the model on your data" or "use the API with a custom system prompt." Both are higher-friction, higher-cost, and lower-trust.

## Where else this pattern applies

I've been collecting examples:

- **Documentation sites.** A "feed this doc to your AI" button that generates a markdown primer.
- **Open-source repos.** A "feed this README to your AI" button that pulls all the docs into one blob.
- **API references.** A "feed this API to your AI" button that generates a primer from the OpenAPI spec.
- **Legal / compliance docs.** A "feed this policy to your AI" button for company policies.

In every case, the pattern is the same:

1. You have structured context.
2. You convert it to a single text blob.
3. The user pastes it into their AI.

## What I got wrong the first time

The first version of the button generated a 2000-word primer that covered every primitive in the index. That was too much — Claude's context window is finite, and a 2000-word primer eats into the budget for actual work.

The current version is around 600 words. It lists every primitive by name with a 5-10 word description, organized by scenario. That's the right balance: enough to give Claude situational awareness, not so much that it crowds out the user's actual prompt.

## How to build this for your own project

If you have a structured representation of context (docs, index, schema, policy), here's the 100-line implementation:

```typescript
function generatePrimer(index: Index): string {
  const sections: string[] = [];

  sections.push(`# ${index.title}\n`);
  sections.push(`A primer on ${index.title} for AI assistants. Read this once, then proceed.\n`);

  for (const scenario of index.scenarios) {
    sections.push(`## ${scenario.title}\n`);
    sections.push(scenario.description + '\n');
    sections.push(`Use these primitives in order: ${scenario.chain.map(p => p.name).join(' → ')}\n`);
  }

  for (const collection of [index.agents, index.commands, index.skills]) {
    sections.push(`## ${collection.label}\n`);
    for (const item of collection.items) {
      sections.push(`- \`${item.name}\` — ${item.one_liner}`);
    }
  }

  return sections.join('\n');
}
```

That's it. Render the result in a `<textarea>` with a "copy to clipboard" button.

## What I'd add next

The pattern has limits. The primer is static text — it doesn't reflect the current state of the user's project (open files, recent edits, etc.). To go further, you'd need to inject dynamic context (e.g., the user's current branch, their last 5 commits) into the primer.

This is where MCP servers start to look interesting. A "Teach Claude" button that:
1. Reads the user's project state via MCP
2. Generates a context primer that includes both the static index AND the dynamic project state
3. Pastes it into Claude

That's the natural next step. Watch this space.

## Try it

The button is at the top of https://vexilo.app/?lang=en. Click it, paste the result, and notice what happens.

If you're building a similar pattern, I'd love to see it. Open a discussion in https://github.com/lilhawk7077/claude-code-resources/discussions and link to your work.