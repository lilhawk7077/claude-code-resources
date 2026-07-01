# Vexilo — Architecture

## High-level

```
┌─────────────────────────────────────────┐
│  Browser (Next.js + Vercel)             │
│  https://vexilo.app/?lang=en            │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│  Static JSON tree of indexed primitives │
│  - agents[]                             │
│  - commands[]                           │
│  - skills[]                             │
│  - rules[]                              │
│  - workflows[]                          │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│  Weekly update pipeline (manual)        │
│  - Pull from gstack / ECC / Auto Agent  │
│  - Pull from anthropics/skills          │
│  - Manual review + description edit     │
│  - Regenerate JSON tree                 │
│  - Deploy                               │
└─────────────────────────────────────────┘
```

## Data model

```typescript
type Primitive = {
  id: string;
  kind: 'agent' | 'command' | 'skill' | 'rule';
  name: string;
  one_liner: string;
  long_description?: string;
  source: 'claude-code' | 'gstack' | 'ecc' | 'auto-agent' | 'anthropic-skills';
  url?: string;
  scenario_tags: string[];   // e.g., ['bug-fix', 'security-review']
  workflow_step?: 'research' | 'plan' | 'tdd' | 'security' | 'commit';
  // ...
};

type Scenario = {
  id: string;
  title: string;
  description: string;
  chain: PrimitiveRef[];   // ordered list of primitives to chain
};

type Workflow = {
  id: 'main-5-step';
  steps: WorkflowStep[];
};
```

## Why static JSON?

- Fast (no DB query)
- Cacheable (CDN-friendly)
- Offline-friendly (after first load)
- Easy to diff / review in PRs
- Search via client-side index (FlexSearch or MiniSearch)

## "Teach Claude this handbook" — how it works

1. User clicks the button
2. The site generates a markdown primer that lists every indexed primitive, organized by scenario
3. User pastes the primer into their next Claude session as part of their first message
4. Claude reads the primer and uses it as context for the rest of the session

The primer is generated client-side from the same JSON tree. There is no API call, no server, no telemetry.

## Update pipeline (current)

Right now: manual. Each week I:

1. `git pull` gstack, ECC, Auto Agent, anthropics/skills
2. Diff the indexed files vs. my local snapshot
3. Update the JSON tree (add new entries, remove deleted, edit descriptions)
4. Generate the primer markdown
5. Re-deploy

Long-term: I'd love to automate (1)-(4) and have humans review the diff in PRs.

## Why Next.js?

- Fast initial render for the interactive workflow
- Easy i18n (en + zh)
- Vercel hosting is free for this traffic level
- Static export possible (no DB needed)

## Why not a CLI?

A CLI version is on the roadmap. The trick is making the index discoverable — most users start in the browser, not in their terminal. The browser-first approach also lets us show the visual workflow, which a CLI can't.