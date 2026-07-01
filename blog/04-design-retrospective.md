---
title: "Building the visual Claude Code workflow map: a design retrospective"
date: 2026-07-01
author: Alex
tags: [claude-code, design, ui]
description: "How I designed the interactive 5-step workflow map at the top of vexilo.app — and what I'd change if I started over."
---

# Building the visual Claude Code workflow map: a design retrospective

The homepage of https://vexilo.app/?lang=en has, near the top, a clickable visualization of the 5-step Claude Code workflow. Each node (Research → Plan → Test-first → Security → Commit) is a button. Click it, and the page shows you which agents, commands, and skills pull weight at that step.

This post is about how I designed it, what worked, what didn't, and what I'd change.

## The problem

Before the visualization, Vexilo was just an alphabetical list. Users opened the page, saw 31 agents + 99 commands + 123 skills, and immediately bounced. Too much, no hierarchy, no entry point.

I needed a way to say: "here's the small set of things you should care about for the small set of tasks you do daily."

## What I tried first

**v0.1 — Tabbed table.** One tab per scenario (Fix bug, Build feature, etc.). Inside each tab, a table of relevant primitives. Worked OK but felt like a Wikipedia page. No visual identity.

**v0.2 — Card grid.** One card per scenario, with a brief description. Click a card, expand to see the chain. Better. But the user still had to know which scenario card matched their task. New users don't.

**v0.3 — Tag cloud.** Tags like `bug-fix`, `security`, `tdd`. Click a tag, filter the list. Failed — too abstract.

**v1.0 — The 5-step workflow map.** This is what's live now. Five nodes in a horizontal row, each connected to the next. Click a node, see the primitives.

## Why v1.0 worked

Three reasons:

**1. It's directional.** The arrow from Research → Plan → TDD → Security → Commit tells a story. New users can read the page top-to-bottom and learn the workflow by seeing it.

**2. It's interactive but not overwhelming.** Five nodes is few enough that the user can hold them in their head. They don't have to memorize a taxonomy.

**3. It maps to existing mental models.** "Research before planning" is something every engineer already believes. I'm not teaching a new workflow — I'm naming an existing one.

## What I'd change

If I started over:

**1. Make it collapsible.** Some users want to see the primitives immediately; others want to see the workflow first. Let them toggle.

**2. Add a "where am I?" indicator.** If the user has clicked into a scenario card, highlight which workflow step is active. Right now the connection between scenarios and workflow is implicit.

**3. Add a "you've done this 50 times" tracker.** Show users how often they've visited each node. (Privacy-respecting — localStorage only.) Power users want to know what they actually use.

**4. Make it printable.** A printable version of the workflow as a one-page PDF. Engineers love printable things.

## What I learned about the design process

Three things:

**1. The first design is rarely the right one.** I shipped three versions in six weeks. Each was better than the last. Don't fall in love with v1.

**2. Constraints help.** The 5-step workflow was a constraint I imposed on myself to avoid the "alphabetical list" trap. Without the constraint, I'd still be trying to make 250+ primitives browsable.

**3. Test with new users, not power users.** My initial feedback came from power users who already knew what they wanted. Their feedback made the design worse. New users forced me to simplify.

## What this means for your design

If you're building a navigation layer over a complex ecosystem (developer tools, design systems, content libraries), three patterns to steal:

1. **Directional workflow map.** Visualize the steps, not the inventory.
2. **Five or fewer nodes.** Anything more, users won't hold in their head.
3. **Click to expand.** Default to a high-level view, expand for detail.

The Vexilo homepage is the simplest possible version of these patterns. There's a much fancier version in the design files (eventually: collapsible + printable + tracker), but the simple version is what shipped.

## Try it

Open https://vexilo.app/?lang=en. The 5-step workflow is the second thing you see (after the hero).

If you're building a similar visualization, [open a discussion](https://github.com/lilhawk7077/claude-code-resources/discussions) — I'd love to see what you ship.