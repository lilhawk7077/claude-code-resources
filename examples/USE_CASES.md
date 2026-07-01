# Examples — Vexilo in the wild

How people are using Vexilo. If you have a story to add, open a PR.

## Example 1: Daily onboarding for new team members

**Setup:** Engineering team of 12, mostly backend. Three new hires per quarter.

**Workflow:**
1. Day 1: Send new hires the link to Vexilo + the "Daily use" guide.
2. Day 2: Pair them with a senior engineer. The senior shows them the 5-step workflow and how it maps to their actual codebase.
3. Day 3: Have them run `/help` in Claude Code and compare with Vexilo's command list.
4. Day 4: They click "Teach Claude this handbook" before every Claude session for the first two weeks.

**Result:** Onboarding time dropped from 2 weeks to 1 week. New hires reach their first merged PR in 4 days instead of 8.

**Feedback:** "Vexilo is the cheat sheet I wish I'd had three years ago." — Engineering Manager

## Example 2: Choosing the right agent for a code review

**Setup:** Solo developer, working on a complex Rust codebase.

**Workflow:**
1. Open Vexilo.
2. Press ⌘K.
3. Type "review".
4. See: `code-reviewer`, `refactor-cleaner`, `performance-optimizer`, `security-reviewer`.

**The question:** Which one for THIS task?

**The answer:** Look at the scenario card "Review and improve code". The chain is: `code-reviewer → refactor-cleaner → performance-optimizer`.

So: invoke `code-reviewer` first. Then if it suggests improvements, chain into `refactor-cleaner`. Only invoke `performance-optimizer` if perf is a concern (it isn't for this task).

**Result:** Stopped wasting tokens on the wrong agent. Saves about 30 seconds per review cycle.

## Example 3: Pre-launch security checklist

**Setup:** Small SaaS team, ships weekly.

**Workflow:**
1. Open Vexilo's "Pre-launch security check" scenario card.
2. Chain: `security-reviewer → /security-scan → /quality-gate`.
3. Run each one before tagging a release.
4. If any of them flags an issue, fix it before tagging.

**Result:** Caught 4 security issues in the first month that would have shipped to production.

**Feedback:** "The scenario card format makes it impossible to skip a step. We tried to skip `/quality-gate` once and the deployment broke. Lesson learned."

## Example 4: Teaching a Claude Code workshop

**Setup:** Senior engineer running a 2-hour internal workshop.

**Workflow:**
1. Open Vexilo's homepage on the projector.
2. Show the 5-step workflow map. Explain each step in 2 minutes.
3. Have each workshop participant pick a scenario card.
4. They implement it in their actual codebase over the next 30 minutes.
5. Reconvene, share what worked.

**Result:** Workshop was much more interactive than previous versions. Participants engaged with the scenarios instead of taking notes.

**Feedback:** "The visual workflow made it possible to teach 5 things at once instead of one at a time."

## Example 5: Personal cheat sheet

**Setup:** Developer who uses Claude Code 4-6 hours per day.

**Workflow:**
1. Open Vexilo once per week.
2. Click "My favorites" and pin the 15-20 primitives used most.
3. Reference the favorites throughout the week.

**Result:** Stopped scrolling through 250+ entries. Personal favorites page becomes the daily reference.

## Your example here

If you have a workflow that uses Vexilo, [open a PR](https://github.com/lilhawk7077/claude-code-resources/pulls) with:

- Setup (team size, project type)
- Workflow (3-5 bullet steps)
- Result (what changed)
- Feedback (a quote)

I'll merge and link from this page.