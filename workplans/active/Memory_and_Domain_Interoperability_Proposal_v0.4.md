# General Memory, Scientific Inquiry and Governed Engineering: Interoperability

**Conceptual Cross-System Architecture Proposal**

**Version:** 0.4 — repairs the v0.3 contracts challenged by the independent review; supersedes `Memory_and_Domain_Interoperability_Proposal_v0.3.md` as a review candidate only
**Date:** 2 November 2026
**Status:** PROPOSED — unratified; pending independent re-review of the changed contracts and review by the UPMS, SSDS and SCIRE developers
**Author:** Claude (AI, Opus 5.5), at the product owner's request and under the owner's decisions below
**Related document:** `SCIRE_Conceptual_Proposal_v0.4.md`

**Inputs**

| Input | Identity | Role |
| --- | --- | --- |
| Interoperability Proposal v0.3 | SHA-256 `b4a594ae1b4369cf064565c7a25d8ff0b402d1fbaaa5f2b2c38464ce2c64c916` | Base text |
| SCIRE v0.3 Independent Concept-Level Review (Codex, OpenAI family) | SHA-256 `60dae8f585390ccb6636aa4513aa6155ac0c1b378ea4299ef4656d0078435021` | SC-31–SC-33, V3-01–V3-13 |
| Agent-Centered Memory and Domain Knowledge Interoperability v0.2 | SHA-256 `634d4e8aeeb208e6d25e7136e196c098b0c6bfc79216934e0e92a3ae13f31c5e` | Predecessor properties the review asked to restore (cache revocation) |
| Product owner's decisions | This design conversation, 2 November 2026 | D-A to D-J, as listed in the SCIRE v0.4 header |

**Owner decisions bound by this revision** (summarized; the SCIRE v0.4 header gives them in full):

- **D-A** — Separation by responsibility: UPMS holds an agent's or team's general context and logistics; SCIRE holds scientific argument and discussion.
- **D-B** — SCIRE is the proposal layer; SSDS owns the decided model and implementations.
- **D-C** — The PI decides what goes to SSDS to build; SCIRE never executes; SSDS executes only what a user requested.
- **D-D** — Independent systems with their own governing authorities; citation-like links and automated transfer serve traceability and developmental data flow, not operation.
- **D-E** — Every system stays available when a link is unresolved; a particular consequential use that needs the missing backing may be refused or qualified.
- **D-F** — Finalization is the hand-off of a model to SSDS; other scientific outcomes need no finalization.
- **D-G** — Several PIs: scoped authority, joint sign-off where required, never last-writer.
- **D-H** — Overrides of unresolved objections are scoped, reasoned, visible, and never count as resolution.
- **D-I** — Retention, metadata disclosure and revocation belong to the source owners; writer access never authorizes retention.
- **D-J** — Smallest first product; the owner sets error and cost limits before each experiment.

**Review boundary.** This proposal does not amend accepted SSDS D1–D4, PEM, UPMS policy or SCIRE scientific semantics. Each system's own governing process decides its internals.

---

## 0. Summary

Three systems persist information over time. They are separated by **responsibility for the content**, not by the number of users and not by private versus shared:

| System | Responsibility |
| --- | --- |
| **UPMS** | The general contextual record and logistics of an agent or a team: what happened, commitments, schedules, unfinished work, and where the owning records live |
| **SCIRE** | Scientific discussion and argument, and the scoped scientific outcomes it produces. It is the **proposal layer**; one of its outcomes is a model finalized by the PI for hand-off to SSDS. It never executes |
| **SSDS** | The models it is asked to build, adopted under its own D1–D4 governance; their implementations; execution a user requests; realized results; PEM |

The main flow is **SCIRE → SSDS**: the PI decides which finalized models go to SSDS, and SSDS implements and executes only what a user requests. SSDS's results and findings can flow back to SCIRE as evidence. UPMS remembers that this work exists and points to the owning records.

The three systems and their projects are **independent, with their own governing authorities**. They cite each other through citation-like links and may transfer models and feedback automatically, for traceability and development. An unresolved link never stops a system; it can only limit a particular consequential use that needs the missing backing.

There is no shared kernel and no compulsory universal domain ontology. The few exchanges that exist do need **small exchange contracts**: agreed meanings for record identity, revision, outcome and qualification states, and restriction handling. Derived content crossing systems under confidentiality constraints is the one problem no single system can fully control; §7 gives it a bounded floor and a trust model.

---

## 1. Why the Systems Are Separate

### 1.1 One word, three responsibilities

An agent remembers that a meeting happened and that a calculation is pending. A scientific environment keeps the structure and history of a contested hypothesis. An engineering system keeps the model a code must preserve and the lessons from past failures. All persist and retrieve, but what each must guarantee differs.

### 1.2 Costs of consolidation

A universal kernel couples lifecycles and object models, turns local features into cross-project changes, spreads schema migrations, creates a shared failure domain, and tends to accumulate domain exceptions.

### 1.3 Costs of separation

SCIRE and UPMS each need access scopes, revocation, release-set lineage and derived views. These are not small: they are the mechanisms UPMS Candidate 4.1 failed review on. Separation by responsibility accepts that cost. Shared libraries may be extracted when two implementations show the same stable semantics (§10).

---

## 2. Memory, Agency and Authority

- **Memory** retains and retrieves information relevant to current activity.
- **Agency** reasons about goals, chooses tools and acts.
- **Authority** decides which consequential actions or state changes are permitted and accepted within a domain.

UPMS may tell an agent that a calculation was approved; recalling it does not make it approved. SCIRE may identify a promising investigation; that does not let it bypass SSDS's execution controls. PEM may surface an engineering lesson; historical success does not make it accepted authority.

---

## 3. Responsibility, Ownership and Custody

### 3.1 Matrix

| Content | Owner | Notes |
| --- | --- | --- |
| What happened in an agent's or team's work; commitments; schedules; navigation cues | UPMS | Verified against the owning domain for consequential use |
| Scientific discussion records and observations recorded in SCIRE | SCIRE | |
| Questions, hypotheses, objections, evidence assessments, decisions, discovery history | SCIRE | Proposal layer |
| Scoped scientific outcomes (null results, exclusions, characterizations, supported claims, open contradictions) | SCIRE; decided under project rules | Need no finalization |
| Finalized models for hand-off | SCIRE; finalized by the PI within their scope | |
| The decision to build a finalized model | The PI, as an SSDS user | Never a consequence of transfer |
| Models adopted for implementation (D1, D2), architecture (D3), implementations (D4) | SSDS and its authority owners | Adoption relates to an exact package version and may narrow it |
| Execution, realized results, qualification | SSDS, on a user's request | |
| Engineering lessons, failure families, applicability | SSDS PEM | Non-authoritative under PEM's own rules |
| Laboratory data, literature, external datasets | Their own systems | Referenced by SCIRE |
| Access, retention and disclosure enforcement | The system holding the resource, under the source owner's policy | |
| Cross-system references, contextual summaries, caches | Held by consumers, subordinate to the owners | |

**One canonical owner per record.** Storage location never confers semantic or decision authority.

### 3.2 Responsibility is not custody

Separation by responsibility decides who owns the **meaning** of content. It does not move records between systems.

- **Scientific content first recorded in UPMS.** A mixed-purpose conversation held in UPMS may contain scientific statements. The **original record stays in UPMS's custody**, under UPMS's access and retention rules. When someone brings the content into SCIRE, SCIRE creates its own interpretation and, where retention in SCIRE is permitted (§7), an authorized imported copy citing the original. UPMS may add a link to the SCIRE record. The original is never replaced by a pointer, and access or retention responsibilities never transfer silently. Any UPMS assessment of the scientific content has **no scientific standing**.
- **Logistics in SCIRE.** Meeting times and assignments that arise in a scientific meeting stay in SCIRE's source record as said. SCIRE does not manage them; whoever wants them tracked records them in UPMS.
- **Scientific status in summaries.** A UPMS overview may say "SCIRE question Q is open; three positions are live". It cannot say which is right. For consequential use, the consumer dereferences SCIRE, and for adopted models, SSDS.

### 3.3 Outcome, finalized, adopted, executed

These states are distinct, each with one owner:

- **Outcome decided** (SCIRE): a scoped scientific result stands for a stated purpose. Publication is an outcome decision.
- **Finalized** (SCIRE, by the PI): a model is finished for hand-off, with exact statement versions, use, regime, basis, applicable unresolved objections and overrides, and authority rule.
- **Adopted for implementation** (SSDS): a user has asked SSDS to build the model, and SSDS has adopted it, possibly narrowed, through its own governance. The adoption cites the exact SCIRE package version. SCIRE's finalization is never relabeled as SSDS-adopted.
- **Executed** (SSDS): SSDS has run an implementation a user requested, with its execution outcome and qualification.

No consumer may present an inquiry decision as a finalized model, or a finalized model as adopted or executed.

---

## 4. Independent Operation

- **UPMS without SCIRE or SSDS:** general contextual record and logistics.
- **SCIRE without UPMS or SSDS:** full scientific discussion, inquiry, outcomes and finalization. Calculations needing governed execution stay recorded as needed.
- **SSDS without SCIRE or UPMS:** governed work under its own D1–D4 and PEM. A model can enter SSDS without ever having been in SCIRE.

**Availability versus eligibility (D-E).** A link from one system to another's record identifies that record and its revision, like a citation. Two properties are kept apart:

- **Availability.** An unresolvable link never stops a system, never stops unrelated work, and never changes a record's historical status. A past decision is not undone because its cited source is unreachable.
- **Eligibility of a particular use.** A new consequential use that needs the missing backing (a decision, a finalization, a publication, a broader claim, an authorization) may be refused or qualified until the backing is available. Independently sufficient local evidence, or an authorized snapshot, can satisfy it instead. A snapshot is evidence of what the source said at its revision, not authority over the source; current authorizations still follow their owner's freshness rule.

Each system and project keeps its own governing authority. A link never extends one system's authority into another.

**Failure isolation.** A failure or upgrade of one system degrades only the uses that depend on it. An unavailable, unauthorized or unreachable system is reported as such. No response is never evidence that a record does not exist or that an obligation was fulfilled.

**Independent lifecycle.** Each system is versioned, reviewed and released on its own. Coordination is needed only when an exchange contract another system relies on changes.

---

## 5. Referential Memory

### 5.1 UPMS remembers where to look

When an agent or team takes part in scientific or engineering work, UPMS keeps enough to reconnect: which project, what problem, what was decided and by which system, what is pending, which records hold the details, which revision a recollection refers to, and whether it is a summary or a verified state.

### 5.2 Why duplication is dangerous

An agent may remember that hypothesis H was favored; SCIRE may since have recorded an objection. The memory remains true as history but no longer establishes current status. An agent may remember that a workplan was approved; that cannot show the approval still applies to the current revision.

### 5.3 Consequential dereferencing

Casual continuity does not require verifying every remembered detail. Scientific interpretation, execution authorization, publication and material engineering decisions require the owning system's current, applicable record, or a qualified result when it cannot be obtained (§4). Dereferencing covers the **modality** of a scientific statement, not only its status: a remembered "X is true" whose SCIRE record says "hypothesized, AI interpretation, unconfirmed" must not be repeated as an assertion.

### 5.4 Contextual summaries carry their source

A UPMS summary about another system's record keeps the record's identity, its revision where known, the retrieval time, and a label that it is a contextual summary. Where the revision is unknown, that stays visible. A summary carries the restrictions of what it summarizes (§7).

### 5.5 Derived views stay with their owner

UPMS may keep overviews of an agent's or team's work. SCIRE keeps its compass. SSDS exposes its own governed state. A UPMS overview that mentions a SCIRE question is a derivative of a derivative, never a substitute for SCIRE's record, and a summary of an SSDS approval never authorizes execution.

---

## 6. Exchanges

### 6.1 Principles

- **Domain-native operations.** A caller uses the receiver's declared operations and semantics. No generic mutation interface.
- **Small exchange contracts, no universal ontology.** Each exchange agrees on the meanings it needs: record identity and revision, the outcome and qualification states below, and how restrictions are expressed (§7.3). Nothing else is shared. A receiver that does not support a restriction or state it is given returns a qualified refusal; it never guesses a translation.
- **Narrow and versioned.** Each system publishes only the operations others need. Changing a relied-upon contract needs compatibility consideration; internal changes stay local.
- **Transport is not authority.** MCP or another transport authenticates a call; the receiver decides whether it is permitted.
- **Unsupported is explicit.** A missing operation or field is never read as approval, a negative finding, or proof that no data exist. Receivers never invent revisions, source spans, permissions or statuses.

### 6.2 The first operations

Only the operations needed for §8.2 and §8.4 are defined. **Every operation is optional** (D-D).

| Operation | Caller → owner | Carries | Returns | On failure |
| --- | --- | --- | --- | --- |
| **Resolve link** | Any system or agent → the cited system | Record identity, optional revision, intent (orientation, current state, history, source), the caller's identity and audience | The record or view for that intent, its revision, retrieval time, coverage, visibility limits stated without revealing hidden items | Unavailable / unauthorized / not found *in scope*; never "does not exist" |
| **Transfer model package** | SCIRE → SSDS, manual or automatic, when the PI decides | Exact statement versions, use and regime, basis statement with citation-like links, evidence qualification and usability, applicable unresolved objections and overrides, pending review obligations, limitations, the PI's finalization and authority rule, restrictions (§7.3) | Receipt with transfer identity | Stays in SCIRE as finalized, not transferred |
| **Transfer feedback** | SSDS → SCIRE, manual or automatic | Citations to SSDS results with execution outcome and qualification; adoption decisions with the exact package version and any narrowing; SSDP findings or tensions about the project's science with asserter; restrictions | SCIRE observation, decision or question identity | SSDS's records stay authoritative; SCIRE shows nothing new |
| **Record context** | Agent → UPMS | A contextual note with links to SCIRE or SSDS records, and its restrictions | UPMS record identity, or refusal if retention is not permitted | No effect on SCIRE or SSDS |

**Execution outcome** is one of: completed, failed, canceled, requested with outcome unknown, known not performed. **Qualification** is one of: qualified for a stated scope, unqualified, provisional, failed, unknown. Origin never implies qualification.

A model-package transfer is not a build or run request. SSDS builds and executes only on a user's request, through its own interface and governance. Whether transfers are automated is each system's own choice.

### 6.3 Retrieval intent and coverage

Orientation, historical recollection, current-state verification, justification, source inspection and task resumption are different intents and may get different answers. A consequential request gets the owner's records or a qualified failure, not a free-text narrative. Results state their revision or as-of time, retrieval time, conditions, and known limits such as index watermark, capture coverage, inaccessible records or excluded scopes, without revealing protected items. A caller must not downgrade a current-state request to an unchecked memory narrative.

### 6.4 Delivery

Transfers have identifiable outcomes: sent, received, recorded or refused. Retrying a transfer must not create duplicate records; transfer identities and idempotency rules are defined at the receiving boundary. Build and execution requests are SSDS's own user operations and follow SSDS's rules. No atomic transaction across systems is assumed: if SSDS records a result and SCIRE has not received it, SSDS's record stays authoritative and SCIRE reconciles later.

---

## 7. Lineage and Release Across Systems

### 7.1 Three predicates

Three permissions are distinct predicates, checked separately (D-I):

- **Read or use** a source, possibly for a limited purpose.
- **Retain** content derived from it in a given scope or system.
- **Disclose** content derived from it to a given recipient.

Reading a source, receiving a summary, or supervising an agent grants neither retention nor disclosure. A paraphrase, summary, extracted statement, reviewer verdict or "new insight" derived from a source is still derived from it.

### 7.2 What each system can see

Each system knows what it released into the contexts it mediates. None sees what an agent read in another system, or outside every system, before writing.

- **Within a system,** release-set lineage is enforceable for mediated contexts: the system records which restricted records it released into a context, and everything produced there inherits their restrictions until an **authorized reset** (a reset the governing policy defines, which verifiably starts a context without those records or anything derived from them). Child contexts, retained summaries and continuations inherit the parent's set. UPMS and SCIRE each adopt this floor.
- **Across systems,** an agent that reads restricted content in one system and writes into another moves content the receiver cannot trace on its own.

### 7.3 Rules

1. **Retention is checked before storing.** A receiving system stores new content only if retention in the target scope is permitted for every restriction the content carries. Content of unknown lineage is stored only in a scope the receiver's policy authorizes for unknown-lineage content (a quarantine), if one exists; otherwise the write is refused with a qualified reason. Writer access alone never authorizes retention.
2. **Restrictions are conjunctive.** Content derived from several sources satisfies every source's restrictions. One owner's approval never releases another owner's material. A clearance is bound to the exact output, audience, purpose and scope it covers. Owners may authorize standing grants for precisely scoped classes.
3. **Carried constraints, with a trust model.** When content moves between systems, its restrictions travel with it as part of the exchange contract.
   - Constraints are accepted only from **trusted producers**: a system's own mediated contexts, or an adapter each receiving system has explicitly designated as trusted for that purpose. The declaration is bound to the producing context's identity.
   - A **missing** declaration is unknown lineage, never an empty restriction set. An empty set is valid only when a trusted producer affirmatively declares that its mediated context held no restricted content.
   - A restriction the receiver cannot interpret causes a qualified refusal.
   - Untrusted or unmediated writes are unknown lineage (rule 1).
4. **Audience-scoped generation.** Content meant for an audience is generated, where possible, in a context built only from sources that audience may see. This is preventive: it reduces exposure, but does not replace rules 1 and 2, because a purpose limitation may forbid retaining or disclosing even content the audience may read.
5. **Metadata is protected.** The existence of a restricted source, its title, its contributors' roles and its lineage are restricted unless the source's policy says otherwise. Routing data, coverage statements and refusals describe their authorization scope in general terms and never reveal whether a particular hidden item exists.
6. **Unknown means not cleared.** The receiver distinguishes **forbidden** (a restriction prohibits the action) from **awaiting clearance** (permission unknown or review pending).
7. **Owner review across project boundaries.** Disclosure beyond a project requires review by the owners of the restricted sources in the release set, not only the approval of the supervising person.
8. **Revocation.** Earlier readers are not "unseen". A revocation governs every later read, export and serving of derived content, including cached summaries and stored references: serving a stored derivative to a new reader after revocation is a new disclosure, and a cache never becomes a route around revocation. Disclosures are made under grants with an expiry or a revalidation rule; a consumer that cannot revalidate when required withholds. Content already published under a valid clearance stays published unless the owner's policy says otherwise.

### 7.4 Trust boundary and declared gaps

The guarantees hold for content a system mediates and for constraints from trusted producers. Content an agent or person brings from outside every mediated context is a **declared gap**: it is treated as unknown lineage, and the person bringing it remains responsible for it, as in ordinary scientific confidentiality. No system claims complete mediation of agents it does not run.

### 7.5 When shared machinery would be justified

A shared release log is **one candidate** among several, not the default answer. E3 (§12) compares per-system scoped contexts, trusted constraint transport and designated adapters, authorized review and standing grants, and only then a shared log. A shared log helps only if producers, relevant reads, context continuations and output paths are bound to it; storage centralization alone does not provide mediation. Any shared runtime would reopen D-D and needs the owner's decision.

---

## 8. Cross-System Scenarios

### 8.1 Resuming an investigation

An agent recalls from UPMS that a SCIRE question is open. It resolves the link in SCIRE and works from the question's live positions, unresolved objections and pending needs.

### 8.2 From finalized model to implementation

A SCIRE question converges. The PI finalizes a model ("harmonic approximation, valid below 300 K") with its basis statement, evidence and their qualification, and the override of an objection about anharmonic samples. The PI decides it should be built, and SCIRE transfers the package. Nothing happens in SSDS until a user requests the implementation there. SSDS adopts the model through its own governance; it may narrow it ("below 250 K") or refuse. SSDS records the adoption against the exact package version, builds and runs only what was requested, and returns feedback with execution outcomes and qualification. SCIRE records the narrowing as related to its finalization without relabeling it, and assesses the results.

### 8.3 A discriminating calculation

SCIRE records the need for a calculation that would discriminate between two positions. A user who wants it requests it in SSDS or carries it out elsewhere. The result returns with its origin, execution outcome and qualification. SCIRE never runs it and never submits it on its own.

### 8.4 An SSDS finding becomes a SCIRE question

An SSDS run shows an anomaly its D1 does not explain. SSDS keeps the finding; with feedback transfer enabled, it also becomes a SCIRE question citing the run and the D1 claim. If the PI later finalizes a revised model, it goes back as a new package, and SSDS rebuilds only on a user's request.

### 8.5 Learning from engineering failure

PEM preserves an evidence-backed lesson under its own governance. An agent later asks PEM. PEM assesses applicability. UPMS does not declare the lesson valid in a new project.

### 8.6 Cross-project discovery

An agent sees that project B's work bears on project A. The connection is shown only where the full transfer is permitted. Otherwise the agent sends B's owner a request that does not itself reveal protected information from A.

### 8.7 Unreachable SSDS

- **Before any request:** SCIRE keeps the calculation need recorded as not done.
- **After a request was sent, before an outcome arrived:** SCIRE shows "requested, outcome unknown". It does not report "not performed".
- **After a result was recorded:** the result stays recorded with its outcome and qualification.
- **A new consequential use needing current SSDS state** (for example a broader publication claim backed only by an SSDS result, or a current authorization): refused or qualified until SSDS is reachable or an authorized snapshot suffices (§4).

Unrelated SCIRE work continues throughout. An agent that remembers an SSDS approval reports it as history and does not treat it as current.

### 8.8 A discrepancy and an unavailable SSDS

SCIRE has an open discrepancy question and SSDS is unavailable. SCIRE continues the inquiry and keeps the explanations live. UPMS may remember the open question but must not publish a harmonized "resolved" result.

---

## 9. Multiple Agents and Teams

### 9.1 Scopes

UPMS may hold individual and team scopes. Team membership does not merge members' private records, and scientific project records remain SCIRE's regardless of who participates.

### 9.2 Attribution

Cross-system interactions distinguish: the authenticated actor invoking an operation; the person or agent who originated an assertion; the agent that interpreted or transformed it; the person authorized to approve; and the system that recorded the result. A shared credential never erases attribution or manufactures human authorization.

### 9.3 Independence

Independent review has dimensions: context, sources seen, model family, prompt, tools, evaluation standard and external evidence. A high-consequence review states the separation it can support. Agreement from shared inputs is not counted as independent corroboration, though separately derived arguments remain individually inspectable. A reviewer given restricted evidence produces a verdict derived from it; releasing that verdict more widely is a separate disclosure decision.

---

## 10. Shared Machinery

### 10.1 No shared kernel

UPMS is organized around events and contextual records, SCIRE around questions and statements, PEM around engineering lessons and applicability. Their lifecycles differ. A shared kernel would need many domain exceptions.

### 10.2 Shared utilities

Access scopes, revocation, release-set lineage and restriction handling appear in both UPMS and SCIRE, so they are the first candidates for a shared **library** once both designs have stable semantics. A library is not a runtime: each system keeps its own records and failure domain.

### 10.3 Extraction criteria

Extract a common component only when its semantics are stable across independent consumers, the total system becomes simpler, and domain changes no longer need repeated changes to the shared part. The burden of proof lies with consolidation.

---

## 11. Alternatives

A qualitative comparison under D-A–D-D, not a measured ranking.

| Alternative | Assessment |
| --- | --- |
| A. Complete consolidation | Not recommended: semantic and development coupling without demonstrated need |
| B. Independent semantics on a compulsory shared storage engine | Not an initial requirement |
| C. Fully independent systems with ad hoc integration | Better isolation, but brittle links and unclear authority |
| D. Independent systems, separated by responsibility, with a few named exchanges and small exchange contracts | **Recommended baseline** |
| E. D plus a shared release log or common mediation layer | One candidate for cross-system release control, to be compared in E3 (§7.5); would reopen D-D |
| F. Notebook- or ELN-first SCIRE with typed annotations | A credible first SCIRE prototype if the host can enforce the §7 predicates (SCIRE v0.4 §15) |

---

## 12. Adoption Sequence

1. **Independent development.** Each system continues under its own process. SCIRE starts with its smallest demonstration and paper counterexamples (SCIRE v0.4 §15).
2. **Interoperability discovery.** For each concrete cross-system use, record the owner, consumer, operation, data, authorization, failure behavior, intent, and which restricted sources could flow into a shared output.
3. **First operations.** Implement only the §6.2 operations needed for §8.2 and §8.4, through MCP servers or equivalent. Test each system standalone, and again with every link unresolvable.
4. **Adversarial contract tests.** Attempt to: retain a derivative where retention is forbidden; send a missing constraint declaration and have it read as empty; reveal a hidden item's existence through a refusal or coverage statement; serve a cached derivative after revocation; launder restricted content through summaries; present remembered approval as current; hide objections through partial retrieval; present an inquiry decision as a finalized model, or a finalized model as adopted or executed; make a transfer trigger a build; report "not performed" for a request whose outcome is unknown.
5. **E3 — Derivative flow.** The case set and comparison in SCIRE v0.4 §15, with the trusted actors and mediated outputs declared. The owner sets the acceptance rule before the study. The result decides whether alternative E is proposed.
6. **Shared utilities.** After real deployments, extract libraries only by §10.3.

---

## 13. Requirements

**INT-01 — Separation by responsibility.** UPMS owns general contextual record and logistics; SCIRE owns scientific discussion, argument and outcomes; SSDS owns adopted models, implementations and execution. Responsibility is not custody: original records stay where they were recorded.

**INT-02 — Finalize, decide, build.** A finalized model is a scoped PI decision; the PI decides what goes to SSDS; a transfer never requests a build or run; SSDS adopts, builds and executes only on a user's request and relates its adoption to the exact package version.

**INT-03 — Single canonical owner.** References, summaries and caches never create a competing authority.

**INT-04 — Availability versus eligibility.** Each system and project is independent with its own governing authority; an unresolved link never stops a system or changes a historical status, but may limit a particular consequential use that needs it.

**INT-05 — Small exchange contracts.** Integration uses named, domain-native operations with agreed meanings for identity, revision, outcome, qualification and restrictions; no universal ontology and no generic mutation interface.

**INT-06 — Consequential dereferencing.** Consequential reliance uses the owner's current, applicable record, including modality, or returns a qualified result.

**INT-07 — Explicit authorization.** Retrieved memory and tool access never authorize state changes in another system.

**INT-08 — Permission predicates.** Read, retain and disclose are checked separately; retention before storing; restrictions conjunctive; carried constraints only from trusted producers, a missing declaration being unknown lineage; metadata protected; unknown is not cleared; revocation governs later disclosure, including caches.

**INT-09 — Honest coverage.** "Not found" is scoped; results state revision, freshness and coverage without revealing hidden items; unsupported fields and restrictions are declared, never invented.

**INT-10 — History versus present.** A remembered state is distinguishable from current state; a later correction is never presented as what was known earlier.

**INT-11 — Exact outcomes and recoverable exchange.** Execution outcome and qualification are carried exactly; "outcome unknown" is never reported as "not performed"; transfers are idempotent at the receiver.

**INT-12 — Agreement is not independence.** Multiple agents' agreement from shared sources is not independent evidence.

**INT-13 — Data, not instructions.** Imported memory, evidence and discussion text never carry authority to act.

**INT-14 — Evidence-driven sharing.** Shared libraries only by §10.3; any shared runtime only after E3 and an owner decision reopening D-D.

---

## 14. Risks

| Risk | Failure | Response |
| --- | --- | --- |
| Content in the wrong system | Scientific status asserted from UPMS context | §3.2: no scientific standing; bring content into SCIRE, keeping UPMS custody |
| Inquiry decision or transfer taken as a build | Software runs under an unfinalized or unrequested model | INT-02, §3.3 |
| Remembered state taken as current | Obsolete decisions acted on | INT-06, INT-10 |
| Retention without permission | A derivative stored where its source forbids it | INT-08 rule 1 |
| Missing constraints read as empty | Restricted content treated as clean | INT-08 rule 3 |
| Metadata leakage | A refusal or coverage note reveals a hidden item | INT-08 rule 5, INT-09 |
| Revocation bypass through caches | Revoked content served to a new reader | INT-08 rule 8 |
| Over-restriction | Collaboration blocked | Audience-scoped generation; standing grants; awaiting-clearance state |
| Link treated as a dependency | A system stalls, or reports false "not done" | INT-04, INT-11 |
| Interface creep | Exchange contracts grow into a shared schema | Only the meanings listed in §6.1 |
| Duplicate access machinery diverges | Inconsistent revocation and scope semantics | Shared library once stable (§10.2) |
| Prompt injection through memory or documents | Retrieved text triggers actions | INT-13 |

---

## 15. Open Questions

1. **For the UPMS developer:** does UPMS's claim and judgment model need an explicit marker that its assessments of scientific content carry no standing (§3.2), and how does UPMS express restrictions in the exchange contract (§7.3)?
2. **For the SSDS developer:** how does a transferred package enter D1 review when a user requests the build; how are adoption narrowing and qualification states expressed; and should SSDP findings flow to SCIRE automatically?
3. Which adapters, if any, should each system designate as trusted producers of carried constraints, and on what evidence?
4. What reset is authorized and verifiable for each system's mediated contexts?
5. What grant expiry or revalidation interval do source owners need, and what does a disconnected consumer do when it lapses?
6. What minimum package content is usable by SSDS without either system depending on the other's internal formats?
7. Which operations beyond §6.2 does a real second use case need?

---

## Appendix A. Change Map from v0.3

| Finding | v0.3 | v0.4 |
| --- | --- | --- |
| SC-31 / V3-01 | §7.3(3): unknown lineage retained in the writer's narrowest scope; carried constraints without a trust model; revocation left open | Three predicates; retention before storing with quarantine only if authorized; conjunctive restrictions; carried constraints from trusted producers, missing ≠ empty; metadata protection; forbidden versus awaiting clearance; grants, expiry and cache revocation; declared gaps (§7, INT-08) |
| SC-33 / V3-03 | §4, INT-04: a link "does not create a dependency" and never blocks; §8.7: unreachable SSDS means "not done" | Availability versus eligibility (§4, INT-04, D-E); execution-outcome states; "outcome unknown" (§6.2, §8.7, INT-11) |
| SC-32 / V3-02 | §6.2: package carries overruled objections only | Package carries applicable unresolved objections, overrides and pending review obligations (§6.2) |
| V3-06 | §3.3: finalization as the end state of all scientific work | Outcome, finalized, adopted, executed as distinct states; adoption cites the exact package version and may narrow it (§3.1, §3.3, D-F) |
| V3-08 | §6.2: "SSDS-governed" results without qualification | Execution outcome and qualification carried separately; origin never implies qualification (§6.2) |
| V3-11 | §3.2: UPMS keeps only a pointer after import | Responsibility is not custody; original stays in UPMS; authorized imported copy (§3.2, INT-01) |
| Review §8, F-17 | §6.1: no shared schema | Small exchange contracts with agreed meanings; no universal ontology (§0, §6.1, INT-05) |
| Review §7, confidentiality | §7.3: audience-scoped generation "avoids taint tracking entirely" | Preventive only (§7.3 rule 4) |
| Review §9 | §7.4: shared release log as the one trigger | One candidate among several; mediation requirements; reopens D-D (§7.5, alternative E) |
| Review §8, editorial | Appendix A said "six named operations" | Four operations, listed in §6.2 |
| Review §9 | §11: no ELN-first option | Alternative F (§11) |
| — | INT-01–14 | INT-01–14, revised (§13) |
