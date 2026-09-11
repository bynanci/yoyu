# UX Principles

> Status: v0.2 evidence-traceable. These principles combine published evidence, usability heuristics, accessibility standards, and Yoyu-specific product hypotheses. They are not clinical treatment claims.

## How to read this document

Every major principle must be traceable through four fields:

1. **Evidence** — what research, standard, or heuristic supports the mechanism.
2. **Design implication** — what Yoyu should do because of that evidence.
3. **Confidence** — confidence in the mechanism, not confidence that the current UI implementation works.
4. **Falsification condition** — what observed user behavior would force us to revise or remove the design rule.

Confidence levels:

| Level | Meaning |
| --- | --- |
| **High** | Strong review/meta-analytic evidence or normative standard. |
| **Moderate** | Multiple studies or strong theory, but indirect generalization to Yoyu. |
| **Exploratory** | Limited, heterogeneous, or context-specific evidence. |
| **Heuristic / Normative** | Design guidance or accessibility requirement rather than evidence of psychological benefit. |

## Traceability matrix

| Principle | Evidence | Design implication | Confidence | Falsification condition |
| --- | --- | --- | --- | --- |
| **1. Externalize, do not require memorization** | Intention-offloading research shows external reminders can support prospective memory and reduce reliance on internal remembering; reminder use is also shaped by metacognition and is not always optimal. [Gilbert et al., review](https://pmc.ncbi.nlm.nih.gov/articles/PMC9971128/) [Peper et al., 2023](https://pubmed.ncbi.nlm.nih.gov/36201804/) | Important future intentions, next Anchors, accepted responsibility, stale state, and pending confirmation should be visible or easily retrievable. Do not solve every problem by adding more reminders. | **High** for the mechanism; **Moderate** for Yoyu UI. | If users still need to mentally rehearse the same information, miss more intentions, or feel more reminder burden than a simpler baseline, revise the representation. |
| **2. Direction before detail** | Cognitive-load research distinguishes unavoidable task complexity from extraneous load caused by interface design. Progressive disclosure can reduce exposure to secondary options when the primary/secondary split is correct. [Darejeh et al., 2026](https://pubmed.ncbi.nlm.nih.gov/41849193/) [NN/g Progressive Disclosure](https://www.nngroup.com/articles/progressive-disclosure/) | Direction Mode should prioritize current context, next meaningful Anchor, what can wait, accepted responsibility, and one primary action while keeping necessary detail available. | **High** for reducing extraneous UI load; **Heuristic/Moderate** for the exact disclosure pattern. | If reduced views increase missed risks, repeated expansion, backtracking, or task errors, the interface is hiding too much and must restore context. |
| **3. Recognition over recall** | Nielsen's usability heuristic recommends making relevant state/actions visible rather than forcing users to remember information across screens. [NN/g Heuristic #6](https://www.nngroup.com/articles/ten-usability-heuristics/) | Show explicit labels such as `Waiting for acceptance`, `Last synced 18 min ago`, `Not decided`, and `Pending sync` rather than ambiguous icons or hidden state. | **Heuristic** | If explicit state increases scanning time or noise without improving state comprehension, reorganize or reduce visible status. |
| **4. Transitions are first-class** | Task-switching research consistently finds switch costs and shows preparation can reduce, but not eliminate, them. [Monsell, 2003](https://pubmed.ncbi.nlm.nih.gov/12639695/) [Vandierendonck et al., 2010](https://pubmed.ncbi.nlm.nih.gov/20565170/) | Model preparation, travel, waiting, handoff, recovery, and reorientation as Transitions when they help users move from one state to the next. | **High** for switch-cost mechanism; **Moderate** for daily-life mapping. | If explicit Transition UI adds complexity without improving initiation, preparation accuracy, or change recovery, simplify or remove it. |
| **5. Use cue → action planning selectively** | Implementation-intention research shows if–then plans can improve goal attainment, but rigid plans can have side effects when contexts differ from the planned situation. [Review](https://pmc.ncbi.nlm.nih.gov/articles/PMC4500900/) [Meta-analysis](https://pmc.ncbi.nlm.nih.gov/articles/PMC8149892/) [Non-planned effects](https://pubmed.ncbi.nlm.nih.gov/28666568/) | For appropriate Transitions, offer concrete cue + response framing, but keep it optional, reversible, and condition-aware. | **High** for implementation intentions generally; **Moderate** for this product use. | If users follow stale conditions, feel trapped by the plan, or fail to adapt after context changes, reduce automation and expose review/escape paths. |
| **6. Semantic zoom, not calendar zoom** | Construal Level Theory proposes that psychologically distant events are represented more abstractly and near events more concretely. [Trope & Liberman, 2010](https://pubmed.ncbi.nlm.nih.gov/20438233/) [Temporal construal](https://pubmed.ncbi.nlm.nih.gov/12885109/) | Changing time scale changes information semantics: near = timing/action/transition; far = paths/conditions/values/possibilities. Never invent precise dates for distant intentions. | **High** for theory; **Moderate** for Yoyu UX. | If users lose continuity between scales, confuse long-term possibilities with commitments, or gain no comprehension benefit versus a conventional calendar, revise semantic zoom. |
| **7. Room and uncertainty are legitimate states** | Research suggests uncertainty can contribute to stress in controlled threat contexts, but the generalization to everyday planning is limited. Autonomy research supports preserving user choice and volition. [de Berker et al., 2016](https://www.nature.com/articles/ncomms10996) [SDT meta-analysis](https://pubmed.ncbi.nlm.nih.gov/32437175/) | Represent free time, intentional rest, optional activity, stale information, unknowns, postponed decisions, and intentionally open questions explicitly. Do not convert all empty regions into “available capacity.” | **Exploratory** for uncertainty → everyday stress; **Moderate–High** for autonomy as a construct. | If open states mainly produce confusion, forgotten decisions, or avoidance without preserving perceived control, redesign the state model and review cues. |
| **8. Collaboration without supervision** | Household mental-labor research shows that planning, anticipating, deciding, and monitoring are themselves work; transactive-memory research shows cognition can be distributed across close partners. [Mental labor systematic review](https://pmc.ncbi.nlm.nih.gov/articles/PMC10148620/) [Wegner et al., 1991](https://pubmed.ncbi.nlm.nih.gov/1774630/) | Separate responsibility, support, visibility, edit rights, and consent. Handoff requires explicit acceptance. A read receipt or delivered notification never equals ownership. | **High** for mental-labor literature; **Moderate** for app collaboration mechanics. | If one person still has to create, assign, remind, monitor, and verify everything, or if ownership becomes less clear, the collaboration model has failed. |
| **9. Preserve agency** | Self-Determination Theory supports autonomy, competence, and relatedness as meaningful motivational constructs. [SDT intervention meta-analysis](https://pubmed.ncbi.nlm.nih.gov/32437175/) [SDT overview](https://selfdeterminationtheory.org/) | Suggest rather than silently decide. Users can decline, postpone, stay private, remain undecided, ask for support, and revoke sharing where technically possible. | **High** for the construct; **Moderate** for Yoyu interaction rules. | If users report feeling managed by the system or partner, frequently undo hidden automation, or cannot understand why a decision was made, agency has not been preserved. |
| **10. Explainable state and change** | Visibility of system status, user control, error recovery, and recognition-over-recall are established usability heuristics. [NN/g usability heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/) | Change Preview must show what changed, what stayed valid, what is stale/risky, who needs to confirm, whether the change is local or server-confirmed, and the next recovery action. | **Heuristic** | If users cannot distinguish proposal vs confirmation, local vs synced, or reversible vs committed changes, the state model or copy must change. |
| **11. Calm until needed** | Calm technology argues that technology can move between the periphery and center of attention; this is a design philosophy rather than evidence of clinical benefit. Cognitive-load evidence supports avoiding unnecessary interface demands. | Default surfaces should stay low-noise; critical Anchor, risk, conflict, or explicit handoff can become salient when needed. Notifications are not an engagement mechanism. | **Heuristic / Moderate** | If users miss important information because the interface is too quiet, or feel interrupted despite low task value, recalibrate salience and notification thresholds. |
| **12. Minimalism must remain accessible** | WCAG 2.2 requires or recommends accessible focus, non-drag alternatives, target sizing, understandable operation, and other accessibility behaviors. [WCAG 2.2](https://www.w3.org/TR/WCAG22/) | Minimalism must not mean low contrast, tiny targets, gesture-only semantic zoom, motion-dependent meaning, or color-only status. | **Normative** | Failure of applicable WCAG requirements is a direct design failure, not a hypothesis to rationalize away. |

## 1. Externalize, do not require memorization

Users should not have to remember hidden plans, responsibilities, prior agreements, or sync state.

Prefer:
- visible next Anchor,
- visible accepted ownership,
- explicit freshness / sync status,
- context-sensitive external cues,
- concise status language.

Avoid:
- hidden workflow history,
- ambiguous pending icons,
- reminder spam,
- requiring the user to remember what a blank field meant.

## 2. Direction before detail

When a user explicitly wants a reduced-information view, prioritize orientation rather than completeness.

Direction Mode should answer:

```text
Where am I now?
What matters next?
What can wait?
Who has already accepted responsibility?
What is the next useful action, request, or intentional non-action?
```

### Guardrail

Progressive disclosure must not hide:
- a time-critical Anchor,
- a known conflict,
- missing confirmation,
- stale shared state,
- an external reservation that has not actually changed.

## 3. Recognition over recall

State labels must be interpretable without remembering previous screens.

Prefer:
- `Waiting for Alex to accept`
- `Last synced 18 min ago`
- `Not decided yet`
- `Saved locally — not shared yet`

Avoid:
- icon-only state,
- `Pending` with no explanation,
- checkmarks that mix local, remote, and shared confirmation.

## 4. Transitions are first-class

Yoyu should help users understand how to move between states, not merely what the destination event is.

Possible Transition components:
- preparation,
- stopping the current activity,
- travel,
- waiting,
- handoff,
- recovery,
- reorientation.

A Transition is shown only when it adds useful orientation. It is not mandatory ceremony around every event.

## 5. Cue → action planning is optional

Examples:

```text
When it is 17:10 → begin getting ready.
When Alex accepts the handoff → you no longer need to monitor it.
When travel time becomes uncertain → reopen Change Preview.
```

Do not hard-code cue-response chains when the context is volatile or the user prefers to decide later.

## 6. Semantic zoom, not calendar zoom

| Scale | Primary representation | Do not default to |
| --- | --- | --- |
| Today | next actions, Anchors, active Transition timing | dense hourly grid |
| Week–Month | rhythm, commitments, flexible regions | every micro-task |
| Quarter–Year | phases, experiments, conditions, review points | fake precision |
| 1–3 Years | paths, dependencies, decision windows | fixed deadline chains |
| 3–10 Years | life shape, values, possibilities, open questions | ten-year Gantt chart |

Semantic zoom must preserve continuity: a user should understand how a long-term direction relates to a nearer block without implying every current action serves a ten-year objective.

## 7. Room is a first-class state

The product must represent:
- free time,
- rest,
- undecided time,
- optional activity,
- postponed decisions,
- intentionally private space,
- intentionally open questions.

A free region is not automatically optimization capacity.

`Unknown`, `Not decided`, `No action needed`, and `Missing data` are distinct states.

## 8. Collaboration without supervision

For any shared item, keep these dimensions separate:

1. **Responsibility** — who is accountable / planning / executing / monitoring when relevant.
2. **Support** — who may assist.
3. **Visibility** — who may see the information.
4. **Editability** — who may modify it.
5. **Consent** — whose explicit approval is required.

Rules:
- `readReceipt != consent`
- `notificationDelivered != handoffAccepted`
- `sharedVisibility != editPermission`
- a handoff is not complete until the intended owner explicitly accepts and the authoritative state is committed.

## 9. Preserve agency

The user must be able to:
- choose,
- decline,
- postpone,
- stay private,
- remain undecided,
- ask for support,
- undo where feasible,
- revoke sharing where technically possible.

No silent auto-rescheduling or automatic responsibility reassignment.

## 10. Explainable change

Change Preview should answer:

1. What changed?
2. What did not change?
3. What is stale, risky, or now impossible?
4. Who must confirm?
5. What is only local / pending sync?
6. What is the next recovery action?

Third-party reservations must never be shown as updated unless an integration actually confirms the external change.

## 11. Calm until needed

Default:
- low visual noise,
- no engagement bait,
- no “you have not opened Yoyu today” notification,
- no streaks or productivity scores.

Escalate salience only when the user needs to notice:
- a meaningful Anchor,
- an approaching Transition,
- an explicit handoff request,
- a known conflict,
- a sync/permission failure that changes meaning.

## 12. Minimalism must remain accessible

Target WCAG 2.2 AA where applicable.

Minimum expectations:
- sufficient text and UI contrast,
- readable type at system scaling,
- visible keyboard/focus state,
- state not conveyed by color alone,
- reduced-motion support,
- non-drag alternatives,
- semantic zoom accessible through explicit controls as well as gestures,
- adequate pointer target sizing,
- explicit labels for assistive technology,
- recovery paths for destructive actions.

Reference: https://www.w3.org/TR/WCAG22/

## Visual system direction

- Typography is the primary hierarchy.
- Spacing and hairline dividers are preferred over card-heavy layouts.
- Large Life Blocks should feel spatial and editorial, not tabular.
- Critical Anchors use stronger contrast and weight.
- Secondary context uses lower emphasis while remaining readable.
- Status remains understandable without decorative color.
- Motion clarifies Transition; it never becomes the only explanation of state.
- Uncertainty is represented explicitly, not hidden behind visual softness.

## UX anti-patterns

Do not introduce:
- streaks,
- life scores,
- shame-based overdue states,
- forced daily check-ins,
- continuous partner monitoring,
- `AI knows what you need` copy,
- invisible auto-rescheduling,
- automatic responsibility reassignment,
- reminder volume as a substitute for clarity,
- low-contrast “calm” UI that obscures risk,
- gesture-only timeline navigation,
- medical claims that a screen reduces ADHD or anxiety symptoms without appropriate evidence.

## UI decision record template

Every non-trivial UI decision should be documented using this template in a PR, issue, design note, or future decision log:

```md
### Decision: <short name>

**Evidence**
- Source(s):
- What the evidence actually establishes:
- Population / context limits:

**Design implication**
- UI behavior being proposed:
- Why this is the smallest useful translation:

**Confidence**
- High / Moderate / Exploratory / Heuristic / Normative
- Confidence in mechanism:
- Confidence in this Yoyu implementation:

**Falsification condition**
- What user behavior or metric would make us revise/remove this design?
- What baseline or alternative will we compare against?
```

## Required validation metrics

For important screens, prefer:
- time to orientation,
- next-step identification accuracy,
- proposed vs confirmed comprehension,
- stale / offline / pending-sync comprehension,
- responsibility comprehension,
- unnecessary action count,
- recovery success after change/conflict,
- subjective cognitive effort,
- perceived pressure,
- perceived control / autonomy.

Do **not** treat the following as proof that the UX is working:
- daily active use by itself,
- time spent in app,
- number of created tasks,
- number of notifications sent,
- streak length.

## Current validation questions

- Can users identify the next relevant thing faster in Direction Mode than in a full agenda without missing critical state?
- Does explicit Transition information improve initiation or preparation versus an event-only view?
- Can users move between Today, Year, and 3–10 year scales without confusing direction with commitment?
- Does externalized ownership allow one person to genuinely stop monitoring after an accepted handoff?
- Can users distinguish `intentionally open` from `forgotten / overdue / missing data`?
- Does the minimal UI reduce interface effort without hiding information required for a safe decision?

## References

- Gilbert SJ et al. *Outsourcing Memory to External Tools: A Review of Intention Offloading.* https://pmc.ncbi.nlm.nih.gov/articles/PMC9971128/
- Darejeh A et al. *Cognitive Load Measurement Methods for Usability Testing.* https://pubmed.ncbi.nlm.nih.gov/41849193/
- Monsell S. *Task switching.* https://pubmed.ncbi.nlm.nih.gov/12639695/
- Vandierendonck A et al. *Task switching: interplay of reconfiguration and interference control.* https://pubmed.ncbi.nlm.nih.gov/20565170/
- Trope Y, Liberman N. *Construal-level theory of psychological distance.* https://pubmed.ncbi.nlm.nih.gov/20438233/
- Reich-Stiebert N et al. *Gendered Mental Labor: A Systematic Literature Review...* https://pmc.ncbi.nlm.nih.gov/articles/PMC10148620/
- Wegner DM et al. *Transactive memory in close relationships.* https://pubmed.ncbi.nlm.nih.gov/1774630/
- Nielsen Norman Group. *10 Usability Heuristics for User Interface Design.* https://www.nngroup.com/articles/ten-usability-heuristics/
- Nielsen Norman Group. *Progressive Disclosure.* https://www.nngroup.com/articles/progressive-disclosure/
- W3C. *WCAG 2.2.* https://www.w3.org/TR/WCAG22/

## Validation rule

No principle graduates from “plausible” to “validated for Yoyu” because a paper exists.

The chain must be:

```text
Evidence
→ Design implication
→ Confidence
→ Prototype
→ Comparative usability test
→ Falsification condition
→ Keep / revise / remove
```
