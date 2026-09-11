# Domain Model

> Status: v0.1. This model is intentionally explicit about uncertainty, responsibility, and consent. It will change after prototype testing.

## Design goals

The domain model must support:

- time horizons from today to 3–10 years,
- precise and imprecise time,
- physical and abstract context,
- flexible planning,
- explicit responsibility,
- shared-life collaboration,
- offline and stale-state representation,
- deterministic Direction Mode.

## Core entities

### LifeBlock

A meaningful region of life across time and context.

Suggested fields:

```text
LifeBlock
- id
- title
- direction
- temporalScope
- temporalPrecision
- placeContextId?
- lifeDomainId?
- circleId?
- visibility
- status
- version
- createdAt
- updatedAt
```

A LifeBlock does not require exact start/end timestamps.

### Anchor

A significant point, constraint, or commitment that should not be missed.

```text
Anchor
- id
- blockId
- kind
- title
- temporalScope
- temporalPrecision
- confirmationState
- source
- preparationLeadTime?
- version
```

Possible kinds:
- fixed commitment,
- preparation point,
- decision point,
- external dependency,
- review point.

### Transition

Represents movement between states, blocks, or contexts.

```text
Transition
- id
- fromBlockId?
- toBlockId?
- kind
- trigger
- estimatedDuration?
- requirements[]
- status
```

Examples:
- preparation,
- travel,
- waiting,
- handoff,
- recovery,
- review,
- migration between long-term phases.

### Responsibility

Represents ownership of work or coordination.

```text
Responsibility
- id
- subjectType
- subjectId
- ownerUserId?
- state
- version
```

Important: ownership is not visibility and not consent.

Suggested states:
- unassigned,
- assigned,
- completed,
- cancelled.

### Handoff

Explicit responsibility transfer workflow.

```text
Handoff
- id
- responsibilityId
- fromUserId?
- toUserId
- state
- proposedAt
- resolvedAt?
- expiresAt?
- baseVersion
```

Suggested states:
- proposed,
- accepted,
- declined,
- cancelled,
- expired.

A responsibility must not silently change ownership before the handoff is accepted and committed.

### Circle

A collaboration boundary for trusted people.

```text
Circle
- id
- name
- members[]
- policies
```

A Circle does not imply all content is shared.

### PlaceContext

Physical context when location matters.

Examples:
- home,
- office,
- in transit,
- destination,
- custom place.

Location access must remain optional unless a feature explicitly requires it.

### LifeDomain

Abstract context such as:
- home,
- work,
- relationship,
- travel,
- finance,
- health,
- family.

LifeDomain is not the same as PlaceContext.

## Time model

Time must support more than exact timestamps.

### TemporalScope

Possible forms:

```text
ExactInstant
ExactRange
DateOnly
DateRange
RelativeWindow
OpenEnded
Unknown
```

### TemporalPrecision

Examples:

```text
minute
hour
day
week
month
quarter
year
multi_year
unknown
```

The UI must not infer a more precise time than the stored precision.

## Visibility and consent

These concepts must remain separate.

### Visibility

Who may see an item?

Examples:
- private,
- selected members,
- circle.

### Edit permission

Who may modify an item?

### Consent requirement

Whose confirmation is required before a shared commitment or responsibility becomes effective?

A person being able to see an item does not imply they accepted responsibility for it.

## Free vs unassigned

This distinction is mandatory.

### Free
Nothing is required here. No owner is needed.

### Unassigned
Something is required, but nobody has accepted ownership yet.

The UI and rule engine must never treat these as equivalent.

## Confirmation state

For shared or external information, distinguish:

- draft,
- proposed,
- confirmed,
- rejected,
- stale,
- unknown.

## Versioning

Shared mutable entities should expose a version or ETag-like concurrency token.

Goals:
- prevent silent overwrite,
- detect stale change proposals,
- require re-preview when affected state has changed.

## Direction projection

Direction Mode should be a projection over domain data, not a separate source of truth.

Example projection:

```text
DirectionSnapshot
- currentBlock
- nextAnchor
- nextAction
- acceptedResponsibilities[]
- unresolvedItems[]
- evaluatedAt
- freshness
- reasonCodes[]
- snapshotVersion
- ruleVersion
```

## Invariants

1. `visibility != responsibility`
2. `seen != accepted`
3. `free != unassigned`
4. `unknown != confirmed absence`
5. `pending sync != server confirmed`
6. `proposal != commitment`
7. distant intent must not gain false timestamp precision
8. responsibility transfer requires explicit acceptance
9. private content must not become shared because it belongs to a shared Circle
10. Direction Mode is derived from source state and must remain explainable

## Open questions

- Should Anchors exist independently of Life Blocks?
- Can one responsibility span multiple Life Blocks?
- How should recurring rhythms be represented without rebuilding a calendar recurrence engine too early?
- How should external calendar events map to Anchors without becoming the primary information architecture?
- How should historical versions be retained for relationship-critical shared commitments?
