# SCIRE: Scientific Collaborative Inquiry and Reasoning Environment

**Conceptual Scientific and Architectural Proposal**

**Version:** 0.3 — consolidated revision after concept-level review; supersedes v0.2 as a review candidate only
**Date:** 2 November 2026
**Status:** PROPOSED — unratified; pending independent (different-family) concept review and human decisions
**Author:** Claude (AI, Opus 5.5), at the product owner's request and under the owner's decisions below
**Related document:** `Memory_and_Domain_Interoperability_Proposal_v0.3.md`

**Inputs**

| Input | Identity | Role |
| --- | --- | --- |
| SCIRE Conceptual Proposal v0.2 | SHA-256 `3e71ebb39d57f5b9716a1a414991f0d6f7a330a5e902d20590d2c8f432d985bc` | Base text |
| SCIRE Integration v0.2 Concept-Level Review | `SCIRE_Integration_v0.2_Independent_Concept_Review.md` | Findings SC-A, SC-B, F-01–F-20 |
| Product owner's decisions, 2 November 2026 | This design conversation | D-A and D-B below; delegation of the remaining findings to the author's discretion |

**Owner decisions bound by this revision**

- **D-A — Separation by responsibility.** The owner's words: "The distinction is not the number of user, or even private vs. public. It is separation of responsibility … the UPMS serves for general memory and logistics, while SCIRE stores scientific argument and discussion histories." UPMS holds an agent's or team's general contextual record; SCIRE holds scientific argument and discussion.
- **D-B — SCIRE is the proposal layer.** The owner's words: "SCIRE is the proposal layer, SSDS owns the decided model and implementations. The output of SCIRE is the input to SSDS."

**Independence.** This revision was written by the same model family that wrote the review it answers, and that review shares ancestry with the UPMS candidates. Its acceptance therefore needs a reviewer from a different model family.

**Review boundary.** This document proposes scientific meanings (D1) and architectural responsibilities (D3) for SCIRE. Its scenarios are not validation evidence. No scientific result, implementation or authority promotion is claimed.

---

## 0. Summary

Research groups lose scientific understanding in predictable ways. A hypothetical becomes a fact by retelling. An objection that nobody answered stops being mentioned and is then taken as resolved. The evidence behind a claim, and whether its sources are independent, becomes unclear. The reasons a path was abandoned are forgotten. A capable language model with search and a chat archive makes the first two failures worse: it writes fluent syntheses that resolve tension, and it cannot reliably tell a speaker's "what if" from their conclusion.

SCIRE is a persistent environment in which human researchers and AI agents discuss science, and in which the **status** of every scientific statement, the **openness** of every objection, the **basis** of every claim and the **history** of every question stay explicit and attributable.

SCIRE is the **proposal layer** of scientific work. It holds discussion, questions, competing hypotheses, objections, evidence assessments and the decisions a team takes about its inquiry. It does not hold decided scientific models or software: those belong to SSDS, which receives SCIRE's proposals as inputs and returns its governed results as evidence. General context and logistics (schedules, commitments, what happened in other work, where things are) belong to UPMS.

The primary unit is the **open question**, not the argument. A question holds its live alternatives, the observations that bear on them, the objections raised, and the decisions taken. Arguments are optional structure inside a question, added when someone needs them.

Structure is **demand-driven**: a discussion stays an attributed record with an index until someone challenges a statement, takes a decision, sends something out (to SSDS, to a wider audience, to publication) or asks for the structure.

---

## 1. Problem Statement

### 1.1 Four decay processes

| Decay | What happens | What SCIRE preserves |
| --- | --- | --- |
| Status inflation | "Suppose strain drives it" is retold as "strain drives it (Dr. X)" | The modality of every statement and who confirmed it |
| Dissent loss | An unanswered objection disappears from summaries | Every objection stays open until an attributed disposition |
| Basis loss | It becomes unclear which observations bear on a claim, under which conditions, and whether they are independent | Conditional, attributed evidence links with use-role and production class |
| Rationale loss | Rejected paths are re-explored or cited as current | Append-only history of questions, statuses and decisions |

### 1.2 Why a scientific conclusion needs its structure

A conclusion means something only together with its assumptions, evidence and inferences. "This interaction suppresses ferroelectricity" is not a demonstration of a mechanism. The demonstration may run through a predicted change in orbital energies, a change in orbital mixing, a change in the energy of a structural distortion, a balance of competing energy terms, and a stated physical regime. Each step has its own assumptions and uncertainty. A step that is qualitatively reasonable can fail quantitatively. A missing step is often the next research question rather than a defect.

### 1.3 Why scientific history matters

Understanding changes. A group may believe A implies B; find that condition C is needed; find an intermediate mechanism D; replace C by C′, giving D′ and B′. D′ may then explain other phenomena. A final record holding only A, C′, D′, B′ hides how D′ emerged and why the earlier path failed.

### 1.4 Why collaboration complicates this

A meeting holds people and agents with different expertise and assertiveness. Agents can share models, training data, prompts and retrieved sources, so their agreement may be one opinion repeated. A useful system protects minority positions and attribution, and it does not count agreement as corroboration.

---

## 2. Responsibility, Scope and Non-Goals

### 2.1 Responsibility (D-A, D-B)

| System | Responsibility | Not its responsibility |
| --- | --- | --- |
| **SCIRE** | Scientific discussion and argument: discussion records, questions, hypotheses, objections, evidence assessments, inquiry decisions, discovery history; proposals sent to SSDS | Decided models, software, governed execution; general context and logistics |
| **SSDS** | Decided scientific models (D1), numerical methods (D2), architecture (D3), implementations (D4), governed execution, realized results, PEM | Open scientific discussion; competing hypotheses before a model decision |
| **UPMS** | General contextual record and logistics for an agent or a team: what happened, commitments, schedules, where things are | Scientific argument and discussion history |

The split is by **responsibility for the content**, not by the number of users and not by private versus shared. A team discussing a mechanism is doing SCIRE work, even if one of its members is an agent whose general memory is in UPMS. An agent remembering that the team meets on Tuesdays and that a SCIRE question is waiting for a calculation is doing UPMS work.

### 2.2 The proposal layer

SCIRE's outputs to SSDS are **proposals**: an investigation request, a proposed model or assumption for SSDS's D1 owner to consider, or a challenge to an accepted SSDS model. SSDS decides through its own accepted process. SCIRE then records SSDS's decision and results by reference.

SCIRE does take decisions, but only **inquiry decisions**: what to investigate next, which hypothesis to work under for now, what to propose to SSDS, which question to close as unproductive, and what the authors will put forward for publication. None of these is a decided scientific model. An inquiry decision to "work under the harmonic approximation below 300 K" governs what the team explores in SCIRE, not what any software assumes.

### 2.3 Intended uses

- Scientific meetings among people and agents, and brainstorming.
- Building and criticizing arguments; finding hidden assumptions and missing steps.
- Investigating tension between theory, simulation and experiment.
- Comparing competing explanations and choosing discriminating calculations or experiments.
- Long-running projects across many discussions, and reconstruction of why things were believed.
- Literature navigation, tutoring and derivation.
- Preparing proposals to SSDS, reports and publication drafts.

### 2.4 Non-goals

SCIRE does not replace human scientific judgment, decide truth by vote, treat explicit AI reasoning as proof, require formalization of conversation, replace laboratory or simulation systems, hold decided models or software, serve as anyone's general memory, impose its vocabulary on other projects, or require a particular model provider, database or interface framework.

### 2.5 Standalone operation

SCIRE must work without UPMS and without SSDS. Without SSDS, investigations that need governed execution are recorded as proposed and not performed; evidence from other sources is still accepted with its production class (§6.4). Without UPMS, a researcher opens SCIRE directly and resumes from its own records.

---

## 3. Principles

**P1 — Record, interpretation and decision are different things.** What someone said or observed, what someone takes it to mean, and what an authorized person decided are distinct, attributed and dated.

**P2 — Status changes only by an attributed act.** A statement is hypothesized, asserted, challenged or withdrawn because someone did that, not because it was repeated, summarized or persisted.

**P3 — An objection is open until disposed of.** Silence, inattention or majority agreement is not resolution.

**P4 — Evidence is conditional, and comparative where alternatives exist.** An observation bears on a hypothesis under a model and conditions. Where alternatives exist, it favors one over another; it does not "support" a conclusion in isolation.

**P5 — How data were used matters.** Data used to generate, fit or select a hypothesis do not also confirm it.

**P6 — Agreement is not corroboration.** Independence is itself a claim, with stated dimensions and limits.

**P7 — Competing explanations may coexist.** Alternatives may be exclusive, compatible, jointly causal or valid in different regimes. Uncertainty does not justify choosing one.

**P8 — Formal structure is not strength.** Length, connectivity, citation count and consensus are not proof. A short observation can defeat an elaborate argument.

**P9 — Inquiry need not converge.** Opening better questions is progress. Closing is not the only success.

**P10 — Rigor follows consequence.** Structure is added when a statement is challenged, decided upon, sent out or asked about, not by default.

---

## 4. The Scientific Record

### 4.1 Planes

| Plane | Contents | What it establishes | What it does not establish |
| --- | --- | --- | --- |
| **Discussion record** | Attributed messages, transcript spans, attached artifacts and references, append-only | That something was said or attached, by whom, when | That it is true, well-formed or what the speaker meant |
| **Scientific record** | Questions, statements, objections, evidence links, inquiry decisions, each attributed and source-linked | What someone proposed, assessed or decided, and its current status | Empirical truth; decided model authority (SSDS) |
| **Derived views** | Compass, portfolios, timelines, search results, syntheses | Navigation | Anything; they are rebuilt from the two planes above |

A correction to an interpretation is a new attributed record in the scientific plane. It never edits the discussion record. A derived view is never cited as a basis for anything.

### 4.2 Record kinds

Six kinds make up the scientific record. Everything else is a status, an optional structure inside one of them, or a derived view.

| Kind | Meaning | Key fields |
| --- | --- | --- |
| **Question** | An open scientific problem: the unit of inquiry | Statement of the problem, scope, kind (ordinary or discrepancy), live positions, status, what arose from it |
| **Statement** | A proposition with a modality: hypothesis, assertion, definition, assumption, prediction or explanation | Text (and equations), **modality**, conditions and regime, attribution, confirmation state, source links |
| **Objection** | A challenge to a specific statement, inference step, evidence link or applicability condition | Target, ground, attribution, **disposition** |
| **Evidence link** | How an observation bears on one or more statements | Observation reference, relation (§6.1), conditioning model and conditions, **use-role**, **production class**, assessor |
| **Decision** | An attributed inquiry decision or a recorded external decision | Decider and authority basis, scope, effective interval, objections considered and overruled, dissent |
| **Discovery link** | Why a later question or statement was pursued | From (question, observation, failed investigation), to, attribution |

Investigations are questions' planned or completed actions. They are recorded as a decision to investigate plus the resulting evidence links, including null and inconclusive outcomes. Hypothesis portfolios are views of a question's live positions. "Discovery candidate" is a status on a statement. Revisions are versions of records, not separate objects.

### 4.3 Modality and confirmation

Every statement carries a modality: hypothesized, asserted, assumed (for an inquiry), defined, predicted, quoted or reported (from literature or another party). Modality survives every copy, summary and export.

A statement extracted by an AI from a discussion is attributed to that AI as an **interpretation** of the source span. It is attributed to a human only after that human confirms it. Only the speaker can confirm "this is what I meant". An AI is never the confirming party for a human's attribution. An unconfirmed interpretation is shown as the AI's, never as the speaker's, and never supports a decision or a proposal to SSDS.

The secretary distinguishes quotation, paraphrase, inferred missing premise, proposed formalization and independently substantiated statement.

### 4.4 Statuses and the objection rule

Statement statuses: open, challenged, supported-under-conditions, disfavored-under-conditions, withdrawn, superseded. Each change is an attributed act citing its basis.

Objection dispositions: open, acknowledged, answered (with the answer linked), withdrawn by the objector, overruled by a decision (the objection stays visible on that decision), deferred.

**Objection rule.** A question cannot be closed, and a statement cannot become the basis of a decision or a proposal to SSDS, while an objection targeting it is open without a disposition. A decision may overrule an objection. The overruled objection and its author stay visible on the decision and on every view that shows the decision.

### 4.5 Optional argument structure

When a statement is challenged or prepared for a proposal, its justification may be expanded into steps:

`{premises; assumptions or validity conditions} --[inference step]--> conclusion`

Each step can name its inference type: deductive or mathematical, numerical or computational, statistical, causal or mechanistic, abductive, analogical, heuristic. The type sets what counts as checking it. An argument may stop at foundational assumptions, definitions, imported results under their hypotheses, recorded observations, or a declared gap. A challenge targets one step. When it succeeds, it puts dependent conclusions under review; it does not falsify them, and independent routes of support survive. Circular support does not count as independent support.

This structure is used where it helps: for deductive and mechanistic chains, and where a challenge needs a precise target. It is not forced onto statistical or exploratory reasoning (§6.1).

### 4.6 Identity of records and identity of meaning

**Records** have stable identity: who said or recorded what, and when. That identity is always achievable.

**Meanings** do not. "Tc" may mean resistivity onset, resistivity midpoint or Meissner onset; "the gap" may mean a spectroscopic gap or an order parameter. Meanings split and merge as understanding changes, and equivalence can itself be disputed. SCIRE therefore treats sameness of meaning as a **claim**: an attributed, dated, contestable link of kind *identical*, *equivalent under stated conditions*, *refines* or *related*. The default for two similar statements is *unresolved possible match*. Embedding or language-model similarity can suggest a link but never creates one.

Dependency questions ("what depends on this definition?") run over records plus asserted links, and their answers state that coverage. A change of meaning creates review obligations, never automatic truth changes.

---

## 5. Inquiry

### 5.1 Questions are the unit

A question records the problem, where it came from (an argument, objection, discrepancy, observation or failed investigation), its live positions, the evidence bearing on them, open objections, proposed and completed investigations, decisions, and the questions it led to. A question may be opened from anywhere: from a gap in an argument, from an unexpected observation in routine data, from a parameter sweep, or from a failed program.

### 5.2 Discovery history is not justification

A discovery link says why something was pursued. It is never traversed as support. A challenge may motivate an experiment, but the result does not follow from the challenge. A result found while investigating one question does not belong to that question: it opens its own, linked by "arose from".

### 5.3 Discrepancy questions

A discrepancy question investigates a tension between statements, observations or predictions. Its distinguishing content is a **comparability record**, completed before any status of "contradiction" can be set:

- the quantities compared and their operational definitions (the estimand);
- units, conventions and regimes (temperature, composition, phase, model approximation, measurement configuration);
- uncertainty, and known shared dependencies between the two sides;
- whether a logical incompatibility is established or only suspected.

Kinds of tension to distinguish: formal contradiction (same estimand, same conditions, incompatible beyond uncertainty); empirical disagreement; unexpected observation (against expectation, not against a statement); different regimes; different estimands; statistical fluctuation (including look-elsewhere effects); data error; incommensurable models. A mismatch that turns out to be a units or definitions error is not a discrepancy: it is recorded as a corrected meaning link (§4.6).

**Lifecycle.**

- **Remain open** while no available observation discriminates the live explanations. Closing by fiat is an inquiry decision, recorded with its dissent.
- **Split** when the comparability record shows more than one independent tension.
- **Link** two questions that share a root-cause hypothesis or a discriminating test. Never merge them destructively.
- **Spawn** a new question when resolution needs something not about the original pair.

**Reconciliations that must not be automatic.** A weighted mean with an inflated error presupposes a shared estimand: if two methods measure operationally different quantities, the discrepancy is the scientific content. Stratifying by a third variable can remove a reversal, but if that variable is affected by both cause and outcome it creates bias, so "different regimes" is a causal hypothesis needing its own justification. A parameter introduced to make theory agree with the same data is not confirmation (P5): the question splits into "is the new distinction real?" and the original tension, which stays open.

### 5.4 Positions and plausibility

A question's live positions are its hypothesis portfolio. Shared statements and observations are referenced, not copied, so positions can be compared without conflating their premises. SCIRE distinguishes qualitative plausibility, evidential bearing, inferential validity, model applicability, quantitative probability, participant judgment and inquiry decision. Quantitative probabilities are used only when a defensible hypothesis space, priors and likelihoods exist. Overlapping or jointly causal explanations are not given a probability distribution as if exclusive.

### 5.5 Discriminating investigations

SCIRE helps propose calculations or experiments whose outcomes would differ across live positions, weighing informativeness, cost, feasibility and risk. Expected information gain and related methods may be used when their assumptions hold. No method is mandated.

### 5.6 Novelty

New to the group is different from new to the literature. A discovery candidate may prompt a literature review, independent checking and significance assessment. A discovery candidate lists the restricted sources in its production context (§9.2), because a "new insight" is often a paraphrase of a confidential source.

---

## 6. Evidence

### 6.1 Evidential relations

An evidence link connects an **observation** (a result: measured value, computed output, literature-reported result, proof) to one or more statements, under a stated conditioning model and conditions. Its relation is one of:

- **entails or refutes** (deductive, under stated hypotheses);
- **favors A over B** (comparative, under model M), the normal form where alternatives exist;
- **consistent with** (no discrimination among the live positions);
- **bears on, unassessed**.

A link names its assessor and is itself challengeable. The observation and its assessment are separate: reassessment never rewrites the observation. Where SSDS or a laboratory system distinguishes specification, realization and observation, SCIRE references those records rather than copying them.

### 6.2 Use-role

Each link records how the observation was used relative to the statement: **generated** (it suggested the hypothesis), **fitted or selected** (it fixed parameters or chose among variants), or **tested** (it was held out). Only a *tested* link can count as confirmation. Where the selection history is unknown, the link says so and the claim is limited accordingly. Repeated tuning and reuse of validation data stay visible.

### 6.3 Independence

Two lines of evidence are independent only in stated respects: data, method, instrument or code, model, analyst, model family, prompt and retrieved sources. Independence is a claim with those dimensions and a coverage statement. A missing provenance link does not establish independence. Several agents agreeing from shared inputs are reported as one opinion with those inputs. Valuable independence comes from a different evidence route or method, not from a different context window.

### 6.4 Production class

Every observation carries its production class:

| Class | Example | Standing |
| --- | --- | --- |
| SSDS-governed | A qualified SSDS run | Inherits SSDS qualification for its stated scope |
| Project-recorded | A notebook calculation or lab measurement with recorded inputs | As recorded; no SSDS qualification |
| External-reported | A literature value or collaborator's result | Subject to source verification and applicability |
| Uninstrumented | A number pasted into a meeting | Usable for inquiry; labeled; cannot support a proposal to SSDS without upgrade |

A numerically correct computation may solve an inadequate model, and a model may match data for compensating reasons. SCIRE keeps internal consistency, numerical correctness, model adequacy, empirical support and explanatory usefulness distinct.

### 6.5 Flags are routing, not evidence

A screening step (deterministic where units, regimes or exclusive statuses are typed; semantic otherwise) may flag a candidate tension. A flag may open a question. It is never cited as evidence. Two further rules prevent self-confirming loops:

- an assessment cites the observations it rests on; selection of those observations by a flag is recorded as their use-role;
- **no machine-to-machine bootstrapping**: a machine-produced assessment cannot be the sole basis of another machine-produced status change.

### 6.6 Retraction and review obligations

When a source is retracted, corrected, found inapplicable, or has a definition changed, SCIRE creates **review obligations** on dependent links and statements, reached through evidence links and asserted meaning links within stated coverage. History is not rewritten as false: the earlier assessment stays valid as made. A review obligation has an assignee and appears in the compass until disposed of.

### 6.7 Contrary and null results

Contrary observations, failed investigations and null results are kept as evidence links and question outcomes. A null result may matter even when it does not say which assumption failed.

---

## 7. History and Time

### 7.1 Three questions about the past

- **As known then.** The append-only history read as of record time *t*: what SCIRE held and what statuses were current.
- **As now assessed about then.** Current assessments of records dated before *t*.
- **When it happened in the world.** Observation time for observations; effective interval for decisions.

These need only append-only versioning, observation time and decision intervals. Scientific statements themselves are about regimes, not time intervals, and are not given a "valid time". A later correction is never reported as what was known earlier.

### 7.2 Reconstruction queries

SCIRE should answer, with drill-down to records: what did we believe about this mechanism before the last calculation; which observation first challenged the earlier explanation; why was hypothesis H rejected, and by whom; which assumptions changed between two versions; what evidence now bears on the revised result, and how independent it is; which discovery came from investigating a missing step; which objections were open or overruled when a decision was taken.

### 7.3 Deletion, restriction and tombstones

Privacy and legal obligations take precedence over unlimited retention. When a discussion record is deleted or restricted, SCIRE keeps a **tombstone**: a source attributed to a role existed and was removed on a date under a policy, without its content. Interpretations derived from it are marked "source withdrawn". They survive only if re-substantiated from other sources or re-attributed to their interpreter. A person who asks for removal is de-attributed from derived statements.

---

## 8. Deliberation and the Meeting Room

### 8.1 Participants

A participant is a person or an AI agent. Identity, expertise, role in a meeting, permissions and decision authority are separate properties. A facilitator or reviewer role does not confer decision authority.

### 8.2 Facilitation

The facilitator seeks coverage of material questions and minority positions rather than equal speaking time. It prioritizes material weaknesses and genuine uncertainty, avoids interrupting every statement, and offers deeper scrutiny on request.

### 8.3 Decision authority

Who may take which inquiry decisions, confirm statements for a group, and approve proposals to SSDS or publication is set per project. The minimum rules are fixed: only the speaker confirms their own meaning; a decision names its decider and authority basis; dissent stays on the decision. SCIRE records declared conflicts of interest; it does not score trust, reputation or intent.

### 8.4 Independent critique

For consequential questions, a reviewer may be given primary records without another participant's synthesis, with the allowed information recorded. Opposing analyses are synthesized as a **crux map**: the specific premises or observations where they diverge, and what would discriminate. Disputes are not resolved by vote or by deleting a rebuttal. Reviewers may challenge SCIRE's own vocabulary, retrieval coverage and formalization.

### 8.5 Concurrent contributions

Concurrent edits are not resolved by arrival order. Independent edits merge; conflicting revisions of meaning are kept as alternatives; scientific disagreement is represented as positions and objections, not as an edit conflict.

### 8.6 Secretary, literature navigator and tutor

The secretary turns discussion into attributed scientific records under §4.3. The literature navigator finds prior work, conflicting results and missing citations, and treats literature as reported evidence subject to verification and applicability. The tutor expands inferences, explains background and derives equations; its explanations are labeled pedagogy, not project statements.

### 8.7 Demand-driven formalization

By default a discussion is kept as an attributed record with an AI index. Scientific records are created when:

1. someone raises an objection;
2. someone takes a decision;
3. content is sent out: to SSDS, to a wider audience, to publication;
4. someone asks for a statement, question or argument to be recorded.

The secretary may suggest records at any time; the suggestions stay suggestions until one of these triggers or a participant accepts them. A project that never triggers formalization pays nothing for it.

---

## 9. Orientation and Confidentiality

### 9.1 The compass

The compass is a derived view built at read time from the scientific record by deterministic queries: open questions; live positions per question; open objections, ranked by declared consequence; recent decisions with their overruled objections; untested assumptions; stale evidence and pending review obligations; proposals waiting on SSDS. Its fields are exact as of the read. Where several incompatible positions are live, it shows all of them; there is no single "current explanation".

A narrative synthesis may accompany it on request. The synthesis is labeled as synthesis, generated for the reader's audience (§9.2), and never cited. **Persisted or incrementally maintained narrative overviews are not part of the first product.** They are introduced only if experiment E2 (§15) shows that they save reader time without losing planted minority objections, invalidated assumptions, negative studies, stale evidence or restricted-source signals.

A view that cannot show a relevant item (restricted, stale index, partial coverage) says so. "Not found" means not found in the searched scope.

### 9.2 Read, retain and disclose

Three permissions differ: **read or use** a source; **retain** content in a new scope; **disclose** content derived from it to a recipient. Reading a document does not grant disclosure of its contents or of paraphrases, summaries, extracted statements or "novel" insights derived from it. A supervisor's approval of a task does not replace the source owner's release authority.

SCIRE adopts three floors:

1. **Release-set lineage.** SCIRE records which restricted records it releases into each production context (a meeting session, an agent's working context). Everything produced in that context inherits their disclosure constraints until a validated reset.
2. **Audience-scoped generation.** Anything meant for an audience (a compass synthesis, a team summary, a publication draft) is generated in a context built only from sources that audience may see. This turns most leakage questions into access questions.
3. **Owner review across the project boundary.** Disclosure beyond the project requires review by the owners of the restricted sources in the release set. Where the release set cannot be established, the output is withheld or sent for review, not released.

Consequences: a reviewer's verdict on restricted evidence ("the claim is unsupported") is derived from that evidence. Revocation is prospective only: readers who already saw content are not "unseen". Content a participant brings from outside SCIRE's records is a declared gap and remains that participant's responsibility, as in ordinary scientific confidentiality. A cross-project connection is shown only to people with access to both projects; otherwise it is sent as a request to the other project's owner.

### 9.3 Other trust boundaries

SCIRE enforces project-level visibility and separate read, contribute, review and decide permissions. Retrieved documents, tool outputs and imported memory are data, never instructions. Prompt-injected text cannot cause actions.

---

## 10. Interfaces with SSDS and UPMS

### 10.1 SCIRE → SSDS: proposals

SCIRE sends three kinds of proposal, each attributed and approved under the project's decision rules:

- **Investigation request:** question, live positions, relevant assumptions, expected observables, what outcome would discriminate, proposed acceptance criteria, scope.
- **Model proposal:** a statement, assumption or regime proposed for adoption into an SSDS project's D1 (or, where relevant, D2) authority, with its evidence links and open-objection state.
- **Challenge:** an objection to an accepted SSDS model, with its basis.

SSDS decides each through its own accepted process. A SCIRE inquiry decision never governs SSDS software. Statements with open undisposed objections, unconfirmed interpretations and uninstrumented evidence cannot be the basis of a proposal (§4.3, §4.4, §6.4).

### 10.2 SSDS → SCIRE: decisions and results

SCIRE records SSDS's decision on each proposal by reference. SSDS results arrive as SSDS-governed observations (§6.4), referenced, not copied, and SCIRE assesses what they mean for the question's positions. Successful execution is not confirmation of a hypothesis. SCIRE never rewrites SSDS records.

### 10.3 SSDS findings and tensions

SSDP's scientific feedback loop sends material findings and tensions to an authorized writable home. SCIRE is a natural home for those about a project's science: a finding becomes a SCIRE question or objection, with its SSDS binding kept. Whether SCIRE is designated as that home is an SSDS decision.

### 10.4 UPMS ↔ SCIRE

UPMS may hold that an agent or team took part in a SCIRE project, what follow-ups are pending, and references to SCIRE records. It does not hold SCIRE's discussion or argument. Before any consequential scientific use, a consumer dereferences SCIRE. SCIRE needs nothing from UPMS to operate.

The interface contracts are owned by the companion interoperability proposal.

---

## 11. Logical Architecture

These are logical responsibilities, not services.

| Responsibility | Owns |
| --- | --- |
| Discussion record | Append-only attributed messages, spans and artifact references; tombstones |
| Scientific record | The six record kinds, statuses, dispositions, versions and meaning links |
| Assessment support | Screening, comparability records, discriminating-investigation suggestions, literature navigation; outputs are proposals or flags |
| Views | Compass, portfolios, timelines, search, audience-scoped synthesis; no authority |
| Access and release | Permissions, release-set lineage, audience scoping, disclosure review |
| External proposals | Proposal construction, sending, decision and result recording |

The minimum useful prototype supports explicitly created records, the objection rule, modality and confirmation, the compass queries and audience-scoped synthesis. Semantic screening, argument structure and background agents are added only when the experiments in §15 justify them.

### 11.1 Inspectability statement

SCIRE does not itself produce realized scientific results; it retains and projects records that mediate scientific interpretation.

- **Material realized record:** discussion records; statements with modality and confirmation; objections and dispositions; evidence links with use-role and production class; decisions with overruled objections; proposals and SSDS responses; deletions as tombstones; withheld outputs.
- **Intended readers:** project researchers, reviewers, and agents acting for them.
- **Routine questions:** those in §7.2 and the compass fields in §9.1.
- **Proposed product inspectability surfaces**, all beyond any currently accepted deliverable and binding only after the owner accepts them: the compass (§9.1), the reconstruction queries (§7.2), the source-owner manifest for disclosure review (§9.2).

---

## 12. Invariants

**SCIRE-01 — Separation of record, interpretation and decision.** Discussion records, scientific records and derived views are distinct; a correction never edits a discussion record; derived views are never a basis.

**SCIRE-02 — Explicit status.** A statement's modality and status change only by an attributed act and survive every copy and export.

**SCIRE-03 — Objection rule.** No closure, decision basis or proposal over an undisposed open objection; overruled objections stay visible.

**SCIRE-04 — Faithful attribution.** AI interpretations are attributed to the AI until the speaker confirms them; only the speaker confirms their meaning.

**SCIRE-05 — Conditional evidence.** Evidence links state their conditioning model, conditions, relation, use-role and production class; observation and assessment stay separate.

**SCIRE-06 — No counted consensus.** Agreement is not corroboration; independence is a claim with stated dimensions and coverage.

**SCIRE-07 — Flags are not evidence.** A flag may open a question but is never cited; no machine-to-machine status bootstrapping.

**SCIRE-08 — Review, not truth propagation.** Changes of source, meaning or assessment create review obligations within stated coverage, never automatic truth changes.

**SCIRE-09 — Recoverable history.** "As known then" and "as now assessed about then" are both answerable; corrections are never back-dated.

**SCIRE-10 — Proposal layer.** SCIRE decisions are inquiry decisions; decided models belong to SSDS; SCIRE's outputs to SSDS are proposals.

**SCIRE-11 — Release floors.** Release-set lineage, audience-scoped generation, and owner review across the project boundary; unknown lineage is withheld or reviewed, never released.

**SCIRE-12 — Honest coverage.** Views and answers state their scope, staleness and gaps; not found means not found in that scope.

**SCIRE-13 — Demand-driven rigor.** Formal structure is created only on the triggers of §8.7.

**SCIRE-14 — Standalone operation.** SCIRE's records and core operations do not depend on UPMS or SSDS.

---

## 13. Risks

| Risk | Consequence | Response |
| --- | --- | --- |
| Status inflation through the secretary | A hypothetical reused as fact | Modality, confirmation rule (SCIRE-02, -04) |
| Hidden dissent in summaries | Decisions on contested ground | Objection rule; compass from queries (SCIRE-03, §9.1) |
| Formal-looking but unsound arguments | False confidence | Typed inference steps; structure is not strength (P8) |
| Post-hoc fitting counted as validation | Inflated evidence | Use-role (§6.2) |
| Correlated agent agreement | Artificial consensus | Independence as a claim (§6.3) |
| False contradiction or false reconciliation | Real tension hidden, or two results wrongly merged | Comparability record; lifecycle rules (§5.3) |
| Self-confirming flag loops | Machine-made closure or controversy | SCIRE-07 |
| Derivative leakage | Confidential content in shared outputs | Release floors (SCIRE-11) |
| Over-restriction | Collaboration blocked | Audience-scoped generation instead of taint-on-touch |
| Inquiry decision mistaken for model authority | Unauthorized assumptions in software | SCIRE-10 |
| Bureaucracy | More effort formalizing than researching | SCIRE-13 |
| Premature vocabulary | Rigidity across disciplines | Six kinds; meaning links as claims |

---

## 14. Acceptance Scenarios

These are conceptual acceptance scenarios, not a test suite. Each names the expected behavior and the invariants (SCIRE-NN, §12) it exercises.

| # | Scenario | Expected behavior | Invariants |
| --- | --- | --- | --- |
| A | A participant proposes a mechanism with a conclusion | SCIRE records the statement as hypothesized; on challenge or request, it exposes premises, steps and declared gaps; it never invents a complete proof | 02, 13 |
| B | A reviewer disputes one inference step | The objection targets that step; dependents get review obligations; independent support survives; the conclusion is qualified, not falsified | 03, 08 |
| C | An observation conflicts with a prediction | A discrepancy question opens with a comparability record; theory, measurement, assumption, numerical and unknown-mechanism explanations stay live; no unsupported probabilities | 05, 07 |
| D | Two datasets differ only by temperature or a parameter definition | The comparability record shows different regimes or estimands; the result is "not directly comparable" or a corrected meaning link; neither result is deleted or declared false | 05, 08 |
| E | A compass shows a favored mechanism while an objection about doped samples is open | The open objection appears with the mechanism; a decision on the mechanism is impossible until the objection is disposed of; if overruled, it stays visible | 03, 12 |
| F | The secretary records "what if strain drives it?" as "strain drives it (Dr. X)" | The record is the AI's interpretation, hypothesized, unconfirmed; it is never shown as Dr. X's assertion; a correction is a new record; the transcript is unchanged | 02, 04 |
| G | Three agents agree, all from one review paper found by one search | SCIRE reports one opinion with its shared source, retrieval and model family, not three confirmations; a minority challenge stays visible | 06 |
| H | An investigation of H fails but reveals an unrelated anomaly | H's question records a null outcome; a new question opens from the anomaly, linked by "arose from"; the anomaly is not filed as evidence against H | 05, 09 |
| I | A cited paper's key result is retracted | Dependent links and statements, including those reached through meaning links, get assigned review obligations; earlier assessments stay valid as made | 08, 09 |
| J | A user asks why hypothesis H was rejected, and what was believed before the last experiment | SCIRE answers "as known then" and "as now assessed about then" separately, with the records, decisions and dissent | 09 |
| K | An agent drafts a public explanation from confidential evidence without quoting it | The draft inherits the release set; disclosure beyond the project needs the source owners' review; absent a release set, it is withheld | 11 |
| L | A compass synthesis is requested by a member without access to a restricted dataset | The synthesis is generated only from sources that member may see; the view says that restricted material exists and is not shown | 11, 12 |
| M | A team proposes an assumption for an SSDS model | SCIRE sends a model proposal with its evidence and objection state; SSDS decides; SCIRE records the decision by reference; the inquiry decision never governs software | 10 |
| N | SSDS and UPMS are unreachable; a researcher pastes a locally computed number | Deliberation continues; the number is an uninstrumented observation; the SSDS investigation is recorded as not performed | 05, 14 |
| O | A two-person project discusses informally for a month | No structure is created beyond the record and index unless an objection, decision, export or request occurs | 13 |

---

## 15. Development Sequence

Each stage permits review and reconsideration of earlier stages.

**Stage 0 — Falsification experiments, before building.** All use existing material and no new infrastructure.

- **E1 — Status inflation and attribution.** On three or more real project histories with a human-annotated gold set, compare a capable LLM with search over the archive against the same LLM plus the minimal record (modalities, objections, decisions). Measure hypotheticals reported as assertions, misattributions, and recall of open objections and null results. *If the minimal record does not do materially better, the product premise is falsified.*
- **E2 — Overview loss.** Plant a minority objection, an invalidated assumption, a negative study, stale evidence and a restricted source. Compare the query-built compass with synthesis against a persisted narrative overview after N updates. Measure recall of planted items and leakage to a lower-access reader.
- **E3 — Derivative trace.** Trace the adversarial set (multiple owners, partial paraphrase, intermediate summary, reviewer verdict, revocation) through the release floors on paper; count leaks, over-blocks and undecidable cases.
- **E4 — Elicitation cost.** Run the secretary under demand-driven triggers on recorded meetings; measure corrections per hour and acceptance.

**Stage 1 — Minimal record.** Discussion record, the six kinds, modality and confirmation, the objection rule, compass queries, audience-scoped synthesis.

**Stage 2 — Evidence.** Evidence links with relation, use-role and production class; discrepancy questions with comparability records; review obligations.

**Stage 3 — Deliberation.** Meeting Room, facilitator, secretary, independent critique, crux maps.

**Stage 4 — Optional structure.** Argument steps, screening, meaning-link suggestions — each only where Stage 1–3 use shows the need.

**Stage 5 — Interfaces.** SSDS proposals and results; UPMS references; SSDP finding home if SSDS designates it.

---

## 16. Open Questions

1. Which disciplines need statement kinds beyond the six, and can they be expressed as modalities or optional structure?
2. What minimum comparability record is enough across experimental, computational and theoretical work?
3. How should uncertainty be shown across positions without manufacturing a single number?
4. Which inference types admit deterministic checking, and which need expert assessment?
5. What reset makes a production context's release set empty again, and who validates it?
6. What compass fields do researchers actually use (to be learned from E1, E2 and Stage 1 use)?
7. Which discussion content needs verbatim retention, and for how long, under each project's policy?
8. What evidence should be required before SCIRE is trusted for consequential work (thresholds for E1–E4)?
9. For conclusions that never go to SSDS (experimental or theoretical work without governed software), is an authors' publication decision in SCIRE the end state, or is another owner expected? See the owner question in the companion proposal.

---

## 17. Intellectual Foundations

Relevant as references, not dependencies: Toulmin's argument model (claims, grounds, warrants, qualifiers, rebuttals); the Argument Interchange Format; abstract argumentation frameworks, whose acceptability is not empirical truth; assumption-based truth maintenance, for reasoning under alternative assumption sets; likelihoodist and Bayesian accounts of comparative evidence and experimental design; causal graphical models, for when stratification is and is not justified; W3C PROV for attribution and derivation; electronic lab notebooks and research knowledge graphs. A later review should select what is useful and avoid adopting incompatible formalisms wholesale.

---

## Appendix A. Change Map from v0.2

| v0.2 | v0.3 | Basis |
| --- | --- | --- |
| §0, §4.1, §22: argument as primitive; loop Argument → Question → Investigation → Evidence → Argument | Question as unit (§5.1); argument structure optional (§4.5); inquiry entered from anywhere | F-03 |
| §4.2: 19 object types | Six record kinds (§4.2); others become statuses, views or versions | F-06 |
| §4.3, §4.3A: stable identities | Record identity versus meaning links as claims (§4.6) | F-05 |
| §4.6, §7: premise → conclusion support | Conditional, comparative relations (§6.1) | F-04 |
| §4.7: four relation families | Kept as semantics; use-role added (§6.2) | F-10 |
| §4.8: Scientific Discrepancy Case type | Discrepancy question with comparability record and lifecycle (§5.3) | F-07 |
| §6.7: flag ≠ evidence | Kept; no machine-to-machine bootstrapping added (§6.5) | F-08 |
| §9.3: dissent states | Objection rule (§4.4) | F-09 |
| §8.7: valid/transaction time | Append-only history, observation time, decision interval (§7.1) | F-12 |
| §8.6–§8.8, §12.5: L0/L1/L2 orientation | Query-built compass; persisted narrative overviews deferred to E2 (§9.1) | F-13 |
| §10.2, §10.6, OQ7: confirmation threshold open | Confirmation rule (§4.3) | F-14 |
| §10.3, §11.4: progressive formalization | Demand-driven triggers (§8.7) | F-15 |
| §14.1: computation through SSDS | Production classes (§6.4) | F-18 |
| §15, §8.4: retention open | Tombstones (§7.3); release floors (§9.2) | F-19, review §3 |
| §3 P8, §9.5: SCIRE ratifies conclusions for governed use | Proposal layer; inquiry decisions only (§2.2, §10.1) | SC-B, D-B |
| §2.3, §13: SCIRE versus "general agent memory" | Separation by responsibility (§2.1) | SC-A, D-A |
| SCIRE-01–23 | SCIRE-01–14 (§12) | F-16 |
| Open questions 1–24 | 9 (§16); the rest are answered above or moved to experiments | F-16 |
| Scenarios A–O | Consolidated into scenarios A–O of §14, covering the review's ten stress cases and mapped to invariants; Stage 0 experiments added (§15) | F-16, review §6 |
