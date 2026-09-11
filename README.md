# Yoyu / 有餘

**Life, with room to move.**

Yoyu is a calm life-navigation system built around **time, space, transitions, and shared responsibility**.

It helps people understand:

- where they are,
- what matters next,
- what can wait,
- and who is carrying what.

Yoyu is **not another calendar** and **not another task manager**. It starts from larger life blocks rather than dense event grids or productivity scores, and supports horizons ranging from today to years ahead.

## Product principles

- **Direction over density** — show what matters next without filling every gap.
- **Room over rigidity** — uncertainty, flexibility, rest, and undecided states are valid.
- **Shared responsibility over supervision** — collaboration should make ownership clear without turning a partner or family member into a project manager.
- **Semantic time scales** — today, this month, this year, and long-term horizons should change the meaning and level of detail, not merely zoom the same calendar grid.
- **Explicit transitions** — help users understand how to move from the current state to the next one.
- **Trustworthy state** — distinguish proposed, accepted, pending, stale, offline, and confirmed information.
- **Calm by design** — minimal hierarchy, low visual noise, accessible interaction, and no gamified pressure.
- **No LLM dependency** — core navigation should be deterministic, explainable, and usable without generative AI.

## Core domain model

```text
Life Block
  ├─ Time Range
  ├─ Spatial / Life Context
  ├─ Direction
  ├─ Anchors
  ├─ Transitions
  ├─ Flexibility
  └─ Responsibility
```

The model is still under research and may change before implementation.

## Early product surfaces

1. **Now / Direction Mode** — current block, next meaningful anchor, what can wait, and who is already responsible.
2. **Life Landscape** — semantic zoom across day, week/month, quarter/year, 1–3 years, and 3–10 years.
3. **Life Block** — direction, anchors, transitions, flexibility, and responsibility.
4. **Shared Responsibility** — propose, accept, decline, or hand off responsibility explicitly.
5. **Change Preview** — understand what changes, what stays, and who needs to confirm.
6. **Trust & Settings** — sharing, notifications, sync state, export, and future device integrations.

## Non-goals

- Diagnosing or treating ADHD, anxiety, or any medical condition.
- Treating MBTI or planning preference as a clinical category.
- Automatically inferring that a user is anxious from behavior or biometrics.
- Forcing every life goal into deadlines or tasks.
- Monitoring partners or household members.
- Requiring wearable devices or health-data access for core functionality.

## Future direction

Yoyu may later act as an intermediary between people, shared life plans, calendars, and wearable devices. Device integrations should remain optional, permissioned, and separable from the core experience.

## Status

**Pre-development research and product design.**

Current work focuses on UX research, cognitive models, naming, information architecture, UI behavior, domain modeling, API contracts, collaboration semantics, reliability, and wearable-integration boundaries before implementation begins.
