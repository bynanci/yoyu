# Yoyu Roadmap

> Status: v0.1 pre-development roadmap. Dates are intentionally omitted until scope and research readiness are validated.

## Phase 0 — Product framing

Goal: make sure Yoyu solves the right problem before implementation.

- [x] Select working product name: Yoyu / 有餘.
- [x] Define core positioning: time × space × transitions × shared responsibility.
- [x] Define non-goals: not another calendar, not another task manager, no LLM dependency, no clinical claims.
- [x] Create initial documentation structure.
- [ ] Complete naming / brand validation and conflict checks.
- [ ] Finalize product promise and short positioning statement.

Exit criteria:
- product purpose and non-goals can be explained consistently,
- no critical terminology conflicts remain unresolved.

## Phase 1 — UX and cognitive research

Goal: validate the behavioral model before visual polish or engineering commitment.

- [ ] Complete deep UX research evidence map.
- [ ] Separate strong evidence, limited evidence, design inference, and open hypothesis.
- [ ] Interview target users across daily, medium-term, and long-term scenarios.
- [ ] Interview shared-life collaborators separately to understand mental load and control concerns.
- [ ] Validate whether Life Block / Anchor / Transition / Responsibility match user mental models.
- [ ] Identify anti-patterns that increase overload, shame, surveillance, or caregiver burden.

Exit criteria:
- clear evidence-to-design mapping,
- revised cognitive model,
- prioritized UX hypotheses.

## Phase 2 — Information architecture and low-fidelity UX

Goal: prove that the product is understandable without falling back to a calendar grid.

- [ ] Prototype S01 Now / Direction Mode.
- [ ] Prototype S02 Life Landscape.
- [ ] Prototype S03 Life Block Detail.
- [ ] Prototype S04 Together / Responsibility.
- [ ] Prototype S05 Change Preview.
- [ ] Prototype S06 Trust & Settings.
- [ ] Test semantic zoom for Today, Week–Month, Quarter–Year, 1–3 Years, and 3–10 Years.
- [ ] Add empty, unknown, stale, offline, conflict, and permission-denied states.

Exit criteria:
- users understand current direction within seconds,
- users distinguish proposed vs confirmed state,
- long-term views do not create false precision,
- free space remains visibly valid.

## Phase 3 — Domain model and contract design

Goal: make UI semantics implementable and testable.

- [ ] Finalize domain glossary.
- [ ] Validate LifeBlock, Anchor, Transition, Responsibility, Handoff, Circle, PlaceContext, and LifeDomain.
- [ ] Finalize temporal scope and temporal precision model.
- [ ] Finalize visibility, edit permission, and consent separation.
- [ ] Define state machines and invariants.
- [ ] Produce OpenAPI draft.
- [ ] Create JSON fixtures and deterministic Direction Mode golden cases.
- [ ] Define stable error codes and conflict handling.

Exit criteria:
- every core screen maps to explicit domain state and API behavior,
- no UI state depends on hidden or ambiguous backend assumptions.

## Phase 4 — Reliability, privacy, and collaboration review

Goal: make shared-life coordination trustworthy before shipping code.

- [ ] Define handoff acceptance and decline flows.
- [ ] Define offline / reconnect behavior.
- [ ] Define stale-data and last-sync behavior.
- [ ] Define notification deduplication, quiet hours, and expiry.
- [ ] Define data export, delete, and revoke-sharing behavior.
- [ ] Create misuse / surveillance threat model.
- [ ] Validate that one collaborator does not become the permanent planner by default.

Exit criteria:
- no false “accepted” or “handled” states,
- clear recovery from conflict and offline submission,
- minimum necessary sharing is enforced by design.

## Phase 5 — Architecture and stack decision

Goal: select implementation technology based on validated requirements.

Decision inputs:
- mobile vs web priority,
- required offline depth,
- real-time collaboration needs,
- audit/history requirements,
- authentication model,
- wearable/native integration requirements,
- hosting and operating-cost constraints.

- [ ] Decide application platforms for v1.
- [ ] Decide client architecture.
- [ ] Decide backend/runtime and persistence model.
- [ ] Decide authentication and Circle membership model.
- [ ] Decide sync and concurrency strategy.
- [ ] Define test pyramid and CI baseline.

Exit criteria:
- architecture decisions are traceable to validated product requirements,
- no technology is selected solely because it is familiar.

## Phase 6 — MVP implementation

Goal: build the smallest credible Yoyu loop.

Initial candidate loop:

```text
Create / view Life Block
→ see current direction
→ see next Anchor / Transition
→ assign or hand off responsibility
→ preview a change
→ confirm shared state
```

Core MVP must work:
- without LLM,
- without wearables,
- without health-data permission.

Implementation scope is not authorized until previous phase exit criteria are reviewed.

## Phase 7 — Wearable extension

Goal: extend Yoyu without making devices mandatory.

### First evaluate
- next Anchor glance,
- lightweight haptic reminder,
- “received,”
- “remind me later,”
- “request support.”

### Only later evaluate health/activity input
- permission model,
- source provenance,
- freshness,
- provider differences,
- explicit user value.

Do not:
- diagnose anxiety from biometrics,
- auto-alert partners based on biometrics,
- auto-reassign responsibilities from health signals.

## Validation gates

Before moving into full implementation, verify:

- [ ] product name / brand direction is acceptable,
- [ ] UX research has been reconciled into the design principles,
- [ ] three representative time horizons have been tested,
- [ ] collaboration flows have been tested with both sides,
- [ ] domain model and API are aligned with UI,
- [ ] offline and stale-state behavior is specified,
- [ ] accessibility requirements are included,
- [ ] wearable integrations remain optional,
- [ ] no clinical or unsupported claims are embedded in product copy.

## Current next actions

Priority order:

1. Finish and review deep UX research.
2. Convert findings into a revised cognitive model and UX principles.
3. Produce low-fidelity Direction Mode and Life Landscape prototypes.
4. Run user tests across daily, medium-term, and long-term scenarios.
5. Revise domain model and API contract from evidence.
6. Only then select the implementation stack.
