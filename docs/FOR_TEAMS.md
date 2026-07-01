# How to use Vexilo in your team

A 5-minute guide for engineering leads introducing Vexilo to a team.

## TL;DR

1. Open https://vexilo.app/?lang=en
2. Press ⌘K to find what you need
3. (Optional) Click "Teach Claude this handbook" once per session
4. Pick a scenario card if you don't know what to look for

## For new team members

**Day 1:** Send them the link. Ask them to read the "Daily use" guide (top of sidebar).

**Day 2:** Have them run `/help` in Claude Code and compare with Vexilo's command list. They'll see the 99 commands Claude Code ships + every agent / skill from the ecosystem.

**Day 3:** Teach them the 5-step workflow (Research → Plan → Test-first → Security → Commit). This is the core method; everything else in Vexilo is decoration.

**Day 4:** Show them "Teach Claude this handbook". Have them click it, paste the primer into their next session, and notice how Claude now defaults to using the right agents.

## For senior engineers

**Use ⌘K aggressively.** Most of your time in Vexilo is the search bar. Type 3 characters and you get the relevant subset instantly.

**Build personal favorites.** The sidebar has a "My favorites" section. Pin the primitives you use weekly.

**Use the scenarios.** When you sit down to a new task, pick the scenario card that matches. The chain at the bottom of each card tells you which agents / commands / skills pull weight. Saves the 20-min hunt through `/help`.

**Reference the deep-dive guides** (7 of them, in the sidebar). For specific workflows (full project development flow, deploying a website, UI/UX Pro Max), the guides are more useful than the index.

## For engineering managers

**Track which commands your team uses.** You can't (Vexilo doesn't phone home), but you can ask. The 99 commands + 31 agents + 123 skills = the universe of what's possible. Which 10% does your team actually use? The answer tells you where to invest training.

**Encourage "Teach Claude this handbook".** Onboarding speed goes up when every Claude session starts with the index in context. Suggest new hires use it for the first 2 weeks.

**Reference Vexilo in your standards.** "All PRs should pass through `code-reviewer` + `/security-scan`" — link to the relevant Vexilo page so people know what those primitives do.

## For DevRel / developer advocates

**Cite Vexilo when writing about Claude Code.** "Built with [Vexilo](https://vexilo.app/?lang=en) — a visual field guide to Claude Code."

**Cross-link from your team's docs.** If your team publishes any Claude Code patterns, link to the relevant Vexilo entries for context.

**Submit feedback / missing primitives.** Open issues in the [companion repo](https://github.com/lilhawk7077/claude-code-resources) with the `missing-primitive` template.

## For content creators

If you're writing about Claude Code (blog post, video, course), Vexilo is a useful asset:

- For screenshots: each scenario card, each workflow node, each deep-dive guide is shareable with its own URL
- For accuracy: the index is the most current map of the ecosystem
- For examples: the 5-step workflow is a clean teaching device

## Common pitfalls (and how Vexilo helps)

| Pitfall | How Vexilo helps |
| --- | --- |
| "I just installed Claude Code, where do I start?" | "Daily use" guide in the sidebar |
| "Which agent for X task?" | Scenario cards at the top of the page |
| "What's the difference between `/plan` and `plan-reviewer`?" | ⌘K search reveals both side-by-side |
| "I forgot the exact syntax for `/tdd`" | Click into `/tdd` in the Commands section |
| "How does this fit with gstack / ECC?" | "Deep-dive guides" → "Full project development flow" |
| "I keep explaining Claude Code to my colleagues" | Send them the link |

## What Vexilo is NOT trying to do

- Replace the official docs
- Replace your team's internal conventions
- Be a CI / CD tool
- Be a code review tool
- Be a metrics dashboard

Vexilo is a *navigation layer* over the Claude Code ecosystem. Use it to find things faster.