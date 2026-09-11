# API Contract

> Status: v0.1 contract draft. Endpoints are design candidates, not implemented services.

## Principles

1. Core navigation is deterministic and does not depend on an LLM.
2. Server-confirmed shared state is authoritative for shared commitments and handoffs.
3. Clients may cache readable snapshots, but offline state must be clearly labeled.
4. Shared mutations require explicit actor permission and optimistic concurrency checks.
5. Missing data must not be converted into confident conclusions.
6. Read endpoints must not silently change commitments.

## Common response metadata

Responses that affect user decisions should be able to include:

```json
{
  "evaluatedAt": "2026-09-11T14:00:00+08:00",
  "snapshotVersion": "...",
  "freshness": "fresh|stale|offline",
  "ruleVersion": "...",
  "reasonCodes": []
}
```

Exact schema remains to be defined in OpenAPI.

## Direction

### `GET /v1/me/direction`

Purpose: render Now / Direction Mode.

Query candidates:
- `asOf`
- `timezone`
- optional `circleId`

Response candidates:

```json
{
  "currentBlock": {},
  "nextAnchor": {},
  "nextAction": {},
  "acceptedResponsibilities": [],
  "unresolvedItems": [],
  "evaluatedAt": "...",
  "snapshotVersion": "...",
  "freshness": "fresh",
  "reasonCodes": [],
  "ruleVersion": "..."
}
```

Rules:
- no next Anchor means “no next recorded Anchor,” not “nothing exists,”
- stale shared data must remain visibly stale,
- Direction Mode must be derived from stored state plus deterministic rules.

## Landscape

### `GET /v1/circles/{circleId}/landscape`

Purpose: support semantic zoom across life horizons.

Query candidate:
- `horizon=today|week_month|quarter_year|one_three_years|three_ten_years`

The response should return meaning appropriate to the requested horizon, not simply the same records at a wider date range.

## Life Blocks

### `POST /v1/blocks`
Create a Life Block.

### `GET /v1/blocks/{blockId}`
Read a block and its relevant projections.

### `PATCH /v1/blocks/{blockId}`
Update mutable fields.

Requirements:
- actor permission checked server-side,
- support imprecise time,
- version returned on read,
- conditional mutation required for shared state.

## Anchors

Candidate endpoints:

```text
POST   /v1/blocks/{blockId}/anchors
PATCH  /v1/anchors/{anchorId}
DELETE /v1/anchors/{anchorId}
```

Exact deletion semantics should distinguish user deletion from historical removal/audit retention.

## Responsibilities

### `GET /v1/circles/{circleId}/responsibilities`
Read responsibility state relevant to the actor.

### `POST /v1/handoffs`
Propose a responsibility transfer.

### `POST /v1/handoffs/{handoffId}/accept`
Explicitly accept transfer.

### `POST /v1/handoffs/{handoffId}/decline`
Decline transfer.

### `POST /v1/handoffs/{handoffId}/cancel`
Cancel a still-valid proposal where permitted.

Invariant:
- acceptance must atomically validate authorization, handoff state, and responsibility version.

## Change proposals

### `POST /v1/change-proposals`
Create a proposed change and calculate affected state.

Expected response concepts:
- proposed changes,
- affected Anchors,
- affected responsibilities,
- external items not modified,
- required confirmations,
- base versions.

### `POST /v1/change-proposals/{proposalId}/confirm`
Commit a valid proposal after re-checking current versions.

### `POST /v1/change-proposals/{proposalId}/cancel`
Cancel the proposal.

If the affected scope changed after preview, the client must receive a conflict and request a fresh preview.

## Consent and visibility

Candidate endpoints:

```text
GET    /v1/me/consents
POST   /v1/me/consents
DELETE /v1/me/consents/{consentId}
```

Consent must not be inferred from Circle membership.

## Integrations

### `GET /v1/integrations/capabilities`
Return supported capabilities and current availability.

Potential dimensions:
- platform,
- permission state,
- freshness,
- read/write direction,
- background capability,
- degradation behavior.

Core Yoyu flows must remain usable when no integration is connected.

## Concurrency

Shared writes should use optimistic concurrency.

Candidate approach:
- entity version or ETag returned on reads,
- client sends `If-Match` or equivalent version,
- stale precondition returns HTTP 412,
- domain/business conflict uses HTTP 409 with a reason code.

Reference: RFC 9110 conditional requests.

## Idempotency

Mutation endpoints that may be retried by clients should support idempotency keys where duplicate side effects would be harmful.

Examples:
- handoff acceptance,
- change confirmation,
- external integration commands.

## Error shape

Draft pattern:

```json
{
  "error": {
    "code": "HANDOFF_ALREADY_RESOLVED",
    "message": "This handoff is no longer pending.",
    "recoverable": true,
    "details": {}
  }
}
```

UI copy should not rely exclusively on server prose; stable error codes should drive localized client messaging.

## Offline behavior

- Reads may use a local snapshot with visible `lastSyncedAt`.
- Local edits may remain drafts or pending operations.
- Shared acceptance is never displayed as server-confirmed until committed.
- Reconnect must reconcile by version rather than silently overwriting newer state.

## Security baseline

Every endpoint must define:

- authenticated actor,
- object-level authorization,
- visibility scope,
- consent requirement,
- mutation permission,
- audit-sensitive side effects.

Front-end visibility rules are not authorization.

## Contract-first deliverables

Before implementation:

- OpenAPI specification,
- JSON examples,
- error-code catalog,
- permission matrix,
- state-machine diagrams,
- mock fixtures,
- contract tests,
- deterministic Direction golden cases.
