# Yoyu Design

> Status: v0.1 design workspace guide.

This directory is the entry point for product design artifacts. Visual design should follow the product and cognitive model, not invent a separate interaction language.

## Design intent

Yoyu should feel:

- calm,
- spacious,
- legible,
- trustworthy,
- non-judgmental,
- collaborative without feeling monitored.

Minimalism is a means to reduce cognitive noise, not an excuse to hide important state.

## Core surfaces

### S01 — Now / Direction Mode
Show:
- current Life Block,
- next meaningful Anchor,
- what can wait,
- accepted responsibilities,
- one primary action.

### S02 — Life Landscape
Show:
- large life regions,
- semantic time scale,
- transitions between regions,
- uncertainty without fake precision.

### S03 — Life Block Detail
Show:
- direction,
- anchors,
- transition information,
- flexible/undecided space,
- responsibility.

### S04 — Together / Responsibility
Show:
- owner,
- supporter,
- pending handoff,
- acceptance/decline,
- visibility and consent separately.

### S05 — Change Preview
Show:
- before/after,
- what changes,
- what remains,
- external items not updated,
- who must confirm.

### S06 — Trust & Settings
Show:
- sharing scope,
- notification preferences,
- last sync/freshness,
- export/delete controls,
- optional integration capabilities.

## Visual hierarchy

Preferred order:

```text
Conclusion / direction
↓
Key state or Anchor
↓
Context
↓
Secondary details
↓
Metadata / source / freshness
```

Typography should carry most of the hierarchy.

## Layout principles

- Use whitespace before containers.
- Use hairline dividers before adding cards.
- Keep one clear dominant region per screen.
- Avoid dense grids that resemble a calendar by default.
- Allow large blank regions to remain meaningful.
- Use cards only when grouping or interaction boundaries genuinely need them.

## Status design

Do not rely on color alone.

Every critical state should have readable language, for example:

- Confirmed
- Waiting for acceptance
- Draft
- Not decided yet
- Last synced 18 min ago
- Offline — changes not yet shared

## Motion

Motion should explain:
- entering/exiting a Life Block,
- changing semantic time scale,
- expanding detail,
- confirming a transition.

Avoid motion that:
- creates urgency,
- loops continuously,
- obscures final state,
- conflicts with reduced-motion preferences.

## Accessibility

Target WCAG 2.2 AA where applicable.

Design reviews should check:
- text contrast,
- large text/system scaling,
- visible focus,
- non-color state cues,
- screen-reader labeling,
- reduced-motion behavior,
- non-drag alternatives,
- target size and spacing,
- recoverability after destructive actions.

Reference: https://www.w3.org/TR/WCAG22/

## Prototype order

1. Direction Mode
2. Life Block Detail
3. Together / Responsibility
4. Change Preview
5. Life Landscape across at least three scales
6. Trust & Settings

## Prototype scenarios

Prototype at minimum:

### Daily
A user is at home and needs to leave later. Some logistics are already handled by another person.

### Medium-term
A user is in a several-month phase with flexible experiments and one review point.

### Long-term
A user explores a 3–10 year direction with multiple possible paths and no exact deadline.

### Collaboration
A responsibility is proposed, accepted, later changed, and then viewed offline.

## Design review questions

- Is the next direction understandable in seconds?
- Is free/undecided space visibly valid?
- Can the user tell confirmation from proposal?
- Can the user tell responsibility from visibility?
- Does long-term content avoid false precision?
- Does the interface remain understandable when data is stale or offline?
- Does the design reduce noise without hiding risk?

## Future artifacts

This directory may later contain:

```text
design/
├─ README.md
├─ flows/
├─ wireframes/
├─ prototypes/
├─ tokens/
└─ accessibility/
```

Do not treat the future directory list as already implemented.
