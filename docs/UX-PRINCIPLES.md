# UX Principles

> Status: v0.1. These principles are design hypotheses grounded in current product intent and will be revised after UX research and usability testing.

## 1. Direction over density

When a user is overloaded, the interface should reduce choices rather than expose every available task.

**Prefer**
- current context,
- next meaningful anchor,
- what can wait,
- who already owns what,
- one primary action.

**Avoid**
- dense dashboards,
- completion percentages,
- visible backlogs by default,
- multiple competing CTAs.

## 2. Recognition over recall

Users should not have to remember hidden plans, responsibilities, or prior agreements.

The interface should make important state externally visible:

- proposed,
- accepted,
- declined,
- undecided,
- stale,
- offline,
- pending sync,
- confirmed.

## 3. Progressive disclosure

Show the minimum information needed for the current decision. Details remain available without becoming the default view.

Examples:
- a Life Block shows its direction first,
- Anchors are visible before optional tasks,
- responsibility state is visible before handoff history,
- long-term horizons show paths and conditions before detailed actions.

## 4. Semantic zoom, not calendar zoom

Changing time scale changes the meaning of information.

| Scale | Primary representation |
| --- | --- |
| Today | next actions, anchors, transition timing |
| Week–Month | rhythm, commitments, flexible regions |
| Quarter–Year | phases, experiments, conditions |
| 1–3 Years | paths, dependencies, decision windows |
| 3–10 Years | life shape, values, possible directions |

The UI must not automatically convert distant intentions into precise dates.

## 5. Room is a first-class state

Empty time is not missing data.

The product must represent:

- free time,
- rest,
- undecided time,
- optional activity,
- postponed decisions,
- intentionally private space.

A free region must not automatically become available capacity for optimization.

## 6. Collaboration without supervision

Shared life does not imply shared visibility of everything.

The product should distinguish:

- who owns responsibility,
- who may support,
- who can see information,
- who can edit,
- who must consent.

A notification, read receipt, or “seen” state never equals acceptance of responsibility.

## 7. Explainable change

When plans change, the user should be able to understand:

1. what changed,
2. what remains valid,
3. what becomes risky or stale,
4. who needs to confirm,
5. what the next safe action is.

External reservations or third-party systems must never be presented as updated unless an integration has actually confirmed the change.

## 8. Calm does not mean vague

Minimalism must not remove necessary state.

Avoid:
- low-contrast critical information,
- hidden errors,
- gesture-only controls,
- ambiguous icons,
- animations that delay action,
- reassuring language that contradicts actual risk.

## Accessibility baseline

The product should target WCAG 2.2 AA where applicable.

Minimum expectations:

- sufficient text and UI contrast,
- readable type at system text scaling,
- visible keyboard/focus state,
- state not conveyed by color alone,
- reduced-motion support,
- non-drag alternatives for reordering or movement,
- explicit labels for screen readers,
- recovery paths for destructive actions.

Reference: https://www.w3.org/TR/WCAG22/

## Direction Mode

Direction Mode is a user-invoked reduced-information state. It must not claim to detect anxiety.

It should answer only:

1. Where am I now?
2. What is the next meaningful anchor?
3. What do I not need to handle right now?
4. Who is already carrying something for me/us?
5. What is the single most useful next action?

## Visual system direction

- Typography is the primary hierarchy.
- Spacing and hairline dividers are preferred over card-heavy layouts.
- Large blocks should feel spatial, not tabular.
- Critical anchors use stronger contrast and weight.
- Secondary context uses lower emphasis but remains readable.
- Status should remain understandable without decorative color.
- Motion should clarify transition, not provide spectacle.

## UX anti-patterns

Do not introduce:

- streaks,
- life scores,
- shame-based overdue states,
- forced daily check-ins,
- continuous partner monitoring,
- “AI knows what you need” copy,
- invisible auto-rescheduling,
- automatic responsibility reassignment,
- notification volume as a substitute for clarity.

## Validation questions

For each important screen, test:

- Can the user identify the next relevant thing within seconds?
- Can the user tell what is confirmed versus proposed?
- Can the user tell what they do not need to act on?
- Can the user understand who owns responsibility?
- Can the user recover from a change or sync failure?
- Does the minimal UI hide anything needed for a safe decision?
