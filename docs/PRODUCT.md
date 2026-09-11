# Product Foundation

> Status: v0.1 pre-development. This document captures the current product direction and hypotheses; it is not evidence that the product already improves anxiety, ADHD symptoms, or long-term outcomes.

## Product thesis

Yoyu is a **calm life-navigation system** for people who benefit from clearer external structure without rigid planning.

It organizes life around **time, space, transitions, and shared responsibility**. The primary interaction unit is a large, understandable life block rather than a dense calendar event or task list.

The product should help a person answer:

1. Where am I now?
2. What matters next?
3. What can wait or remain undecided?
4. Who is responsible for what?
5. If something changes, what is affected and what remains safe to keep?

## Target users

Initial research focuses on:

- adults with ADHD or executive-function challenges,
- people who prefer flexible, low-constraint planning,
- people who become overloaded when too many tasks, dates, decisions, or responsibilities are visible at once,
- partners, family members, or housemates who coordinate everyday life together.

ADHD and personality/planning preferences are distinct. Yoyu must not medicalize flexible planning preferences or assume all people with ADHD have the same needs.

## Core value

Yoyu should make life feel **legible without making it rigid**.

The intended value is not “complete more tasks.” It is to make direction, ownership, transitions, uncertainty, and room to adjust easier to understand.

## Product pillars

### 1. Direction
Show the smallest amount of information required to know what matters next.

### 2. Room
Unscheduled time, rest, uncertainty, and “not decided yet” are valid states.

### 3. Shared responsibility
Responsibility must be visible and explicitly accepted without turning one person into the permanent planner.

### 4. Semantic time
Information changes meaning across horizons:

- Today: actions, anchors, transitions.
- Week–Month: rhythm, commitments, flexibility.
- Quarter–Year: experiments, phases, conditions.
- 1–3 Years: paths, dependencies, decision windows.
- 3–10 Years: desired life shape, values, possible directions.

### 5. Trustworthy state
The system distinguishes fact from proposal, accepted responsibility from pending handoff, fresh data from stale data, and recorded absence from missing information.

## Core product objects

- **Life Block** — a meaningful region of life across time and context.
- **Anchor** — a key point that should not be missed or requires preparation.
- **Transition** — how the user moves from one state/block to another.
- **Responsibility** — who currently owns or supports a responsibility.
- **Handoff** — an explicit proposal and acceptance flow for responsibility transfer.
- **Place Context** — physical context when location matters.
- **Life Domain** — an abstract context such as home, work, travel, health, relationship, or finance.
- **Circle** — a shared coordination boundary for trusted people.

These objects remain provisional until validated by research and prototype testing.

## Core surfaces

1. **Now / Direction Mode**
2. **Life Landscape**
3. **Life Block Detail**
4. **Together / Responsibility**
5. **Change Preview**
6. **Trust & Settings**

## Product constraints

- Core functionality must work without an LLM.
- Core functionality must work without wearable devices.
- Core functionality must work without health-data permission.
- No automatic diagnosis of anxiety, ADHD state, or emotional state.
- No requirement that all life blocks have exact dates.
- No requirement that every activity map to a long-term goal.
- No silent assignment or transfer of another person’s responsibility.
- No surveillance-first collaboration model.

## Success criteria for early validation

Before implementation is considered validated, users should be able to:

- identify the current block and next anchor without explanation,
- distinguish confirmed, proposed, undecided, and stale states,
- understand who is responsible without opening a task-management view,
- change plans without losing track of what remains valid,
- navigate at least three time scales without interpreting the product as a calendar grid,
- retain autonomy to hide, decline, postpone, or leave something undecided.

## Non-goals

Yoyu is not:

- a clinical treatment,
- a productivity score,
- an automatic life planner,
- an attendance tracker for relationships,
- a partner-monitoring tool,
- a replacement for emergency services, medical care, or human support.

## Open questions

- Is `Life Block` cognitively natural enough for users, or does the concept require different language?
- How much structure is useful before it feels controlling?
- What should remain visible in Direction Mode under overload?
- Which responsibilities should be shareable, private, or jointly confirmed?
- How should long-term uncertainty be represented without creating false precision?
