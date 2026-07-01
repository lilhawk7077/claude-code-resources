---
title: "The 5-step Claude Code workflow I use every day"
date: 2026-07-01
author: Alex
tags: [claude-code, workflow, ai]
description: "How a single 5-step method collapsed my Claude Code context-switching overhead from 20 minutes per task to 30 seconds."
---

# The 5-step Claude Code workflow I use every day

After six months of daily Claude Code use, I've settled into a single workflow that handles 90% of what I do. It collapses to 5 steps. This post is what it is, why it works, and how Vexilo ties it all together.

## The 5 steps

```
Research → Plan → Test-first → Security → Commit
```

That's it. Five steps. Every task, every time.

## Step 1: Research

Before writing a line of code, know what exists.

**What I run:**
- `claude-code-guide` agent (when I'm new to a feature)
- `/help <command>` (when I know roughly what I want)
- Documentation lookup via `documentation-finder` skill

**Why this matters:** The cost of writing the wrong code is much higher than the cost of reading the right docs. 5 minutes of research saves an hour of refactoring.

## Step 2: Plan

Think through before building.

**What I run:**
- `/plan` (for non-trivial features)
- `plan-reviewer` agent (to catch gaps in my plan)
- `task-decomposer` skill (when the task is big)

**Why this matters:** Writing code without a plan is the #1 source of "I built the wrong thing" rework. 10 minutes of planning saves 2 hours of building the wrong thing.

## Step 3: Test-first

Write the failing test before the fix.

**What I run:**
- `tdd-guide` agent (Claude writes the test plan)
- `/tdd` slash command (Claude writes the failing test)
- `test-pattern-library` skill (for project-specific test conventions)

**Why this matters:** TDD forces me to specify the behavior before the implementation. The test becomes the spec.

## Step 4: Security

Before any commit, before any deploy.

**What I run:**
- `security-reviewer` agent (catches obvious issues)
- `/security-scan` slash command (catches subtle issues)
- `vulnerability-checker` skill (for new dependencies)

**Why this matters:** The cost of fixing a security issue in production is 100x the cost of catching it pre-commit. 90 seconds of security scanning has caught more bugs than any other step in my workflow.

## Step 5: Commit

Wrap it up cleanly.

**What I run:**
- `/quality-gate` slash command (lint, format, type-check)
- `/commit` slash command (conventional commit message)
- `commit-message-writer` skill (for non-trivial commits)

**Why this matters:** Conventional commits + auto-generated messages = readable git history forever.

## How long does this take?

- Step 1: 1-5 minutes
- Step 2: 5-15 minutes
- Step 3: 10-30 minutes (this is where the actual work happens)
- Step 4: 1-2 minutes
- Step 5: 30 seconds

Total: 20-50 minutes per task, including the actual coding. For simple bug fixes it's 5 minutes. For new features it's 1-2 hours.

## Why this works

Three reasons:

1. **Each step has a single purpose.** I'm not switching contexts. When I'm planning, I'm planning. When I'm testing, I'm testing.
2. **Each step has a tool.** I don't have to remember what to run — the workflow tells me.
3. **Each step has a feedback loop.** Tests fail before I commit. Security scans fail before I commit. Linters fail before I commit. I catch issues immediately.

## Where Vexilo comes in

The hard part of this workflow was always remembering *which* agent or *which* command to chain. Vexilo is the navigation layer over the whole ecosystem:

- The 5-step workflow is the homepage visualization
- Each scenario card (Fix a bug / Build feature / etc.) shows the full chain for common tasks
- ⌘K search means I never have to scroll
- "Teach Claude this handbook" primes the entire workflow into my Claude session

If you want to try this workflow:

1. Open https://vexilo.app/?lang=en
2. Pick the scenario card that matches your current task
3. Click "Teach Claude this handbook" and paste the primer into your next session
4. Claude now defaults to this workflow for the rest of the conversation

30 seconds of setup. Saves 20 minutes of context-switching per task.

## What's next for me

I'm refining the workflow. The next iteration adds:

- **Step 0: Reflect.** Before research, take 60 seconds to ask "do I actually need to do this?"
- **Step 6: Document.** After commit, write a 3-sentence summary in the PR description.

If you have steps you'd add, [open a discussion](https://github.com/lilhawk7077/claude-code-resources/discussions) and let's argue about it.