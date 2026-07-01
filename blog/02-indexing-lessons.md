---
title: "I indexed every Claude Code agent, command, and skill — here's what I learned"
date: 2026-07-01
author: Alex
tags: [claude-code, indexing, ai-coding]
description: "Six weeks cataloging 31 agents, 99 commands, 123 skills, and 13 rules. Five patterns I didn't expect."
---

# I indexed every Claude Code agent, command, and skill — here's what I learned

After six weeks of cataloging the Claude Code ecosystem — 31 agents, 99 commands, 123 skills, 13 rules — here are the five patterns I didn't expect to find.

## 1. The naming tells you the philosophy

Claude Code has two naming conventions, and they reveal two different philosophies:

- **Slash commands** start with `/` and are imperative (`/plan`, `/tdd`, `/security-scan`). They're meant to be used directly.
- **Agents** are nouns (`tdd-guide`, `code-reviewer`, `security-reviewer`). They're meant to be invoked and reasoned about.

The commands are for *what you want done*. The agents are for *who you want to think about it*.

This split tells me that the Claude Code team designed for two workflows: do-it-myself (commands) and think-with-me (agents). Most users default to commands; power users mix both.

## 2. There's a hidden 4th category

Officially there are agents, commands, skills, and rules. But there's an informal 4th category: **hooks**. Hooks run shell commands at lifecycle events (PreToolUse, PostToolUse, etc.). They're not advertised in the docs but they're how power users automate.

I haven't indexed hooks yet because they require shell-level understanding of each project. It's on the roadmap. (See https://github.com/lilhawk7077/claude-code-resources/issues for tracking.)

## 3. The duplication is intentional

Some of the indexed commands look like duplicates of each other:

- `/plan` and `plan-reviewer`
- `/tdd` and `tdd-guide`
- `/security-scan` and `security-reviewer`

But they're not duplicates — they're different access patterns to the same underlying capability:

- `/plan` is for *you* to invoke when *you* want to plan
- `plan-reviewer` is for *Claude* to invoke when *Claude* decides planning is needed

Same capability, different trigger. Once I saw this pattern, the indexing became much easier.

## 4. The skill ecosystem is exploding

When I started indexing in May 2026, there were about 30 third-party skills. Now there are 123. The growth rate is roughly 10-15 new skills per week.

This is unsustainable for a manual index. I'm going to need community contributions or an automated pipeline. If you maintain a skill collection, [open a PR](https://github.com/lilhawk7077/claude-code-resources/pulls) with the additions.

## 5. Most users only use 10% of what's available

I asked my network (50 Claude Code users, ranging from beginners to daily users):

- Average number of slash commands used: 8-12 out of 99
- Average number of agents invoked: 2-4 out of 31
- Most-requested agent: `code-reviewer`
- Most-requested command: `/help`

The 80/20 rule applies ruthlessly: most users only use a small fraction of the ecosystem. The value of Vexilo is in showing people the *other* 90%.

## What this means for you

If you're a new Claude Code user, the most useful thing I can tell you is: **you don't need to learn everything**. Learn the 8-12 commands and 2-4 agents that match your daily workflow. The rest is decoration until your needs change.

If you're a power user, the most useful thing is: **audit your usage**. Run `/cost` and see what you're actually spending tokens on. You might be using expensive agents when cheaper commands would work.

If you're building tooling around Claude Code, the most useful thing is: **don't add more primitives**. The ecosystem is already overwhelming. Add a *navigation layer* instead.

## Want to see the index?

Everything I described is at https://vexilo.app/?lang=en. Free, no signup.

The companion repo (https://github.com/lilhawk7077/claude-code-resources) has the data model, the discussion threads, and the issue tracker.

If you spot a missing primitive or want to improve a description, open a PR. If you want to argue about workflow design, start a discussion. If you want to build a competitor, please do — the ecosystem needs more navigation layers, not fewer.

---

**Next post:** "Three months of using my own cheat sheet — what actually changed" (coming in two weeks). Subscribe via the discussion thread if you want notifications.