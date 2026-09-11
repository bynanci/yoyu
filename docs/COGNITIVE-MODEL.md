# Cognitive Model

> Status: v0.2 evidence-traceable pre-development hypothesis. This document separates published evidence from Yoyu-specific design inference. It does **not** claim that Yoyu treats ADHD, anxiety, or any clinical condition.

## Purpose

Yoyu should reduce the amount of life coordination a person must keep active in working memory while preserving autonomy, uncertainty, and flexibility.

The product is being designed as an **external cognitive scaffold** rather than a system that decides a user's life for them.

```text
Context
  ↓
ORIENT     Where am I in time / space / life context?
  ↓
ANCHOR     What matters next?
  ↓
BOUND      What does not need attention now?
  ↓
TRANSITION How do I move from the current state to the next?
  ↓
OFFLOAD    What no longer needs to stay in working memory?
  ↓
SHARE      Who has explicitly accepted responsibility?
  ↓
ACT        What is the smallest useful action, request, or intentional non-action?
  ↓
FEEDBACK   What actually happened, synced, changed, or still needs confirmation?
```

A separate cross-cutting rule applies across the model:

```text
SEMANTIC ZOOM
near ─────────────────────────── far
concrete                         abstract

action / timing                  values / possibilities

AGENCY
system suggests ─────────────── user decides
```

## Evidence policy

Every important cognitive claim is classified by evidence strength **for the mechanism**, not by whether Yoyu itself has been validated.

| Confidence | Meaning in this repository |
| --- | --- |
| **High** | Supported by a systematic review, meta-analysis, strong review literature, or normative standard; still may be indirect to Yoyu. |
| **Moderate** | Supported by multiple studies or a strong review, but generalization to this product or population is indirect. |
| **Exploratory** | Limited, heterogeneous, context-specific, or single-study evidence. Useful for hypotheses, not product claims. |
| **Heuristic / Normative** | Usability guidance, design analogy, or accessibility requirement rather than evidence of psychological benefit. |

**Important:** a high-confidence mechanism does not imply high confidence that a particular Yoyu screen works. Every Yoyu-specific design implication requires usability validation.

## Evidence → design traceability

| Cognitive mechanism | Evidence | Design implication | Confidence | Falsification condition |
| --- | --- | --- | --- | --- |
| **Prospective memory / intention offloading** | A review of intention offloading concludes that external reminders can be highly effective and are influenced by metacognitive judgments; people may also show stable reminder-use biases. See [Gilbert et al., 2023, PMC9971128](https://pmc.ncbi.nlm.nih.gov/articles/PMC9971128/) and [Peper et al., 2023](https://pubmed.ncbi.nlm.nih.gov/36201804/). | Externalize future intentions as Anchors and context-sensitive cues. Do not require users to continuously rehearse future plans. Do not assume more reminders are always better. | **High** for offloading as a mechanism; **Moderate** for Yoyu's representation. | If users with Yoyu Anchors still rely on memory as much as before, miss intentions at the same or higher rate, or experience more reminder burden than a simpler baseline, revise the offloading design. |
| **Adult ADHD and time perception / time management** | A 2023 adult ADHD review found some studies showing differences in time estimation, reproduction, and management, but emphasized scarce evidence, heterogeneous methods, and inconsistent results. See [Mette, 2023, PMC9962130](https://pmc.ncbi.nlm.nih.gov/articles/PMC9962130/). | Treat externalized time as an accessibility-support hypothesis, not as a diagnostic assumption. Never design around the claim that every ADHD user has the same form of “time blindness.” | **Exploratory–Moderate** due heterogeneous adult evidence. | If target users do not benefit from externalized timing, or if time cues create pressure without improving orientation, do not justify the feature merely by ADHD labeling. |
| **Extraneous cognitive load** | A 2026 systematic review of 87 interface studies distinguishes intrinsic task complexity from avoidable interface-induced cognitive load and summarizes measurement approaches such as performance metrics and NASA-TLX. See [Darejeh et al., 2026](https://pubmed.ncbi.nlm.nih.gov/41849193/). | Direction Mode should remove interface-generated clutter while retaining information necessary for a correct decision. Measure cognitive effort rather than assuming visual minimalism reduces load. | **High** for measurement/construct use in usability; **Moderate** for specific Yoyu reductions. | If reduced views lower visible information but increase errors, backtracking, hidden-state confusion, or mental effort, the UI is over-minimized and must restore context. |
| **Task switching and transition cost** | Task-switching reviews show slower and often more error-prone performance after switching; preparation can reduce but not eliminate switch cost. See [Monsell, 2003](https://pubmed.ncbi.nlm.nih.gov/12639695/) and [Vandierendonck et al., 2010](https://pubmed.ncbi.nlm.nih.gov/20565170/). | Treat Transition as a first-class domain concept: preparation, travel, waiting, handoff, recovery, and reorientation may matter more than the destination event alone. | **High** for switch cost; **Moderate** for mapping it to daily-life transitions. | If explicit Transition information adds steps or visual burden without improving initiation, preparation accuracy, or change recovery versus a simpler event model, simplify or remove it. |
| **Implementation intentions / cue-to-action planning** | Reviews and meta-analyses indicate that if–then planning can improve goal attainment, while effects vary and overly specific plans can have costs in unplanned situations. See [Gollwitzer-related review, PMC4500900](https://pmc.ncbi.nlm.nih.gov/articles/PMC4500900/), [Wang et al., 2021, PMC8149892](https://pmc.ncbi.nlm.nih.gov/articles/PMC8149892/), and [Bieleke et al., 2018](https://pubmed.ncbi.nlm.nih.gov/28666568/). | When useful, express a Transition as a clear cue + response: “When X becomes true, do Y.” Do not force all goals into rigid if–then automation. | **High** for implementation intentions generally; **Moderate** for Yoyu transitions. | If cue-based next actions create rigidity, inappropriate behavior in changed contexts, or reduce users' willingness to adapt, make conditions optional and expose escape/review paths. |
| **Temporal construal / psychological distance** | Construal Level Theory proposes that psychologically distant events are represented more abstractly, while near events are represented more concretely. See [Trope & Liberman, 2010](https://pubmed.ncbi.nlm.nih.gov/20438233/) and [Liberman & Trope, 2003](https://pubmed.ncbi.nlm.nih.gov/12885109/). | Semantic zoom should change information meaning, not merely magnification: near = timing/action/transition; far = paths/conditions/values/possibilities. | **High** for the theory/review; **Moderate** for this UX implementation. | If users cannot maintain continuity between scales, interpret abstract long-term states as commitments, or perform no better than calendar zoom, revise the scale semantics. |
| **Uncertainty and stress** | In a controlled aversive-learning experiment, subjective uncertainty tracked subjective and physiological stress. The context was threat/electric shock and should not be generalized directly to everyday planning. See [de Berker et al., 2016](https://www.nature.com/articles/ncomms10996). | Distinguish known, unknown, stale, proposed, and intentionally open states. Reduce false ambiguity, but do not remove legitimate uncertainty or claim that this will reduce clinical anxiety. | **Exploratory** for everyday planning UX. | If explicit uncertainty labels increase confusion or worry without improving state comprehension, revise wording and hierarchy. Do not infer therapeutic benefit from comprehension alone. |
| **Autonomy / self-determination** | Self-Determination Theory research supports autonomy, competence, and relatedness as meaningful motivational constructs; meta-analysis of SDT-based health interventions found small positive average effects with theory-specified mediators. See [Ntoumanis et al., 2021](https://pubmed.ncbi.nlm.nih.gov/32437175/) and [Self-Determination Theory](https://selfdeterminationtheory.org/). | Preserve user control: suggest rather than silently decide; allow decline, postpone, private space, intentional non-action, and revocation where technically possible. | **High** for SDT constructs; **Moderate** for Yoyu interaction rules. | If users report less perceived control, feel managed by partners/system defaults, or frequently reverse hidden automation, autonomy-preserving design has failed. |
| **Household mental labor** | A 2023 systematic review describes household cognitive labor such as anticipating, identifying options, deciding, and monitoring; invisible planning/monitoring can itself be burdensome. See [Reich-Stiebert et al., 2023, PMC10148620](https://pmc.ncbi.nlm.nih.gov/articles/PMC10148620/). | Responsibility must represent more than execution. The model should be able to distinguish planning, execution, monitoring, and support when needed, without forcing all complexity into the UI. | **High** for household mental-labor literature; **Moderate** for product modeling. | If shared responsibility merely shifts planning/monitoring work to one partner, or one person still has to assign, remind, and verify everything, the collaboration model has failed. |
| **Transactive memory in close relationships** | Classic experimental work shows that close partners can form a transactive memory system in which knowledge is distributed across people and coordination benefits from knowing “who knows what.” See [Wegner et al., 1991](https://pubmed.ncbi.nlm.nih.gov/1774630/). | Yoyu may support “who is carrying/knows what” so users do not need to duplicate all cognitive work. Handoff must be explicit and accepted. | **Moderate**; foundational but older and not a direct app study. | If explicit ownership increases duplicated checking, mistrust, or caregiver burden rather than allowing a person to stop monitoring, revise the collaboration model. |
| **Recognition rather than recall** | Nielsen's usability heuristic recommends making relevant state/actions visible rather than forcing users to remember them across screens. This is a usability heuristic, not clinical evidence. See [NN/g usability heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/). | Surface proposed/accepted/stale/offline/pending states in context. Prefer descriptive status to ambiguous icons or hidden history. | **Heuristic** | If visible state creates more scanning and slower decisions than a simpler presentation, reduce or reorganize it rather than citing the heuristic as proof. |
| **Progressive disclosure** | NN/g describes progressive disclosure as initially showing important options while making advanced/secondary options available on demand. See [Progressive Disclosure](https://www.nngroup.com/articles/progressive-disclosure/). | Keep optional detail available but subordinate; do not hide high-frequency or safety-critical information. | **Heuristic** | If users repeatedly open hidden detail to complete normal tasks, or miss critical state because it was collapsed, the disclosure boundary is wrong. |
| **Accessibility / multiple input paths** | WCAG 2.2 is a normative accessibility standard, including requirements for focus visibility, non-drag alternatives, target sizing, and predictable interaction. See [WCAG 2.2](https://www.w3.org/TR/WCAG22/). | Semantic zoom, reordering, and timeline interactions must not rely solely on drag, pinch, color, or fine motor precision. | **Normative** | Accessibility failures against applicable WCAG criteria are direct failures, not hypotheses to rationalize away. |

## Primary cognitive problems to support

### 1. Prospective memory

Remembering to do something in the future can require ongoing monitoring or reliance on internal memory.

Yoyu response:
- externalize important Anchors,
- expose relevant situational cues,
- show preparation before the Anchor when useful,
- distinguish reminder configuration from guaranteed delivery,
- avoid reminders for every trivial action.

### 2. Working-memory and interface load

The product should not force people to mentally integrate state scattered across multiple screens or remember hidden workflow history.

Yoyu response:
- prioritize current context and next Anchor,
- keep optional detail available but subordinate,
- make responsibility and freshness visible,
- measure whether Direction Mode reduces effort without hiding necessary context.

### 3. Intention → action gap

Knowing a goal does not necessarily answer “what do I do now?”

Yoyu response:
- represent Transitions explicitly,
- optionally use cue → action framing,
- expose the smallest meaningful next action,
- allow intentional non-action and “not now” as legitimate states.

### 4. Context switching and transition cost

Moving between places, roles, plans, or activities may require preparation and reconfiguration.

Yoyu response:
- model preparation, travel, waiting, handoff, recovery, and reorientation when they matter,
- show what remains stable across a change,
- avoid abrupt hidden auto-rescheduling.

### 5. Uncertainty

Unknown information is different from missing data, a rejected proposal, an unaccepted handoff, or an intentionally open choice.

Yoyu response:
- preserve explicit uncertainty states,
- show what is known, unknown, stale, proposed, or awaiting confirmation,
- do not manufacture precise dates or confident reassurance.

### 6. Distributed and transactive cognition

Shared life coordination can be distributed across people, devices, calendars, routines, and external artifacts.

Yoyu response:
- make responsibility transfer explicit,
- separate memory support from shared agreement,
- keep personal, shared, visibility, editability, and consent as different dimensions,
- treat devices and calendars as optional nodes rather than universal sources of truth.

## Direction Mode

Direction Mode is intentionally invoked by the user. It must not claim to detect or diagnose anxiety.

It should answer:

```text
Where am I?
What matters next?
What can wait?
Who has explicitly accepted responsibility?
What is the next useful action, request, or intentional non-action?
```

A valid answer may be:

> Nothing needs action right now. The next confirmed Anchor is later today.

The system should not fill free time merely because capacity appears available.

### Direction Mode falsification test

Compare Direction Mode against a conventional agenda / full-context baseline.

Reject or revise the design if users:
- identify the next relevant Anchor less accurately,
- miss important risk or confirmation state more often,
- take longer because essential information is hidden,
- report equal or higher cognitive effort,
- feel more controlled or pressured.

## Semantic zoom specification

| Horizon | Cognitive representation | UI priority |
| --- | --- | --- |
| **Today** | concrete | action, timing, Anchor, active Transition |
| **Week–Month** | mixed | rhythm, commitments, flexible regions |
| **Quarter–Year** | more abstract | phases, experiments, conditions, review points |
| **1–3 years** | abstract | paths, dependencies, decision windows, reversible choices |
| **3–10 years** | highly abstract | desired life shape, values, possibilities, intentionally open questions |

Long-term direction may connect to current action, but the product must not imply that every present action must serve a ten-year goal.

## Responsibility model implication

“Who executes?” is not always the same as “who plans?” or “who keeps monitoring?”

The domain model should be able to express, where useful:

```text
Responsibility
├─ accountable
├─ planningOwner
├─ executionOwner
├─ monitoringOwner
├─ supporters[]
├─ handoffStatus
└─ acceptedAt
```

The UI should only expose this complexity when it improves comprehension. The data model must not assume execution ownership eliminates the cognitive labor of planning or monitoring.

## Open questions as a first-class concept

“Not decided” must not collapse into “task incomplete.”

Candidate domain representation:

```text
OpenQuestion {
  prompt
  status: intentionally_open | needs_information | awaiting_shared_decision
  reviewWindow?
  decisionDependencies[]
}
```

This is currently a **product hypothesis**, not a research-proven construct. It should be tested against simpler representations.

## Cognitive anti-patterns

Avoid:

- treating “ADHD” as a uniform cognitive profile,
- claiming that a calm interface treats anxiety,
- showing the entire backlog during overload,
- using more reminders as a substitute for better external structure,
- too many simultaneous CTAs,
- ambiguous “done” states for shared work,
- auto-generated deadlines for distant goals,
- shame-based overdue language,
- hiding stale or unsynced state,
- forcing every intention into rigid if–then automation,
- repeated reminders when ownership is unclear,
- inferring emotional state from behavior or biometrics without an explicitly validated and consented use case.

## Product hypotheses to validate next

| Hypothesis | Test | Success signal | Failure / cancellation condition |
| --- | --- | --- | --- |
| **H1 Direction Mode** | Compare reduced Direction Mode with full agenda during an overload-like scenario. | Faster and more accurate next-step identification without losing critical state. | More missed Anchors, more hidden-state errors, or equal/higher effort. |
| **H2 Transition** | Compare event-only vs event + Transition preparation. | Better initiation/preparation accuracy and fewer “what now?” moments. | Added steps without measurable benefit. |
| **H3 Semantic Zoom** | Ask users to reason about the same life situation at Today, Year, and 3–10 year scales. | Users understand the change in abstraction and do not confuse directions with commitments. | Users lose continuity or interpret possibilities as deadlines. |
| **H4 Offloading** | Compare Anchor/cue support with a basic reminder or no external support. | Lower prospective-memory burden and equal/better completion accuracy. | Reminder burden rises or users still need to mentally rehearse everything. |
| **H5 Responsibility** | Run paired collaboration tasks with explicit handoff and a conventional shared-task baseline. | Both parties correctly identify ownership and one party can stop monitoring after accepted handoff. | Planning/monitoring burden remains concentrated or ownership is misunderstood. |
| **H6 Open Question** | Compare intentionally-open state with blank field / overdue task representation. | Users recognize “not decided yet” without treating it as failure. | Users use it as an unclear dumping ground or lose track of decisions that truly require action. |

## Measurement guidance

Early research should prioritize usability and cognition rather than engagement metrics.

Prefer:
- time to orientation,
- next-step identification accuracy,
- responsibility comprehension,
- confirmed/proposed/stale-state comprehension,
- unnecessary action count,
- recovery after change or sync conflict,
- subjective cognitive effort (for example, brief task-level rating or carefully selected workload measure),
- perceived pressure,
- perceived control / autonomy.

Do not use as primary proof of product value:
- time in app,
- streaks,
- number of notifications sent,
- number of tasks created,
- daily active use in isolation.

## References

- Mette C. *Time Perception in Adult ADHD: Findings from a Decade—A Review.* 2023. https://pmc.ncbi.nlm.nih.gov/articles/PMC9962130/
- Gilbert SJ et al. *Outsourcing Memory to External Tools: A Review of Intention Offloading.* 2023. https://pmc.ncbi.nlm.nih.gov/articles/PMC9971128/
- Peper P, Alakbarova D, Ball BH. *Benefits from prospective memory offloading depend on memory load and reminder type.* 2023. https://pubmed.ncbi.nlm.nih.gov/36201804/
- Monsell S. *Task switching.* 2003. https://pubmed.ncbi.nlm.nih.gov/12639695/
- Vandierendonck A et al. *Task switching: interplay of reconfiguration and interference control.* 2010. https://pubmed.ncbi.nlm.nih.gov/20565170/
- Trope Y, Liberman N. *Construal-level theory of psychological distance.* 2010. https://pubmed.ncbi.nlm.nih.gov/20438233/
- Liberman N, Trope Y. *Temporal construal.* 2003. https://pubmed.ncbi.nlm.nih.gov/12885109/
- de Berker AO et al. *Computations of uncertainty mediate acute stress responses in humans.* 2016. https://www.nature.com/articles/ncomms10996
- Reich-Stiebert N et al. *Gendered Mental Labor: A Systematic Literature Review...* 2023. https://pmc.ncbi.nlm.nih.gov/articles/PMC10148620/
- Wegner DM et al. *Transactive memory in close relationships.* 1991. https://pubmed.ncbi.nlm.nih.gov/1774630/
- Darejeh A et al. *Cognitive Load Measurement Methods for Usability Testing.* 2026. https://pubmed.ncbi.nlm.nih.gov/41849193/
- W3C. *Web Content Accessibility Guidelines (WCAG) 2.2.* https://www.w3.org/TR/WCAG22/
- Nielsen Norman Group. *10 Usability Heuristics for User Interface Design.* https://www.nngroup.com/articles/ten-usability-heuristics/
- Nielsen Norman Group. *Progressive Disclosure.* https://www.nngroup.com/articles/progressive-disclosure/

## Validation principle

Every important cognitive principle in Yoyu must be traceable through:

```text
Evidence
→ Design implication
→ Confidence
→ UI behavior
→ Measurable task
→ Falsification condition
→ Decision: keep / revise / remove
```

A cognitive theory is evidence for a possible mechanism. It is never, by itself, evidence that Yoyu's implementation works.
