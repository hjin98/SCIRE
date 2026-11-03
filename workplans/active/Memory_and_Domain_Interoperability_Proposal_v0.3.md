# General Memory, Scientific Inquiry and Governed Engineering: Interoperability

**Conceptual Cross-System Architecture Proposal**

**Version:** 0.3 — consolidated revision after concept-level review; supersedes `Agent_Centered_Memory_and_Domain_Interoperability_Proposal_v0.2.md` as a review candidate only
**Date:** 2 November 2026
**Status:** PROPOSED — unratified; pending independent (different-family) concept review and review by the UPMS, SSDS and SCIRE developers
**Author:** Claude (AI, Opus 5.5), at the product owner's request and under the owner's decisions below
**Related document:** `SCIRE_Conceptual_Proposal_v0.3.md`

**Inputs**

| Input | Identity | Role |
| --- | --- | --- |
| Agent-Centered Memory and Domain Knowledge Interoperability v0.2 | SHA-256 `634d4e8aeeb208e6d25e7136e196c098b0c6bfc79216934e0e92a3ae13f31c5e` | Base text |
| SCIRE Integration v0.2 Concept-Level Review | `SCIRE_Integration_v0.2_Independent_Concept_Review.md` | Findings SC-A, SC-B, F-01–F-20 |
| Product owner's decisions, 2 November 2026 | This design conversation | D-A and D-B below; delegation of the remaining findings to the author's discretion |
| UPMS Architecture Manual, Review Candidate 4.1 | SHA-256 `19a9e3edd77d4543ae1343fa0a7bba88dd92a0625a2514ee1f5138deab1d57df` | Context only; unratified, same-family review NO-PASS |

**Owner decisions bound by this revision**

- **D-A — Separation by responsibility.** "The distinction is not the number of user, or even private vs. public. It is separation of responsibility … the UPMS serves for general memory and logistics, while SCIRE stores scientific argument and discussion histories. One serves for an agent or team's general contextual record, the other is specific to scientific argument and discussions."
- **D-B — SCIRE is the proposal layer.** "SCIRE is the proposal layer, SSDS owns the decided model and implementations. The output of SCIRE is the input to SSDS."

**Title change.** v0.2 called UPMS "agent-centered". Under D-A, UPMS serves an agent *or a team*, so the title and file name drop that term. The lineage is kept by the input table above.

**Review boundary.** This proposal does not amend accepted SSDS D1–D4, PEM, UPMS policy or SCIRE scientific semantics. Each system's own governing process decides its internals.

---

## 0. Summary

Three systems persist information over time, and all three can be called "memory". They are separated by **responsibility for the content**, not by the number of users and not by private versus shared:

| System | Responsibility |
| --- | --- |
| **UPMS** | The general contextual record and logistics of an agent or a team: what happened, commitments, schedules, unfinished work, and where the authoritative records live |
| **SCIRE** | Scientific discussion and argument: questions, hypotheses, objections, evidence assessments, inquiry decisions and discovery history. It is the **proposal layer** |
| **SSDS** | Decided scientific models and their implementations (D1–D4), governed execution, realized results and Project Engineering Memory (PEM) |

The main flow is **SCIRE → SSDS**: SCIRE's proposals are SSDS's inputs. SSDS's decisions and results come back to SCIRE as recorded decisions and evidence. UPMS remembers that this work exists and what is pending, and points to the owning records.

Each system works without the others. They interact through a small number of named, domain-native operations, not through a shared kernel, schema or generic envelope. One problem — derived content crossing systems with confidentiality constraints — cannot be fully solved by any one system. That problem is stated, given a floor, and named as the only current reason that could justify shared machinery later.

---

## 1. Why the Systems Are Separate

### 1.1 One word, three responsibilities

An agent remembers that a meeting happened and that a calculation is pending. A scientific environment keeps the structure and history of a contested hypothesis. An engineering system keeps the decided model a code must preserve and the lessons from past failures. All persist and retrieve, but what each must guarantee differs. Shared persistence does not imply a shared semantic architecture.

### 1.2 Costs of consolidation

A universal kernel couples lifecycles and object models, turns local features into cross-project changes, spreads schema migrations, creates a shared failure domain, and tends to accumulate domain exceptions until it is more complex than separate systems. These costs are high while all three systems are still being designed.

### 1.3 Costs of separation, stated honestly

Separation is not free. SCIRE and UPMS each need access scopes, revocation, release-set lineage and derived views. v0.2 called this "acceptable duplication". It is not small: these are the mechanisms UPMS Candidate 4.1 failed review on. The owner's separation by responsibility accepts that cost. Shared *utilities* (libraries) for these mechanisms may be extracted when two implementations show the same stable semantics (§10).

---

## 2. Memory, Agency and Authority

Three functions stay separate:

- **Memory** retains and retrieves information relevant to current activity.
- **Agency** reasons about goals, chooses tools and acts.
- **Authority** decides which consequential actions or state changes are permitted and accepted within a domain.

UPMS may tell an agent that a calculation was approved; recalling that does not make it approved. SCIRE may identify a promising investigation; that does not let it bypass SSDS's execution controls. PEM may surface an engineering lesson; historical success does not make it accepted authority. These hold whether the systems are integrated or standalone.

---

## 3. Responsibility and Ownership

### 3.1 Matrix

| Content | Owner | Notes |
| --- | --- | --- |
| What happened in an agent's or team's work; commitments; schedules; navigation cues | UPMS | Subject to verification against the owning domain for consequential use |
| Scientific discussion records (messages, transcripts, attached artifacts of scientific meetings) | SCIRE | |
| Questions, hypotheses, objections, evidence assessments, inquiry decisions, discovery history | SCIRE | Proposal layer |
| Proposals to SSDS (investigation requests, model proposals, challenges) | SCIRE authors them; SSDS decides them | |
| Decided scientific models and methods (D1, D2), architecture (D3), implementations (D4) | SSDS and its authority owners | |
| Governed execution, realized results, qualification evidence | SSDS | |
| Engineering lessons, failure families, applicability | SSDS PEM | Non-authoritative under PEM's own rules |
| Laboratory data, literature, external datasets | Their own systems | Referenced, not owned, by SCIRE |
| Access enforcement | The system that owns the resource | |
| Cross-system references, contextual summaries, caches | Held by consumers, subordinate to the owners | |

**One canonical owner per record.** Many systems may refer to, index or summarize a record. Storage location never confers semantic or decision authority.

### 3.2 Content that sits near the boundary

Separation by responsibility needs a rule for content that arrives in the "wrong" system.

- **Scientific content in UPMS.** An agent working with a researcher in an ordinary session will capture scientific statements in UPMS's general record. UPMS keeps them as context ("we discussed whether strain drives the transition"). Any UPMS assessment of such a statement is contextual and has **no scientific standing**. When the content matters scientifically, someone brings it into SCIRE with its attribution and source; from then on SCIRE owns it, and UPMS keeps a pointer.
- **Logistics in SCIRE.** Meeting times, task assignments and reminders that arise in a scientific meeting may be kept in SCIRE's discussion record as said. SCIRE does not manage them; an agent or team that wants them tracked records them in UPMS.
- **Scientific status in summaries.** A UPMS overview may say "SCIRE question Q is open; three positions are live". It cannot say which position is right. For consequential use the consumer dereferences SCIRE, and for decided models, SSDS.

### 3.3 Decided versus proposed

"Decided" in a scientific sense means accepted by an SSDS project's D1 or D2 owner. SCIRE records inquiry decisions (what to investigate, which hypothesis to work under for now, what to propose, what to submit for publication), which are attributed human decisions about the inquiry. A SCIRE inquiry decision never governs SSDS software, and no consumer may present it as a decided model.

---

## 4. Independent Operation

- **UPMS without SCIRE or SSDS:** general contextual record and logistics for unrelated work.
- **SCIRE without UPMS or SSDS:** full scientific discussion and inquiry from its own records. Investigations that need governed execution are recorded as proposed and not performed; evidence from other sources is accepted with its production class.
- **SSDS without SCIRE or UPMS:** governed work under its own D1–D4 and PEM. Neither other system is a runtime dependency for independently authorized work.

**Failure isolation.** A failure or upgrade of one system degrades only the integrations that depend on it. An unavailable, unauthorized or unreachable system is reported as such. No response is never evidence that a record does not exist or that an obligation was fulfilled.

**Independent lifecycle.** Each system is versioned, reviewed and released on its own. Coordination is needed only when an operation another system relies on changes.

---

## 5. Referential Memory

### 5.1 UPMS remembers where to look

When an agent or team takes part in scientific or engineering work, UPMS keeps enough to reconnect: which project, what problem, what was decided and by which system, what is pending, which records hold the details, which revision a recollection refers to, and whether it is a summary or a verified state. It does not duplicate SCIRE's argument record or SSDS's authority.

### 5.2 Why duplication is dangerous

An agent may remember that hypothesis H was favored; SCIRE may since have recorded a challenge. The memory remains true as history but no longer establishes current status. An agent may remember that a workplan was approved; that cannot show the approval still applies to the current revision.

### 5.3 Consequential dereferencing

Casual continuity does not require verifying every remembered detail. Scientific interpretation, execution authorization, publication and material engineering decisions require the owning system's current, applicable record. Dereferencing covers the **modality** of a scientific statement (hypothesized, asserted, quoted), not only its current status: a remembered "X is true" whose SCIRE record says "hypothesized by the AI, unconfirmed" must not be repeated as an assertion.

### 5.4 Contextual summaries carry their source

A UPMS summary about another system's record keeps the record's identity, its revision where known, the retrieval time, and a label that it is a contextual summary. Where the revision is unknown, that stays visible.

### 5.5 Derived views stay with their owner

UPMS may keep overviews of an agent's or team's work. SCIRE keeps its compass. SSDS exposes its own governed state. These do not share storage or algorithms. A UPMS overview that mentions a SCIRE question is a derivative of a derivative, never a substitute for SCIRE's record, and a summary of an SSDS approval never authorizes execution.

---

## 6. Interfaces

### 6.1 Principles

- **Domain-native operations.** A caller uses the receiver's declared operations and semantics. No universal `update_memory` with unconstrained payloads, no generic envelope that becomes a shared schema.
- **Narrow and versioned.** Each system publishes only the operations others need. Internal schemas are not contracts. Changing a relied-upon operation needs compatibility consideration; internal changes stay local.
- **Transport is not authority.** MCP or another tool transport authenticates a call; the receiver decides whether it is permitted. A tool call is a request, not acceptance.
- **Unsupported is explicit.** A missing operation or field is never read as approval, a negative finding, or proof that no data exist. Receivers never invent revisions, source spans, permissions or statuses they cannot supply.

### 6.2 The first operations

Only the operations needed by the first cross-system use (§8) are defined. Others are added when a concrete use case needs them.

| Operation | Caller → owner | Carries | Returns | On failure |
| --- | --- | --- | --- | --- |
| **Resolve reference** | UPMS (or agent) → SCIRE / SSDS | Record identity, optional revision, intent (orientation, current state, history, source) | The record or view for that intent, its revision, retrieval time, coverage, visibility limits | Unavailable / unauthorized / not found *in scope*; never "does not exist" |
| **Submit investigation request** | SCIRE → SSDS | Question, positions, assumptions, observables, discriminating outcome, proposed acceptance criteria, scope, approver | Request identity and receipt | Recorded in SCIRE as proposed, not sent |
| **Submit model proposal or challenge** | SCIRE → SSDS | Proposed statement, assumption or regime (or the objection), evidence links, objection state, approver | Request identity; later, SSDS's decision by reference | As above |
| **Publish result or decision** | SSDS → SCIRE | Reference to the SSDS decision or governed result, its revision and scope | SCIRE receipt | SSDS's record stays authoritative; SCIRE reconciles later |
| **Persist scientific finding** (optional) | SSDS → SCIRE | An SSDP finding or tension about a project's science, with its SSDS binding and asserter | SCIRE question or objection identity | SSDS keeps the finding in its own home |
| **Record context** | Agent → UPMS | A contextual note with references to SCIRE or SSDS records | UPMS record identity | No effect on SCIRE or SSDS |

Whether SCIRE is a designated home for SSDP findings is an SSDS decision.

### 6.3 Retrieval intent and coverage

Orientation, historical recollection, current-state verification, justification, source inspection and task resumption are different intents and may get different answers. A consequential request gets the owner's records or a qualified failure, not a free-text narrative. Results state their revision or as-of time, retrieval time, relevant conditions, and known limits such as index watermark, inaccessible records or excluded scopes. A caller must not downgrade a current-state request to an unchecked memory narrative to get an answer.

### 6.4 Delivery

Consequential operations have identifiable outcomes: received, validated, accepted or refused, completed or failed, result published. Retries must not duplicate a computation or authorization; request identities and idempotency rules are defined at the receiving boundary. No atomic transaction across systems is assumed. If SSDS publishes a result and SCIRE fails to record it, the SSDS result stays authoritative and SCIRE reconciles later. If UPMS fails to record an interaction, nothing in SCIRE or SSDS is undone.

---

## 7. Lineage and Release Across Systems

### 7.1 Three permissions

Where they matter, three permissions are distinct: **read or use** a source; **retain** content in a new scope or system; **disclose** derived content to a recipient. Reading a source, receiving a summary, or supervising an agent does not grant disclosure. A paraphrase, summary, extracted statement or "new insight" can reveal protected content without quoting it.

### 7.2 What each system can see

Each system knows what it released into each session or production context. None sees what an agent read in another system before writing. So:

- **Within a system,** release-set lineage is enforceable: the system records what restricted records it released into a context, and everything produced in that context inherits their constraints until a validated reset. UPMS and SCIRE each adopt this floor.
- **Across systems,** an agent that reads a restricted SCIRE record and then writes into UPMS (or the reverse) moves content the receiving system cannot trace. This is a declared gap.

### 7.3 Floors for the cross-system gap

1. **Audience-scoped generation.** An agent producing content for an audience builds its context only from sources that audience may see. This is the preferred control because it avoids taint tracking entirely.
2. **Carried constraints.** When an agent writes into one system from a context that holds restricted records from another, it declares the release constraints of that context (not the content) with the write. The receiving system enforces them as if they were its own. A write that cannot declare its constraints is treated as having unknown lineage.
3. **Unknown lineage is not clearance.** Content of unknown lineage is retained in the narrowest scope the writer may use and is not disclosed beyond it without review.
4. **Owner review across project boundaries.** Disclosure beyond a project needs review by the owners of restricted sources in the release set, not only the approval of the supervising person.

Content a person carries from outside any instrumented system remains that person's responsibility, as in ordinary confidentiality. Revocation is prospective: earlier readers are not "unseen". Routing metadata (project names, record titles) must not itself leak to unauthorized recipients.

### 7.4 When shared machinery would be justified

If ordinary research workflows routinely move restricted material across UPMS, SCIRE and SSDS, and per-system floors plus carried constraints either leak or block too much, a shared release log (one record of releases across systems) would become justified. That is the one stated reason, at present, for shared runtime machinery. The decision should rest on the derivative-trace experiment (E3, §12) and on early use.

---

## 8. Cross-System Scenarios

### 8.1 Resuming an investigation

An agent recalls from UPMS that a SCIRE question is open and a calculation is pending. It resolves the reference in SCIRE, receives the question's live positions, open objections and pending proposals, and works from that record.

### 8.2 From discussion to computation (the first cross-system use)

Researchers identify a discriminating calculation in SCIRE. An authorized participant approves an investigation request under the project's rules. SCIRE submits it to SSDS. SSDS validates it against its accepted D1–D4 and execution rules, then runs, schedules or refuses it. SSDS publishes the result or refusal; SCIRE records it as an SSDS-governed observation or decision and assesses what it means for the positions. UPMS may remember that the investigation happened and that a follow-up discussion is due.

### 8.3 Proposing a model

A SCIRE question converges on an assumption ("harmonic approximation valid below 300 K"). The team sends a model proposal to the SSDS project, with its evidence links and objection state. SSDS's D1 owner decides through its own process; it may accept, narrow ("below 250 K") or refuse. SCIRE records the decision by reference. Until then, the assumption governs only SCIRE's inquiry, and a request to run software outside SSDS's accepted regime is SSDS's to refuse.

### 8.4 An SSDS finding becomes a SCIRE question

An SSDS run shows an anomaly that its D1 does not explain. SSDS persists the finding; where SSDS designates SCIRE as the home, it becomes a SCIRE question bound to the SSDS run and D1 claim. Discussion happens in SCIRE; any resulting model change returns to SSDS as a proposal.

### 8.5 Learning from engineering failure

PEM preserves an evidence-backed lesson under its own governance. An agent later remembers the class of problem and asks PEM. PEM assesses applicability. UPMS does not declare the lesson valid in a new project.

### 8.6 Cross-project discovery

An agent recalls that project B studied a mechanism relevant to project A. If the people it is working for can see both projects, it presents the connection in A with references to B. Otherwise it sends B's owner a request to share; it does not paraphrase B's content into A.

### 8.7 Stale or unavailable source

An agent remembers an SSDS approval but cannot reach SSDS. It may report the recollection as history; it must not treat the approval as current. SCIRE, unable to reach SSDS, records the investigation as not performed and does not report a result.

### 8.8 A discrepancy and an unavailable SSDS

SCIRE has an open discrepancy question that may come from different regimes. SSDS is unavailable. SCIRE continues the inquiry, keeps the explanations live, and records the calculation as not performed. UPMS may remember the open question but must not publish a harmonized "resolved" result.

---

## 9. Multiple Agents and Teams

### 9.1 Scopes

UPMS may hold individual and team scopes. Membership in a team scope does not merge members' private records, and scientific project records remain SCIRE's regardless of who participates.

### 9.2 Attribution

Cross-system interactions distinguish: the authenticated actor invoking an operation; the person or agent who originated an assertion; the agent that interpreted or transformed it; the person authorized to approve the operation; and the system that recorded the result. A shared service account or credential never erases attribution or manufactures human authorization.

### 9.3 Independence

Independent review has dimensions: context, sources seen, model family, prompt, tools, evaluation standard and external evidence. A high-consequence review states the separation it can support, without claiming to detect out-of-band influence. An agent that repeats another's assessment adds no new observation. A reviewer given restricted evidence produces a verdict derived from it; releasing that verdict more widely is a separate disclosure decision.

---

## 10. Shared Machinery

### 10.1 No shared kernel

UPMS is organized around events and contextual records, SCIRE around questions and statements, PEM around engineering lessons and applicability. Their lifecycles differ: consolidation and salience, coexisting alternatives and append-only history, admission and maturity. A shared kernel would need many domain exceptions.

### 10.2 Shared utilities

Independently implemented identities, journals or indexes are not defects. Access scopes, revocation and release-set lineage are larger and appear in both UPMS and SCIRE, so they are the first candidates for a shared **library** once both designs have stable semantics. A shared library is not a shared runtime: each system keeps its own records and failure domain.

### 10.3 Extraction criteria

Extract a common component only when its semantics are stable across independent consumers, the total system becomes simpler, and domain changes no longer need repeated changes to the shared part. The burden of proof lies with consolidation.

---

## 11. Alternatives

| Alternative | Assessment |
| --- | --- |
| A. Complete consolidation: one kernel for persistence, identity, semantics and lifecycle | Not recommended: semantic and development coupling without demonstrated need |
| B. Independent semantics on a compulsory shared storage engine | Not an initial requirement; storage convenience should not become a dependency |
| C. Fully independent systems with ad hoc integration | Better isolation, but brittle point-to-point links and unclear authority |
| D. Independent systems, separated by responsibility, with a few named domain-native operations | **Recommended baseline** |
| E. D plus a shared release log | Held in reserve; justified only by the condition in §7.4 |

---

## 12. Adoption Sequence

1. **Independent development.** Each system continues under its own process. SCIRE prioritizes its minimal record and the falsification experiments in its own proposal.
2. **Interoperability discovery.** For each concrete cross-system use, record the owner, consumer, operation, data, authorization, failure behavior and intent (orientation, current state, history, source, proposal, finding), and which restricted sources could flow into a shared output.
3. **First operations.** Implement only the §6.2 operations needed for §8.2, through MCP servers or equivalent. Test each system standalone first.
4. **Adversarial contract tests.** Attempt to: launder restricted content through summaries; present remembered approval as current authorization; hide challenges through partial retrieval; present a SCIRE inquiry decision as an SSDS model; route a discrepancy into unauthorized SSDS execution.
5. **E3 — Derivative trace.** Trace multi-owner, partial-paraphrase, intermediate-summary, reviewer-verdict and revocation cases through the per-system floors and carried constraints. Count leaks, over-blocks and undecidable cases. The result decides whether alternative E is needed.
6. **Shared utilities.** After real deployments, inspect duplication, recurring defects and maintenance cost; extract libraries only by §10.3.

---

## 13. Requirements

**INT-01 — Separation by responsibility.** UPMS owns general contextual record and logistics; SCIRE owns scientific discussion and argument; SSDS owns decided models, implementations and governed execution.

**INT-02 — Proposal flow.** SCIRE's outputs to SSDS are proposals; SSDS decides them through its own process; SCIRE records the decisions by reference.

**INT-03 — Single canonical owner.** References, summaries and caches never create a competing authority; storage location confers none.

**INT-04 — Standalone operation.** Each system's core functions work without the other two.

**INT-05 — Domain-native, named operations.** Integration uses the receiver's declared operations; no generic mutation interface and no shared schema.

**INT-06 — Consequential dereferencing.** Consequential reliance uses the owner's current, applicable record, including the modality of scientific statements.

**INT-07 — Explicit authorization.** Retrieved memory and tool access never authorize state changes in another system.

**INT-08 — Release floors.** Read, retain and disclose are distinct; release-set lineage within each system; audience-scoped generation; carried constraints across systems; unknown lineage is not clearance; owner review across project boundaries.

**INT-09 — Honest coverage.** "Not found" is scoped; results state revision, freshness and gaps; unsupported fields are declared, never invented.

**INT-10 — History versus present.** A remembered state is distinguishable from current state; a later correction is never presented as what was known earlier.

**INT-11 — Failure isolation and recoverable exchange.** Connector failures degrade only the dependent capability; consequential operations have identifiable outcomes and receiver-defined idempotency.

**INT-12 — Agreement is not independence.** Multiple agents' agreement from shared sources is not independent evidence.

**INT-13 — Data, not instructions.** Imported memory, evidence and discussion text never carry authority to act.

**INT-14 — Evidence-driven sharing.** Shared utilities or runtime only by §10.3 and §7.4.

---

## 14. Risks

| Risk | Failure | Response |
| --- | --- | --- |
| Content in the wrong system | Scientific status asserted from UPMS context | §3.2: UPMS assessments of scientific content have no standing; bring content into SCIRE |
| Inquiry decision taken as model | Software runs under an undecided assumption | INT-02, §3.3 |
| Remembered state taken as current | Obsolete decisions acted on | INT-06, INT-10 |
| Derivative leakage across systems | Restricted content in another system's shared output | INT-08; E3 decides on a shared release log |
| Over-restriction | Collaboration blocked by blanket taint | Audience-scoped generation first |
| Interface creep | A generic envelope becomes a shared schema | Named operations only (§6.2) |
| Duplicate access machinery diverges | Inconsistent revocation and scope semantics | Shared library once stable (§10.2) |
| Partial failure | Missing or duplicated results | Identifiable outcomes, idempotency, reconciliation |
| Prompt injection through memory or documents | Retrieved text triggers actions | INT-13 |

---

## 15. Open Questions

1. **For the owner:** for scientific conclusions that never pass through SSDS (experimental or theoretical work without governed software), is an authors' publication decision recorded in SCIRE the end state, or should some other system own "decided" science there?
2. **For the UPMS developer:** does UPMS's claim and judgment model need an explicit marker that its assessments of scientific content carry no standing (§3.2), and what triggers the hand-off of such content to SCIRE?
3. **For the SSDS developer:** should SCIRE be a designated home for SSDP findings and tensions about a project's science (§6.2), and how does an SSDS model proposal enter D1 review?
4. What reset empties a production context's release set, and who validates it?
5. What is the minimum carried-constraint declaration (§7.3) that is useful without exposing private project details?
6. How does revocation in one system reach references and summaries already held in another?
7. Which operations beyond §6.2 does a real second use case need?

---

## Appendix A. Change Map from v0.2

| v0.2 | v0.3 | Basis |
| --- | --- | --- |
| Title; §2.1, §3, INT-03: UPMS as agent-centered cognitive memory | Separation by responsibility; UPMS serves an agent or a team (§0, §3.1); boundary rule for misplaced content (§3.2) | SC-A, D-A |
| §3 matrix; §7.2, §7.8: SCIRE and SSDS D1 presented as disjoint; SCIRE ratification | Proposal flow; "decided" means SSDS D1/D2; inquiry decisions only in SCIRE (§3.3, §6.2, §8.3) | SC-B, D-B |
| — | SCIRE as optional home for SSDP findings (§6.2, §8.4) | SC-B |
| §6.1, §6.4, §6.6: "conformal messaging", common envelope, semantic envelope candidate | Removed; six named operations (§6.2) | F-17 |
| §11.4: duplication acceptable | Duplication acknowledged as large; shared library path (§1.3, §10.2) | Review §5 |
| §6.7, §10.6: release checks without a floor | Per-system release-set lineage, audience-scoped generation, carried constraints, owner review (§7) | Review §3 |
| — | Shared release log as the one stated trigger for shared runtime (§7.4, alternative E) | Review §5 |
| §5.3: dereference current status | Also dereference modality (§5.3) | Review stress case 3 |
| §7.2: computation via SSDS only | SCIRE accepts other evidence with production classes (§4; companion §6.4) | F-18 |
| §8.4: seven delivery states | Condensed into §6.4 | F-16 |
| §8.6: change notifications | Deferred; on-demand resolution is the baseline | Review §7.2 |
| §8.7, INT-22: valid versus record time in exchanges | History versus present (INT-10); time semantics owned by each domain | F-12 |
| INT-01–22 | INT-01–14 (§13) | F-16 |
| Scenarios I–XVII | §8 scenarios plus adoption-stage contract tests (§12) | F-16 |
| Open questions 1–22 | 7 (§15), addressed to their deciders | F-16 |
| §19 reviewer questions | Folded into §15 | F-16 |
