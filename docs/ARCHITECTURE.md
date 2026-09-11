# Architecture

> Status: v0.1 architecture direction. No production stack has been selected yet.

## Architectural goals

Yoyu should be:

- deterministic at its core,
- explainable,
- usable without LLMs,
- usable without wearables,
- resilient to temporary offline state,
- explicit about shared-state freshness,
- privacy-preserving by default,
- modular enough to add device integrations later.

## High-level model

```text
Client UI
  ├─ Local read model / cache
  ├─ Direction projection
  ├─ Draft edits / pending operations
  └─ Integration adapters
        ↓
Application API
  ├─ Identity & authorization
  ├─ Life Blocks / Anchors / Transitions
  ├─ Responsibilities / Handoffs
  ├─ Change proposals
  ├─ Consent / visibility
  └─ Sync / versioning
        ↓
Persistence
  ├─ source-of-truth domain state
  ├─ versions / audit-sensitive events
  └─ integration metadata
```

## Core separation

### 1. Domain core

Owns:
- Life Blocks,
- Anchors,
- Transitions,
- Responsibilities,
- Handoffs,
- consent and visibility semantics.

It should not know about a specific wearable vendor or LLM provider.

### 2. Direction projection

Transforms domain state into a small explainable read model.

Inputs:
- domain snapshot,
- evaluation time,
- timezone,
- user preferences,
- rule version.

Output:
- current block,
- next anchor,
- next action,
- accepted responsibilities,
- unresolved items,
- reason codes,
- freshness.

The same inputs should produce the same output.

### 3. Collaboration service

Owns shared-state mutations and explicit handoff semantics.

It must:
- verify actor permissions,
- validate current entity versions,
- enforce consent requirements,
- reject stale proposals,
- never infer acceptance from notification delivery or read state.

### 4. Sync layer

Coordinates local and server state.

Principles:
- local reads can continue when useful,
- shared writes may remain pending offline,
- pending state must be visible,
- reconnect reconciles by version,
- no silent last-write-wins for relationship-critical shared state.

### 5. Integration adapters

Future integrations should sit behind capabilities rather than leak vendor-specific assumptions into the domain model.

Examples:
- external calendars,
- Apple HealthKit,
- Android Health Connect,
- Garmin APIs,
- watch notifications or lightweight actions.

An adapter should expose:

```text
capability
permission state
availability
freshness
source provenance
read/write direction
degradation behavior
```

## Client architecture principles

The client should separate:

- domain entities,
- server/shared state,
- local drafts,
- presentation projections,
- integration state.

Avoid coupling the UI directly to backend response shapes if that would make semantic zoom or offline behavior difficult to evolve.

## Suggested client state layers

```text
Remote authoritative state
        ↓
Normalized domain cache
        ↓
Derived read models
        ↓
Screen state

Local drafts / pending ops ─────┘
```

## Offline strategy

Initial direction:

- cache last useful read models,
- store local drafts separately from confirmed state,
- mark `lastSyncedAt`,
- queue only operations that are safe to retry,
- require reconciliation for shared acceptance/conflict-sensitive actions.

Yoyu should not claim full offline collaboration unless that behavior is actually implemented and tested.

## Time handling

Requirements:
- store timezone explicitly where meaning depends on local time,
- preserve temporal precision,
- distinguish date-only from exact instant,
- avoid converting long-term goals into UTC timestamps without semantic justification,
- make evaluation time an explicit input to deterministic rules and tests.

## Security and privacy

Baseline:
- server-side object authorization,
- least-privilege sharing,
- purpose-specific consent,
- separation of health data from ordinary life-planning data,
- audit-sensitive history for responsibility/consent changes,
- data export and deletion design before lock-in grows.

## Wearables

Wearables are optional extensions, not required infrastructure.

Phase order:

1. phone core,
2. lightweight wearable output/actions,
3. only then evaluate health/activity inputs with explicit use cases.

No biometric value should automatically trigger a diagnosis, partner alert, or responsibility reassignment.

## Observability

Future implementation should be able to distinguish:

- API failure,
- stale cached state,
- rule evaluation failure,
- sync conflict,
- integration unavailability,
- permission denial,
- notification delivery uncertainty.

Do not collapse these into one generic “something went wrong.”

## Testing strategy

### Domain tests
State-machine and invariant tests.

### Direction golden tests
Fixed snapshot + fixed evaluation time + fixed rule version → expected projection.

### Contract tests
Client/API request and response compatibility.

### Concurrency tests
Stale handoff, double acceptance, revoked access, reconnect conflict.

### Accessibility tests
Focus, scaling, screen-reader labels, reduced motion, non-drag paths.

### End-to-end scenarios
At minimum:
- daily plan,
- medium-term phase,
- long-term direction,
- responsibility handoff,
- offline edit and reconnect,
- plan-change preview.

## Stack decision gate

Do not select framework/database/backend solely from habit.

Before stack selection, confirm:

- offline depth required for v1,
- mobile/web priority,
- native wearable requirements,
- real-time collaboration requirements,
- audit/history requirements,
- authentication and household membership model,
- deployment and operating-cost constraints.

The architecture should follow the validated product model, not define it prematurely.
