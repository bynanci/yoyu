# Cognitive Model

> Status: v0.1 pre-development hypothesis. This document translates cognitive and HCI concepts into product behavior. It does not claim clinical efficacy.

## Purpose

Yoyu should reduce the amount of life coordination a person must keep active in working memory while preserving autonomy and flexibility.

The product model is:

```text
Context
  ↓
What does the user need to understand now?
  ↓
External cognitive support
  ↓
One clear action / request / intentional non-action
  ↓
Visible, trustworthy feedback
```

## Primary cognitive problems to support

### 1. Prospective memory
Remembering to do something in the future creates ongoing mental load.

Product response:
- externalize important Anchors,
- show preparation before the Anchor when relevant,
- distinguish recorded reminders from guaranteed delivery,
- avoid requiring the user to continuously rehearse future intentions.

### 2. Working-memory load
Too many simultaneously visible details make coordination harder.

Product response:
- prioritize current context and next Anchor,
- collapse optional detail,
- make responsibility state visible,
- use Direction Mode when the user explicitly wants a reduced-information view.

### 3. Task initiation
Knowing a goal does not necessarily answer “what do I do now?”

Product response:
- represent Transitions explicitly,
- expose the smallest meaningful next action,
- separate “not now” from “unfinished failure.”

### 4. Context switching and transition cost
Moving between places, roles, plans, or activities can require additional cognitive effort.

Product response:
- model preparation, travel, waiting, handoff, recovery, and reorientation as Transitions,
- show what remains stable across a change,
- avoid abrupt hidden auto-rescheduling.

### 5. Uncertainty
Unknown information is different from a rejected proposal, missing data, or intentionally open choice.

Product response:
- preserve explicit uncertainty states,
- show what is known, what is unknown, and what needs confirmation,
- do not manufacture precise dates or confident reassurance.

### 6. Distributed cognition
Shared life coordination can be distributed across people, devices, notes, calendars, and routines.

Product response:
- make responsibility transfer explicit,
- separate personal memory support from shared agreement,
- treat wearables and calendars as optional external nodes, not the source of truth for all meaning.

## Interaction model

### Normal mode

The user can explore Life Blocks, upcoming Anchors, shared responsibilities, and longer horizons.

### Direction Mode

Direction Mode is intentionally invoked by the user. It should not diagnose or infer anxiety.

It answers:

```text
Where am I?
What matters next?
What can wait?
Who is already handling something?
What is the next useful action?
```

A valid answer may be:

> Nothing needs action right now. The next confirmed Anchor is later today.

The system should not fill free time just because it is visible.

## Recognition over recall

Important state should be recognizable without remembering past conversations or hidden workflow history.

Examples:

- “Waiting for Alex to accept” is better than a generic pending icon.
- “Last synced 18 min ago” is better than displaying stale shared state as current.
- “Not decided yet” is different from an empty field.

## Chunking

Information should be grouped around meaningful life units rather than arbitrary UI containers.

Preferred chunks:
- current Life Block,
- next Anchor,
- active Transition,
- responsibility group,
- unresolved decision.

Avoid card proliferation where every line becomes its own visual container.

## Choice architecture

When the user needs immediate direction, reduce simultaneous decisions.

Rules:
- one primary action per reduced state,
- secondary actions remain available but visually subordinate,
- no forced choice when “leave undecided” is valid,
- no default acceptance on behalf of another person.

## Temporal construal

Near-term information should be concrete; distant information should be more abstract and condition-based.

This produces semantic zoom:

```text
Today        → action / timing / transition
Week–Month   → rhythm / commitments
Quarter–Year → phase / experiment / condition
1–3 years    → path / dependency / decision window
3–10 years   → desired life shape / values / possibilities
```

A long-term direction may link to a current action, but the product must not imply that every present action must serve a ten-year goal.

## Agency and self-determination

The interface should preserve the user’s ability to:

- choose,
- decline,
- hide,
- postpone,
- remain undecided,
- ask for support,
- revoke sharing where technically possible.

Support should not become coercion.

## Collaboration model

For any shared item, users should be able to answer four separate questions:

1. Who owns the responsibility?
2. Who may support?
3. Who can see or edit it?
4. Whose consent is required for change?

These must not be collapsed into one generic “shared” status.

## Feedback model

A trustworthy feedback response includes:

- what happened,
- whether it is local or server-confirmed,
- what changed,
- what did not change,
- whether another person must confirm,
- whether the information may be stale.

## Cognitive anti-patterns

Avoid:

- showing the entire backlog during overload,
- too many simultaneous CTAs,
- ambiguous “done” states for shared work,
- auto-generated deadlines for distant goals,
- shame-based overdue language,
- hiding sync state,
- repeated reminders when ownership is unclear,
- inferring emotional state without explicit consent and valid evidence.

## Research questions

- Does Life Block match how users naturally group life situations?
- Does explicit Transition representation reduce “what do I do now?” uncertainty?
- Is Direction Mode more useful than a conventional agenda view during overload?
- Can shared responsibility reduce mental load without increasing caregiver burden?
- Which information is essential at each semantic zoom level?

## Validation principle

Every cognitive principle must map to:

```text
Evidence / hypothesis
→ UI behavior
→ measurable usability task
→ success and failure criteria
```

A cognitive theory alone is not evidence that Yoyu’s implementation works.
