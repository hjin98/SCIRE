# SCIRE: Scientific Collaborative Inquiry and Reasoning Environment

**Conceptual Scientific and Architectural Proposal**

**Version:** 0.2 — UPMS-informed conceptual revision; supersedes v0.1 as a review candidate only  
**Date:** November 2, 2026  
**Status:** PROPOSED — Unratified; pending independent concept-level review and human decisions  
**Working name:** SCIRE  
**Related document:** *Agent-Centered Memory and Domain Knowledge Interoperability — Conceptual Integration Proposal*

**Revision basis:** Preserves the v0.1 scientific model; incorporates selected, independently justified ideas observed in the public *Universal Persistent Memory Substrate* (UPMS) architecture proposals. Those UPMS proposals themselves are **not accepted authority**. Its Candidate 4.1 same-family review reported **NO-PASS**, prominently including a source-to-derivative publication leakage challenge. No UPMS machinery, numerical limits, release policy, or implementation is adopted by reference.

**Review boundary:** This document proposes scientific meanings (D1) and architectural responsibilities (D3) for separate adjudication. Its conceptual acceptance scenarios are not validation evidence; no scientific result, software implementation, or authority promotion is claimed.

---

## 0. Executive Summary

SCIRE is a proposed persistent, collaborative scientific reasoning environment for human researchers and AI agents.

Its purpose is not merely to record meetings, answer scientific questions, or manage research tasks. It is to support the development, examination, revision, and preservation of scientific understanding.

Scientific research routinely proceeds through incomplete arguments, contested assumptions, incompatible explanations, unexpected observations, and investigations that uncover entirely new questions. These processes contain substantial scientific value, including when an initial hypothesis is ultimately rejected.

Conventional conversational AI systems often fail to preserve this value. They may present coherent conclusions without exposing their justification, lose the history of revisions, conflate plausible explanations with established results, or prematurely resolve disagreements into a single narrative.

SCIRE is intended to address these limitations by treating scientific reasoning itself as a persistent, inspectable, evolving object.

The proposed system combines:

1. **Collaborative deliberation:** Multi-human and multi-agent discussion, constructive critique, facilitation, and equitable participation.
2. **Explicit argumentation:** Structured propositions, assumptions, inference applications, evidence, alternative explanations, and rebuttals.
3. **Scientific inquiry:** First-class questions, knowledge gaps, competing hypotheses, proposed investigations, and discovery opportunities.
4. **Epistemic assessment:** Evaluation of argument validity, scientific applicability, evidence adequacy, uncertainty, and conflicting interpretations.
5. **Discovery lineage:** Preservation of the historical development of ideas, including rejected hypotheses, overturned assumptions, and intermediate results that become independent discoveries.
6. **Scientific research assistance:** Literature investigation, scientific tutoring, experimental design, hypothesis comparison, and preparation of scientific publications or governed computational investigations.
7. **Durable project knowledge:** Persistent, recoverable scientific records that remain useful without dependence on a particular AI agent's conversational context or personal memory.

The principal scientific abstraction is an iterative discovery process:

**Argument → Question or Challenge → Investigation → New Evidence or Knowledge → Revised and New Arguments.**

This process is neither necessarily linear nor convergent. It may produce branching questions, incompatible hypotheses, entirely new research domains, or multiple scientifically meaningful conclusions.

SCIRE shall support these outcomes without confusing scientific exploration, evidentiary support, participant consensus, and authorized scientific decisions.

The proposed architecture shall be independently operational. It may later integrate with the Scientific Software Development System (SSDS) and a general agent-centered memory substrate through optional domain-native interfaces, but neither is required for SCIRE's core functionality.

This document establishes the conceptual scientific model, architectural responsibilities, proposed invariants, major risks, acceptance scenarios, and open design questions. It does not specify a database, agent framework, complete ontology, formal reasoning algorithm, deployment topology, or implementation workplan.

---

### v0.2 amendment map (non-normative)

This revision adds a source-faithful, two-plane scientific record with a third, explicitly derived orientation layer; tiered project and inquiry overviews; discrepancy-case investigation rather than automatic contradiction resolution; typed distinctions among logical justification, discovery, evidence-production, and authorization relationships; time- and applicability-aware state; source-derivative confidentiality and independent critique. The existing Meeting Room, hypothesis portfolios, scientific secretary, research-assistance and standalone-operation objectives remain intact.

These additions are **proposals to review**, not commitments to instantiate a fixed graph schema, always-on agent, mandatory formalizer, central clearinghouse, or specific inference algorithm.

---

## 1. Motivation and Problem Statement

### 1.1 Scientific reasoning is more than producing answers

A scientific conclusion is meaningful only in relation to the assumptions, evidence, models, and inferences that justify it.

The statement that a particular electronic interaction suppresses ferroelectricity, for example, is not equivalent to a demonstration of the mechanism.

A useful scientific argument may require a sequence such as:

- A model predicts a change in orbital energies.
- That change modifies orbital mixing.
- The modified electronic structure alters the energy associated with structural distortions.
- Competing contributions to the total energy are evaluated.
- The resulting energy landscape changes its stability.
- The mechanism is shown to apply within a specified physical regime.

Each step has its own assumptions and uncertainty. An inference that appears reasonable qualitatively may prove quantitatively inadequate.

A system that stores only the final conclusion loses the structure needed for criticism, teaching, falsification, and further discovery.

### 1.2 Incomplete justification is a scientific opportunity

Scientific discoveries frequently emerge when a researcher asks why an apparently obvious inference should be valid.

A missing premise may conceal an unrecognized physical mechanism. A previously accepted approximation may fail outside its original validity regime. A disagreement between theory and experiment may expose a measurement problem, a numerical defect, a missing model assumption, or genuinely new physics.

The inability to complete an argument is therefore not necessarily failure.

It can identify the next scientific question.

SCIRE should preserve and investigate these gaps rather than merely patch explanations into plausible narratives.

### 1.3 Scientific history matters

Scientific understanding changes over time.

A researcher may initially believe that A implies B, discover that an additional condition C is required, identify an intermediate mechanism D, then find evidence that C is inadequate and replace it with C′, producing D′ and B′.

D′ may subsequently explain other phenomena and become an independent discovery.

A final argument containing only A, C′, D′, and B′ does not preserve how D′ emerged or why earlier explanations were rejected.

SCIRE should preserve both the current best-supported argument and the historical trajectory of discovery.

### 1.4 Scientific collaboration introduces additional complexity

A research meeting may contain several scientists and several AI agents with different expertise, priorities, and judgments.

A productive system must not simply amplify the most assertive participant or the most verbose AI model.

It should preserve minority explanations, unanswered objections, scientific disagreements, and the attribution of contributions.

It must also recognize that multiple agents can share the same assumptions or training-derived biases. Agreement among agents does not by itself establish independent scientific corroboration.

### 1.5 Existing tools address only parts of this problem

Chat systems, electronic lab notebooks, citation managers, issue trackers, knowledge graphs, and workflow engines provide useful individual capabilities.

SCIRE's proposed contribution is to coordinate these activities around a persistent scientific argument-and-inquiry model.

The system should remain useful as a meeting environment, a long-term research companion, an argument-review environment, and an interface to scientific investigations.

---

## 2. Mission, Scope, and Non-Goals

### 2.1 Mission

**SCIRE shall facilitate the creation and improvement of reliable scientific understanding by preserving and actively examining the relationship among arguments, evidence, questions, alternative explanations, investigations, and historical discovery.**

### 2.2 Intended use cases

The system should support:

- Scientific brainstorming and hypothesis generation.
- Human–AI and multi-human scientific meetings.
- Detailed scientific argument construction and criticism.
- Identification of hidden assumptions and missing inferences.
- Investigation of conflicts between theory, simulation, and experiment.
- Comparison of multiple explanatory hypotheses.
- Scientific tutoring and guided derivation.
- Research literature navigation and critical synthesis.
- Selection of discriminating calculations or experiments.
- Long-running scientific projects spanning many discussions.
- Reconstruction of the intellectual history behind scientific findings.
- Preparation of research proposals, technical reports, and publications.
- Controlled handoff of approved computational investigations to external systems.

### 2.3 Explicit non-goals

SCIRE is not intended to:

- Replace human scientific judgment.
- Determine scientific truth through majority vote.
- Treat AI-generated reasoning as a proof merely because it is explicit.
- Claim that all scientific reasoning can be reduced to deductive logic.
- Require complete formalization of every conversational statement.
- Replace scientific simulation or laboratory execution systems.
- Replace SSDS's governed engineering and computation workflows.
- Become a general-purpose autobiographical memory for AI agents.
- Impose its argument ontology upon other projects.
- Require a universal memory kernel.
- Require any specific language model, graph database, or UI framework.

### 2.4 Standalone operation

SCIRE shall remain capable of conducting and preserving scientific deliberation without an installed general agent-memory substrate or SSDS connector.

External integrations are optional capabilities.

Loss of an optional connector must not invalidate locally owned scientific records or prevent core deliberation operations.

---

## 3. Fundamental Scientific Principles

### Principle P1 — Justification is distinct from assertion

Every material scientific claim should be traceable to its supporting premises, inference applications, evidence, or explicitly declared unresolved justification.

An assertion does not become established simply because it appears in a graph.

### Principle P2 — Scientific arguments are revisable

A validly recorded scientific argument may be challenged, qualified, strengthened, superseded, or rejected.

Historical revision should preserve material earlier reasoning and the causes of change.

### Principle P3 — A challenge is not a refutation

A raised objection identifies a possible problem.

Whether the objection is sound, applicable, and decisive requires separate assessment.

### Principle P4 — An unresolved question is a first-class scientific object

Questions and missing justifications may be investigated independently, linked to multiple arguments, and eventually generate new discoveries.

### Principle P5 — Competing explanations may coexist

Uncertainty does not justify choosing one explanation prematurely.

Alternatives may be mutually exclusive, partially compatible, jointly causal, or differently applicable across physical regimes.

### Principle P6 — Scientific evidence is context-dependent

The meaning and adequacy of evidence depend on observables, methods, error models, assumptions, parameters, physical regimes, and provenance.

### Principle P7 — Formal structure is not epistemic strength

An elaborate argument may be invalid. A concise observation may decisively challenge it.

Explanatory length, graph connectivity, citation count, and agent consensus must not be treated as proof.

### Principle P8 — Scientific decisions require identifiable authority

Scientific proposals, research decisions, evidentiary assessments, and accepted scientific formulations are different objects.

The ability to construct or criticize an argument does not automatically grant authorization to change accepted scientific or engineering authority.

### Principle P9 — Discovery need not converge immediately

Productive inquiry may broaden the space of questions or generate new research projects.

The system should support exploration and closure without equating progress exclusively with closure.

### Principle P10 — Historical scientific meaning must remain recoverable

Rejected arguments, invalidated assumptions, and earlier assessments remain historically useful when they explain scientific developments or affect later interpretations.

---

## 4. Core Scientific Representation

### 4.1 A structured scientific argument model

A scientific argument is proposed as a network of typed semantic objects and explicit relationships.

Its central inference form is:

`{P1, P2, ..., Pn; A1, ..., Am} --[I_k]--> C`

where:

- `Pi` are propositions serving as premises.
- `Ai` are relevant assumptions or validity conditions.
- `I_k` is an identified inference application.
- `C` is a conclusion.

The inference application is itself an inspectable object.

It should expose the warrant that connects its premises to its conclusion.

A directed graph or hypergraph is a natural conceptual representation because many scientific conclusions require several premises jointly, and one proposition can participate in many different arguments.

This does not mandate a graph database or particular serialization.

### 4.2 Candidate semantic objects

The initial conceptual vocabulary includes:

| Object | Scientific meaning |
|---|---|
| Proposition | A statement with sufficiently identified meaning and scope |
| Definition | A declaration establishing the meaning of a scientific term or object |
| Assumption | A condition taken as a premise for a bounded argument or model |
| Inference application | A particular use of a reasoning rule or scientific warrant |
| Argument | A connected justification for one or more conclusions |
| Argument context | A set of assumptions and applicable inferences defining a possible reasoning scenario |
| Hypothesis | A proposed explanatory or predictive scientific claim |
| Question | A scientific unknown requiring clarification or investigation |
| Challenge | An objection directed at a claim, premise, inference, evidence item, or applicability condition |
| Scientific discrepancy case | A scoped, durable investigation of apparent or established tensions between claims, observations, predictions, assumptions, interpretations, or regimes; may remain open or branch |
| Evidence record | A referenced observation, calculation, proof, literature result, or other evidentiary source |
| Evidence assessment | An interpretation of evidence relative to a specific claim |
| Investigation | A proposed or executed scientific procedure intended to answer a question |
| Scientific decision | An attributable authorization or adjudication within its defined scope |
| Discovery candidate | A scientific result judged potentially significant, pending appropriate verification |
| Historical revision | A record of a material change in scientific interpretation or structure |
| Deliberation source segment | An attributable original message, transcript span, or attached source, preserving what was actually recorded |
| Scientific interpretation proposal | A source-linked, attributable candidate extraction or reconstruction, potentially awaiting correction or confirmation |
| Orientation projection | A derived, time- and permission-scoped navigational view; not a new source of scientific truth or authority |

This is an illustrative, extensible vocabulary rather than a mandatory exhaustive ontology.

Objects may have multiple scientific roles; for example, a derived result may simultaneously serve as a conclusion in one argument and a premise in another.

### 4.3 Identity and scope

Material scientific objects should have stable identities.

Their meanings must remain sufficiently precise to avoid ambiguous reuse.

A proposition's scientific identity may depend on its definitions, assumptions, mathematical conventions, parameter bindings, and validity regime.

If two statements differ materially in meaning, the system should not silently merge them because their text appears similar.

Conversely, harmless rewording should not necessarily create a new scientific proposition.

The criteria for semantic identity, equivalence, refinement, split, and replacement remain open for later detailed design.

### 4.3A Semantic identity, definitions, and faithful interpretation

A meaningful scientific statement is more than a matching string. Relevant identity may include physical system, symbol definitions, dimension and units, quantified conditions, approximation, experimental protocol, parameter instance/default, and spatial or temporal regime. SCIRE should distinguish **identity**, **equivalence under stated conditions**, **refinement**, **relatedness**, and **unresolved possible matches**. It should never fuse scientific objects merely because an embedding or language model finds them similar.

Original language, equations, images, and qualifiers should retain source-level spans where permissible. A structured reconstruction should identify its source, interpreter, translation or transformation, semantic version, review state, and unresolved meaning. A corrected reconstruction may supersede a faulty interpretation without altering the historical claim that a participant uttered the original words. Conversely, transcripts are authoritative only as evidence of what was recorded, not as proof that the participant's proposition is true or scientifically well-formed.

Definitions and their prerequisites should be resolvable before a consequential dependent inference. Scientific warrants, valid deductions, empirical adequacy, and governing approval remain distinct. A semantic identity change can create a **review obligation** for affected arguments/evidence, never an automatic determination of their truth.

### 4.4 Types of inference

SCIRE should recognize that scientific reasoning includes several types of inference, potentially including:

- Deductive and mathematical reasoning.
- Numerical or computational inference.
- Statistical induction.
- Causal or mechanistic explanation.
- Abductive inference to an explanatory hypothesis.
- Analogy across systems.
- Heuristic reasoning and exploratory conjecture.

The distinction matters.

A logically valid deduction from accepted premises differs substantially from a plausible mechanistic explanation based on incomplete evidence.

The inference type should help determine appropriate validation expectations without forcing all scientific discourse into formal theorem proving.

### 4.5 Bounded argumentative completeness

A mature consequential argument should expose every materially relevant inference, assumption, evidence dependency, and unresolved gap.

However, literal recursive proof of every underlying premise is neither feasible nor necessary.

An argument may bottom out in clearly identified foundational assumptions, definitions, established external scientific results under their hypotheses, validated observations, or declared unresolved premises.

Exploratory ideas may remain incomplete.

The system should not require premature completion as a prerequisite for discussion.

Its objective is to prevent hidden critical gaps, not to discourage creative conjecture.

### 4.6 Localized challenges and dependency impact

A challenge should target the specific object or relationship at issue.

For example:

- The conclusion is not supported by the given premises.
- An imported theorem's assumptions are not satisfied.
- A numerical approximation is invalid in the current regime.
- An experimental observation is affected by a confounder.
- An intermediate inference is physically implausible.
- A claimed causal relationship is not established.

A successful challenge to one inference should trigger reassessment of dependent conclusions, not automatic global rejection.

Independent supporting arguments may survive.

Graph traversal can determine which objects require review; it cannot by itself determine whether those conclusions are scientifically false.

Circular justification should not count as independent support. Legitimate mutually dependent definitions or coupled scientific models need explicit treatment rather than accidental inference cycles.

---

### 4.7 Distinct scientific relationship families

SCIRE should expose at least four conceptual relation families where their distinction affects scientific interpretation:

1. **Justificatory relations:** premises, inference applications, warrants, direct definition prerequisites, objections, and competing routes of support.
2. **Discovery relations:** which question, failed explanation, exploratory investigation, or serendipitous observation caused a later question or idea to be pursued. Historical causation of discovery is not a validity proof.
3. **Evidentiary and production provenance:** specification, realization, dataset/instrument/simulation, source observation, transformation, assessment, and shared ancestor. This permits common-mode and selection-history assessment.
4. **Decision and authorization relations:** who proposed, examined, adjudicated, authorized, or withdrew a scientific decision in which scope and at which time.

These are **semantic distinctions**, not a requirement for four databases or disjoint graphs. A relation may be stored however practical, but a discovery path or authorization signature must not be silently substituted for a justification path. Completeness of any dependency or ancestry map is only claimable over a declared, reviewed scope; missing edges do not prove independence or absence of downstream impact.

### 4.8 First-class Scientific Discrepancy Case

A *Scientific Discrepancy Case* (SDC) records a potentially important difference that demands explanation, rather than treating every tension as a Boolean contradiction. A useful conceptual case contains: (a) the precise claims/observations and their source identities; (b) compared quantities, definitions, units and regimes; (c) relevant uncertainty and known shared dependencies; (d) whether a logical incompatibility was actually established or merely suspected; (e) competing explanations and distinct hypothesis contexts; (f) objections, missing evidence, discriminating tests and findings; (g) attributable assessment and status history; and (h) dependent conclusions requiring review.

An SDC can result in confirmed contradiction, reconciled applicability differences, revised theory, measurement error, multi-cause explanation, insufficient evidence, or a **new scientific question**. Resolution need not mean selecting one hypothesis: partially compatible or unresolved explanations may remain live, with reasoned qualifications. The lightweight alternative is a flagged discrepancy with a deferred investigation; a full case is warranted only when the consequence justifies it.

---

## 5. Inquiry, Questions, and Scientific Discovery

### 5.1 Questions as durable objects

SCIRE should represent scientific questions independently of the conversations in which they arise.

A question record may contain:

- The unresolved scientific problem.
- Its originating argument, challenge, discrepancy, or observation.
- Relevant known premises and evidence.
- Missing scientific knowledge.
- Proposed methods of investigation.
- Possible consequences of resolving the question.
- Current status and unresolved limitations.
- Related research questions.
- Attribution and historical evolution.

### 5.2 From justification gaps to research programs

A missing inference may prompt a question.

Investigating that question may reveal a previously unknown intermediate mechanism.

That mechanism may become a new proposition, support other arguments, and generate further questions.

SCIRE should preserve these relationships without reducing them to a single linear derivation.

A historical chain of research motivation is distinct from a chain of logical implication.

For example, a challenge may motivate an experiment, but the experiment's result does not logically follow from the fact that someone raised the challenge.

### 5.3 Discovery branching

Any scientifically meaningful intermediate result may become a new research subject.

A result originally introduced to justify one conclusion may acquire its own evidence, competing explanations, physical applicability regimes, and connections to other projects.

SCIRE should support this branching without treating the original investigation as the permanent parent or owner of all subsequent scientific meaning.

### 5.4 Cross-domain scientific connections

The system should support discovering possible relationships between previously disconnected arguments or research areas.

Potential methods include semantic retrieval, structural similarity, shared assumptions, common mathematical forms, and domain-specific search.

A discovered similarity should initially be treated as a candidate analogy or hypothesis.

Scientific equivalence requires analysis of mechanisms, governing equations, assumptions, and applicability.

The system must distinguish promising intellectual connections from verified scientific relationships.

---

## 6. Hypothesis Portfolios and Competing Explanations

### 6.1 Purpose

A hypothesis portfolio organizes competing or complementary explanations for an unresolved scientific problem.

It is a contextual view over scientific objects, not a separate source of truth.

Each explanatory context includes the claims, assumptions, inference structures, supporting evidence, contradictory evidence, known gaps, applicability regime, and proposed discriminating investigations relevant to that explanation.

### 6.2 Example: theory–experiment disagreement

Suppose a molecular theory predicts a result that appears inconsistent with a macroscopic experimental observation.

Possible explanations include:

1. The theoretical model or approximation is inadequate.
2. The experimental measurement or its interpretation is unreliable.
3. A previously assumed physical condition is false or incomplete.
4. The numerical implementation or convergence is inadequate.
5. The theoretical and experimental observables are not actually equivalent.
6. Multiple factors contribute to the disagreement.
7. An additional, currently unknown mechanism is operating.

SCIRE should preserve these possibilities without presupposing that they are exhaustive or mutually exclusive.

A hypothesis that revises a background assumption may overlap with one that identifies a limitation of the theoretical model.

### 6.3 Shared scientific objects, separate contexts

The portfolio should not duplicate an entire scientific graph for each hypothesis.

Relevant observations, definitions, and propositions can be shared through stable identities.

Alternative argument contexts represent the different assumptions and inference pathways under which particular conclusions follow.

The system must preserve the ability to compare contexts without conflating their premises.

### 6.4 Plausibility and confidence

The system should distinguish:

- Qualitative plausibility.
- Evidence strength.
- Inferential validity.
- Model applicability.
- Quantitative probability.
- Participant judgment.
- Scientific acceptance or authorization.

Quantitative Bayesian model comparison may be appropriate when defensible priors, likelihoods, and a properly specified hypothesis space exist.

Otherwise, qualitative or interval-based uncertainty may be more honest.

The system must not generate precise probabilities merely to provide an appearance of rigor.

If explanations overlap or multiple causes can coexist, a simple probability distribution over mutually exclusive alternatives may be inappropriate.

### 6.5 Discriminating investigation

SCIRE should help propose calculations or experiments whose potential outcomes differ across competing hypotheses.

It should consider scientific informativeness, cost, feasibility, uncertainty, and risk.

Expected information gain, Bayesian experimental design, sensitivity analysis, and related methods may be useful when their assumptions are satisfied.

However, no specific optimization algorithm is mandated at the conceptual stage.

### 6.6 Exploratory versus confirmatory evidence

An observation used to generate a hypothesis cannot automatically serve as independent confirmation of that hypothesis.

If a model assumption is adjusted specifically to explain existing experimental data, agreement with those same data is not necessarily validating evidence.

SCIRE should preserve the chronology of hypothesis generation, model selection, data use, and subsequent testing.

Where consequential, this should reveal selective reporting, repeated tuning, shared evidence dependencies, and reuse of ostensibly independent validation data.

---

### 6.7 Conflict screening is not scientific reconciliation

SCIRE should separate two operations that generic memory systems often conflate:

**Candidate conflict detection:** An explainable, bounded screening step identifies seemingly incompatible statements, predictions, evidence assessments, definitions, parameter bindings, or decision states. Deterministic checks are attractive where typed units, regimes, mutually exclusive status, or exact logical relationships permit them; semantic detection may produce uncertain candidates. A conflict flag is not a conclusion and is not itself evidence for either scientific explanation.

**Scientific explanatory reconciliation:** An investigator evaluates whether the compared claims address the same observable, theory, timescale, material regime, and uncertainty; reconstructs relevant inference and evidence ancestry; considers measurement, model, numerical and selection effects; proposes competing explanations; and identifies the observation or reasoning that would discriminate among them. This is scientific inquiry, not a data-cleaning merge, vote, last-writer-wins rule, or instruction for an LLM to generate a pleasing unified narrative.

Where assessment must be triggered by a detected flag, distinguish the **routing signal** from **evidentiary input**. A flag can open an inquiry; its existence cannot count as independent evidence that a hypothesis is true or false. Resulting scientific assessments should cite actual admissible source material, uncertainty and warrant.

## 7. Evidence, Validation, and Scientific Uncertainty

### 7.1 Distinguishing records and assessments

The existence of evidence is different from its interpretation.

SCIRE should distinguish:

1. An evidence specification: the experiment, calculation, proof obligation, or test being defined.
2. An evidence realization: the concrete execution or observation episode.
3. An observation: the result produced.
4. An assessment: the scientific interpretation of that result relative to a claim.

Later reinterpretation should not silently rewrite the historical observation.

### 7.2 Evidence provenance

Consequential scientific evidence should be traceable to sufficient information about its source.

Examples include a publication and exact result, simulation input and output artifacts, experiment and measured conditions, or mathematical proof and applicable hypotheses.

The level of detail should match the scientific consequence.

SCIRE should reference externally owned evidence rather than duplicating large source datasets unnecessarily.

### 7.3 Applicability

Evidence should be evaluated in the regime where it is used.

Relevant dimensions may include temperature, pressure, chemical composition, structural phase, model approximation, boundary conditions, numerical precision, stochastic uncertainty, and measurement configuration.

A result can be historically valid while inapplicable to a new model or scientific question.

An inability to establish applicability should remain visible as uncertainty.

### 7.4 Contradictory evidence

Contradictory evidence should not be suppressed to preserve a clean scientific narrative.

SCIRE must retain material contrary observations, unresolved disagreements, and failed investigations.

A negative result may be valuable even when it does not identify which theory or assumption is responsible.

### 7.5 Independence and common-mode uncertainty

Multiple agreeing agents do not constitute independent experimental evidence.

Similarly, simulations using the same model assumptions, datasets, numerical implementation, or validation reference may share important systematic errors.

The system should support identifying these common dependencies when they materially affect confidence.

### 7.6 Scientific adequacy versus numerical correctness

A numerically converged calculation may faithfully solve a scientifically inadequate model.

A model may reproduce an observation for compensating or accidental reasons.

SCIRE should therefore distinguish:

- Internal logical or mathematical consistency.
- Numerical and software correctness.
- Model adequacy.
- Empirical support.
- Explanatory and predictive usefulness.

The relevant human scientific authority retains responsibility for consequential acceptance.

---

### 7.7 Evidence ancestry, independence, and admissibility

For consequential claims, an evidence assessment should be able to distinguish the original observation from transformations, derived interpretations, agent-generated summaries, independent replications, reused training/validation data, and multiple outputs ultimately dependent on one source. A provenance graph describes what can be traced; it does not guarantee that all sources or influences have been observed. Claims of independent corroboration must therefore declare material ancestry/coverage limitations.

An assessment's scientific admissibility should be decided using applicable evidence and governing scientific criteria, not by bootstrapping from another assessment's favorable status. Reassessments are temporally and contextually scoped; two competent investigators' conflicting assessments may legitimately coexist pending further inquiry. Source correction, retraction, superseded validity regime, or a change in a material definition should route dependent judgments to review without retroactively falsifying the original observation.

## 8. Persistent Scientific Evolution and Discovery Lineage

### 8.1 Three distinct historical representations

SCIRE should preserve:

**A. Deliberation history:** What participants said, proposed, questioned, rejected, or agreed to, with appropriate attribution and timestamps.

**B. Structured scientific history:** How argument objects, assumptions, evidence assessments, questions, and hypothesis contexts evolved.

**C. Decision history:** What scientific decisions or authorizations were actually made, by whom, under which conditions.

These representations should be connected but not conflated.

For clarity, this triple history is **not** three competing canonical truth stores. It comprises two complementary source/semantic planes plus a decision/governance record: (i) original discussion and source artifacts; (ii) SCIRE-owned structured scientific records; and (iii) attributable governance history. **Derived overview projections** sit above these as disposable/reconstructible navigational views and are deliberately excluded from canonical scientific authority.

A structured proposition may be a tentative machine extraction, a participant-confirmed interpretation, or a separately adjudicated scientific claim; these states should be explicit. The original transcript governs historical attribution subject to correction/retention policy; the structured scientific owner governs its accepted interpretation within legitimate authority. Neither automatically proves empirical truth. Semantic corrections must be represented as attributed revisions, not silent edits to what a source said.

A meeting utterance is not automatically an accepted proposition.

A structured inference is not automatically a valid inference.

A decision to investigate a hypothesis is not a declaration that the hypothesis is true.

### 8.2 Non-destructive revision

Materially superseded reasoning should remain recoverable.

A new argument may replace, narrow, generalize, or challenge an old one without erasing the old argument's historical meaning.

The current scientific view should not automatically treat all historical objects as current support.

### 8.3 Reconstruction queries

SCIRE should eventually support questions such as:

- What did we believe about this mechanism before the latest calculation?
- Which observation first challenged the earlier explanation?
- Why was hypothesis H-017 initially considered unlikely?
- Which assumptions changed between these two argument versions?
- What independent lines of evidence now support the revised result?
- Which discovery emerged from investigating a previously missing inference?
- What unresolved disagreements were recorded when a scientific decision was made?

### 8.4 Historical recoverability versus active complexity

Complete recoverability need not imply that every historical conversational detail remains represented as an active graph node.

The system should distinguish primary records, scientifically significant structured history, and derived summaries or indexes.

Consolidation may simplify active presentation but must not erase distinctions required for scientific reconstruction.

### 8.5 Scientific novelty

The system should distinguish a discovery new to the research group from a result demonstrated to be new to the scientific literature.

A discovery candidate may trigger literature review, independent validation, and significance assessment.

SCIRE must not label a result publishably novel solely because it arose unexpectedly in a meeting.

---

### 8.6 Hierarchical scientific orientation, not hierarchical authority

Scientific continuity becomes difficult when a project contains years of meetings and interdependent arguments. SCIRE therefore proposes **tiered, source-backed orientations**:

- **L0 — Project compass:** Project objectives, currently investigated questions, major scientific decisions and their scope, prominent unresolved discrepancies, active hypothesis families, high-consequence challenges, notable changes since the last view, and navigable sources.
- **L1 — Inquiry or topic hubs:** One scientific question, mechanism, subject, hypothesis portfolio, investigation program, or discovery branch, showing competing explanations, evidence coverage, uncertainties, pending reviews and direct routes to detailed objects.
- **L2 — Scientific object views:** Actual propositions, source-bound definitions, inference/warrant chains, evidence specifications/realizations/observations/assessments, disputes, and decision records.
- **Underlying primary record:** Original meeting segments and external source artifacts, subject to access and retention controls.

The levels are **navigation and cognitive economy**, not layers of increasing scientific authority. A small minority objection or invalidating caveat cannot be omitted from an L0/L1 view merely because it is inconvenient; salient qualifications must remain visible or be explicitly signaled with a source link. Overview narratives are labeled synthesis, while deterministic current-state fields derive from current owner records at a declared read point. Views should distinguish source-revision identity, retrieval/refresh time, coverage, permitted visibility, unresolved gaps, and whether a field is historical, current, contested, or proposal-only.

No universal token budgets, mandatory L0/L1 schema, or UPMS consolidation thresholds are adopted. Budget, scope and update policy must follow actual scientific workload and information-loss tests.

### 8.7 Incremental orientation and periodic deeper reconciliation

A practical conceptual strategy is to update affected inquiry hubs and an overlay of recent changes promptly, then perform bounded, less frequent full-region reconstruction from canonical records. Summarization cannot create or change accepted scientific decisions. Rebuilding a view after source correction, revocation, definition revision, or newly discovered evidence may be necessary even when no recent meeting occurred.

For historical queries, distinguish **event/valid time** (when a claim, observation or decision was intended to hold) from **record/transaction time** (when SCIRE learned or recorded it). A later corrected reconstruction must not be reported as what the project knew at the earlier time. Exact temporal representation remains a design choice, but 'as known then' and 'as currently assessed about then' must be answerable without silent ambiguity.

### 8.8 Retrieval intent and honest coverage

Orientation, task resumption, historical reconstruction, current scientific status, and rigorous justification are different retrieval intents. A short orientation may use a non-authoritative hub; a consequential claim should drill into the relevant source, warrant, evidence and decision owners. Every answer must be permission-scoped and should disclose relevant source/index coverage, staleness and unresolved references. An absent search result is not evidence that no challenge or prior work exists unless the searched scope is genuinely complete for that assertion.

---

## 9. Multi-Human and Multi-Agent Deliberation

### 9.1 Participant model

A participant may be a human researcher or an AI agent.

Identity, expertise, contribution, meeting role, permissions, and scientific authority are separate properties.

Being designated as a facilitator or reviewer does not automatically grant authority to ratify scientific conclusions.

### 9.2 Scientific facilitator

A facilitator may coordinate speaking opportunities, identify neglected objections, request clarification, and summarize disagreement.

The facilitator should seek scientific coverage rather than enforce equal speaking time mechanically.

The objective is to ensure that materially important questions and minority explanations are not lost.

### 9.3 Preservation of dissent

SCIRE should distinguish whether a concern has been:

- Raised.
- Acknowledged.
- Answered.
- Scientifically resolved.
- Withdrawn.
- Deferred or left unresolved.

Silence, lack of attention, or majority agreement should not automatically count as resolution.

### 9.4 Agent diversity

Multiple AI agents may produce superficially independent opinions while sharing model architectures, source material, reasoning conventions, or biases.

The system should seek independent evidence, adversarial testing, complementary expertise, and different analytical methods rather than count agent votes as scientific corroboration.

### 9.5 Human scientific authority

Consequential decisions should be attributable to properly authorized participants.

Examples include acceptance of a research direction, approval of an external computational investigation, adoption of a material scientific assumption, and ratification of a scientific conclusion for governed use.

The exact governance model is project-dependent.

SCIRE should support role-based and project-specific decision rules without prescribing one universal meeting hierarchy.

### 9.6 Concurrent contributions

The system must eventually handle multiple participants updating related scientific objects.

Concurrent changes should not silently overwrite each other or resolve scientific conflicts according to arrival order.

The later design must distinguish mergeable independent edits, conflicting semantic revisions, and unresolved scientific disagreements.

---

### 9.7 Independent critique and epistemic lineage

The Meeting Room should support independent or partly blinded reasoning passes where a consequential question benefits from them. A reviewer should be able to examine primary claims/evidence without inheriting another agent's synthesized conclusion, with the scope of allowed information recorded. Where two agents share upstream sources, generated prompts, models, evaluation criteria, or a synthesis, their agreement may be correlated. A missing provenance edge cannot certify an independent trajectory.

Independent review is a methodological safeguard, not mandatory multi-agent choreography for every question. Contrary, minority, failed and negative findings are retained where scientifically significant, and reviewers should be able to challenge the system's own ontology, retrieval coverage, and formalization assumptions. A synthesizer cannot resolve a scientific dispute by majority vote or delete an unresolved rebuttal.

## 10. Scientific Secretary, Literature Navigator, and Tutor

### 10.1 Scientific secretary

The secretary function transforms deliberation into persistent, attributable records.

It should identify arguments, assumptions, questions, contradictions, decisions, and research obligations while preserving the participants' intended meaning.

### 10.2 Reconstruction is fallible

Natural-language interpretation can introduce scientific errors.

A tentative question may be incorrectly transformed into a factual assertion.

An AI may infer a missing premise that the speaker never endorsed.

An incomplete discussion may be reconstructed as a complete argument.

Therefore, an AI-generated reconstruction should retain its own attribution and source links.

For material scientific content, the system should support correction and appropriate confirmation.

### 10.3 Progressive formalization

Informal scientific discussion should remain natural.

A new hypothesis may begin as a sketch.

The system should gradually elaborate its scientific structure as scrutiny, evidence, and consequential decisions make additional rigor useful.

It should not require a formal ontology editor for ordinary conversation.

### 10.4 Literature investigation

SCIRE should help identify relevant prior work, conflicting results, missing citations, theoretical foundations, and possible novelty limitations.

External literature must be treated as scientific evidence subject to source verification and applicability, not as unquestionable authority.

### 10.5 Scientific tutoring

The system should be able to expand an inference, explain background theory, derive an equation, compare competing models, or identify prerequisites that a participant wishes to understand.

Pedagogical explanations should remain distinguishable from project-authoritative scientific claims.

---

### 10.6 Source-grounded reconstruction and correction path

The secretary should preserve a route from each material extracted object to the source segments or artifacts that motivated it, together with the actor/model performing the extraction and any human confirmation. It should distinguish (i) quotation, (ii) paraphrase, (iii) inferred missing premise, (iv) proposed formalization, and (v) independently substantiated scientific claim. Translation or reformatting of equations/units requires source-faithful handling and explicit corrections when material.

A participant may correct an extracted scientific interpretation without falsifying or deleting the historical utterance. Corrections and competing reconstructions should remain auditable, while privacy deletion and permissible retention limits take precedence over unrestricted history preservation. Neither source transcription nor structured extraction receives truth status merely by persistence.

## 11. Discovery Assistance and Research Strategy

### 11.1 Active identification of epistemic gaps

SCIRE should help detect consequential gaps in scientific arguments, including:

- Unsupported premises.
- Hidden assumptions.
- Insufficiently justified causal transitions.
- Conflicting observations.
- Unexamined approximation regimes.
- Discrepancies between prediction and measurement.
- Missing validation.
- Apparently related unresolved questions.

Absence of a recorded edge must not be interpreted as proof of scientific independence or completeness.

### 11.2 Scientific opportunity assessment

A missing inference may be valuable because its resolution has explanatory reach beyond the current problem.

Candidate factors for prioritization include:

- Expected scientific significance.
- Number and importance of dependent arguments.
- Ability to distinguish alternatives.
- Potential relevance across research areas.
- Experimental or computational tractability.
- Cost, uncertainty, and expected information value.
- Evidence of genuine novelty.

These are advisory criteria, not mechanical definitions of scientific merit.

### 11.3 Divergent and convergent inquiry

SCIRE should support both:

**Convergent research:** Evaluating evidence, narrowing alternatives, resolving challenges, and reaching justified decisions.

**Divergent research:** Opening new questions, constructing alternative explanations, exploring analogies, and identifying unexpected scientific possibilities.

A successful scientific meeting may close a problem or reveal that the original question was inadequately formulated.

Neither outcome is inherently superior.

### 11.4 Avoiding excessive intervention

The AI should not interrupt every scientific statement with exhaustive objections.

It should prioritize material weaknesses, genuine uncertainty, and useful opportunities for clarification.

Participants should be able to request deeper scrutiny on demand.

The system should make important unresolved issues accessible without overwhelming researchers with bookkeeping.

---

## 12. Human Interface and Interaction Model

### 12.1 Meeting Room as the primary interface

The SCIRE Meeting Room is the primary collaborative interface, not the entirety of the system.

Participants should be able to discuss scientific questions naturally, with supporting argument and evidence records maintained alongside the conversation.

### 12.2 Progressive disclosure

Recommended views include:

**Discussion view:** Natural conversation with concise scientific summaries.

**Argument view:** Inspectable premises, inference objects, assumptions, evidence, and objections.

**Critical view:** Weakest inferences, missing assumptions, conflicting assessments, and challenges.

**Hypothesis portfolio view:** Alternative explanations, predictions, and discriminating investigations.

**Inquiry view:** Open questions, research branches, candidate discoveries, and proposed next steps.

**Historical view:** Earlier reasoning states, revisions, and discovery lineage.

### 12.3 Interaction requirements

Participants should be able to inspect why a claim is supported, challenge a particular inference, introduce alternative hypotheses, correct attributed reasoning, request literature support, propose an investigation, and reconstruct relevant prior decisions.

These operations should not require the user to understand the underlying database structure.

### 12.4 Accessibility and cognitive economy

The system should prioritize intelligible scientific communication.

Visual graphs are useful where relationships are material, but should not become mandatory for all reasoning.

Structured text, equations, evidence tables, and conversational explanations may be more effective in different contexts.

---

### 12.5 Scientific compass and inspectable drill-down

The Meeting Room may present a concise project compass, inquiry hub, or discrepancy-case panel. A researcher should be able to move from an overview sentence such as “the current explanation is contested” to the actual competing claims, the exact measurement/calculation, the linked inference, the governing assessment, and the original discussion where authorized. A machine-written summary should explicitly show when it is a synthesis rather than current authoritative scientific status.

For consequential use, the interface should not imply completeness from an attractive graph or a polished paragraph. Stale indexes, partial source access, unpublished alternative explanations, or incompatible time scopes require clear qualifications. View design should favor the smallest accessible form that preserves material scientific meaning.

---

## 13. Conceptual Architectural Responsibilities

The following are proposed logical responsibilities, not mandatory independent services.

### 13.1 Deliberation interface

Owns user interaction, collaborative sessions, facilitator presentation, and access to structured scientific views.

### 13.2 Scientific semantic model

Owns propositions, inference applications, argument contexts, questions, hypotheses, challenges, and their domain-specific meanings.

### 13.3 Epistemic assessment

Supports evidence interpretation, applicability review, confidence assessment, contradiction analysis, and evaluation of alternative explanations.

Its output is an assessment, not automatic scientific ratification.

### 13.4 Scientific inquiry assistance

Supports gap detection, literature navigation, cross-argument connections, discriminating investigations, and research prioritization.

### 13.5 Persistent project record

Owns durable scientific objects, participant contributions, semantic revisions, historical reconstruction, and project-local continuity.

SCIRE must preserve its essential project state independently of general agent memory.

### 13.6 External integration

Provides optional domain-native interfaces for scientific computation systems, literature sources, laboratory data, and general cognitive-memory agents.

External sources do not become SCIRE-owned merely because they are referenced.

### 13.7 Scientific governance

Enforces permissions and records consequential scientific approvals, adjudications, and decisions.

The project-specific authority model remains subject to later definition.

These responsibilities may be implemented together or separately according to actual requirements.

---

### 13.8 Orientation, traceability and scientific discrepancy workflows

A **projection responsibility** provides permission-filtered, provenance-linked project/inquiry views and source drilling, without becoming a scientific authority owner. A **discrepancy workflow responsibility** screens candidate incompatibilities, opens appropriately scoped SDCs, and supports review of explanatory alternatives. A **lineage and impact responsibility** distinguishes source exposure, evidence ancestry, scientific derivation, discovery, and authorization, and produces bounded review obligations when materially affected sources or definitions change.

These are logical capabilities, not mandatory separate services, durable graph stores or background agents. Expensive semantic extraction, LLM synthesis and periodic reconstruction should be justified by observable workload and quality evidence. The minimum useful prototype may support only explicit manually linked objects and basic source-backed hubs.

---

## 14. Integration with SSDS and General Agent Memory

SCIRE shall be designed for standalone operation.

When external systems are available, they may extend its capabilities.

### 14.1 SSDS integration

SCIRE may produce a scientific investigation request, including the question, hypotheses, relevant assumptions, expected observables, proposed validation criteria, and authorized scope.

SSDS independently validates the request against its own accepted authority and execution rules.

SSDS owns the governed execution and returns appropriately identified evidence and results.

SCIRE then interprets those results within its scientific reasoning model.

**SCIRE may propose or authorize scientific intent within its legitimate scope, but it does not bypass SSDS's governing execution and acceptance processes.**

### 14.2 General agent-memory integration

An external agent may retain contextual memory of participating in SCIRE, including project objectives, recent decisions, outstanding obligations, and references to scientific records.

The agent's general memory should not become a duplicate canonical argument graph.

Consequential scientific claims and current authorization must be verified against the owning domain state.

### 14.3 Optionality

SCIRE shall not require a common memory kernel, common object ontology, shared physical database, or permanently connected external agent.

See the companion integration proposal for the complete responsibility model.

---

### 14.4 Portable references and conditional integration

When SCIRE sends investigation intent to SSDS, it sends a **request**, not a command that revises D1–D4 authority. Its scientific interpretation of returned results does not rewrite SSDS's execution/evidence records. Where general memory links to an SCIRE inquiry, the general memory remains an agent-centered navigation aid and must dereference SCIRE before asserting consequential current scientific state.

External interfaces may expose authorized overview projections, discrepancy-case inspection, question/hypothesis comparison, source-backed historical retrieval and proposal submission. They need not expose every internal semantic object; nor should a consumer infer that omitted data are nonexistent. Every boundary remains optional and denial/unavailability must not damage native SCIRE integrity.

---

## 15. Security, Trust, and Research Ownership

SCIRE may handle unpublished research, confidential datasets, and sensitive scientific disagreements.

The conceptual architecture should preserve:

- Project-specific resource visibility.
- Separate read, contribution, review, and authorization permissions.
- Human and agent attribution.
- Source trust and provenance.
- Boundaries between private participant context and shared project knowledge.
- Controlled export and citation of restricted material.
- Safe treatment of retrieved documents and tool outputs as data rather than executable instructions.
- Protection against unauthorized actions induced by prompt-injection content.

An agent's ability to read a document does not imply permission to redistribute its contents or incorporate them into unrelated general memory.

This restriction extends to **derivatives**: a paraphrase, executive summary, independently generated seeming insight, extracted proposition, or scientific overview may reveal restricted source content even when it does not quote the source. Publication/export must assess the recipient's allowed scope and material source/production ancestry, not merely the permissions of the exporting agent. In particular, an overseeing agent's approval is not a substitute for source-owner release authority.

The publicly proposed UPMS Candidate 4.1 was challenged in a same-family review for a private team record potentially reaching a broader audience through an agent-produced derivative; that candidate's review reported **NO-PASS**. SCIRE should treat this as an adversarial design case rather than assume that MCP authentication, summary redaction or visible citation links alone solve downstream disclosure. If the required lineage or release authorization cannot be established for sensitive derived content, the system should withhold or request review rather than silently publish. The exact enforcement model, permitted retention and deletion behavior remain open.

Historical retention must be reconciled with privacy, legal deletion obligations, and access-control requirements. Append-preserving scientific revision does not imply that data must be retained indefinitely against governing privacy policy.

The exact security implementation remains open.

---

## 16. Major Scientific and Architectural Risks

| Risk | Consequence | Proposed mitigation |
|---|---|---|
| Formal-looking but unsound reasoning | False confidence in conclusions | Separate inference structure from scientific warrant and evidence |
| Misinterpreted conversation | False attribution or invented premises | Source-linked reconstruction and correctable interpretation |
| Graph growth and excessive bureaucracy | Loss of usability | Progressive disclosure and proportionate structure |
| Premature elimination of alternatives | Missed scientific discoveries | Concurrent hypothesis contexts and visible unresolved disagreement |
| Confidence without statistical basis | False precision | Explicit qualitative uncertainty and defensible probabilistic models only |
| Historical evidence reused inapplicably | Invalid scientific conclusions | Regime-bound evidence assessments and review-required states |
| Confirmation bias and post-hoc fitting | Inflated evidence strength | Track exploratory/confirmatory provenance and model-selection history |
| Correlated AI agreement | Artificial consensus | Evaluate independent evidence and common-mode dependencies |
| Scientific status confused with authority | Unauthorized changes | Separate proposal, assessment, decision, and ratification |
| Cross-domain data leakage | Loss of research confidentiality | Permission-aware retrieval and controlled export |
| Incorrect automatic dependency propagation | Valid results discarded or invalid results retained | Propagate review obligations, not automatic truth values |
| Dependency on external agent memory | Loss of project continuity | Native SCIRE persistence and standalone acceptance |
| Premature universal ontology | Architectural rigidity | Small extensible domain model and deferred schema choices |

---

Additional v0.2 risks include: **narrative authority laundering** (a plausible overview treated as adjudication); **false conflict closure** (incompatible regimes incorrectly merged); **unobserved common ancestry** (agent agreement mistaken for independent replication); **derivative confidentiality leakage** (restricted sources rephrased into shared material); **temporal ambiguity** ('known then' confused with a retrospective correction); and **staleness disguised as absence** (partial indexes presented as exhaustive). Proposed countermeasures are explicitly scoped projection status, case-based explanatory review, ancestry coverage statements, recipient-sensitive derivative release checks, dual-time reconstruction, and retrieval-coverage disclosure.

---

## 17. Representative Acceptance Scenarios

These are proposed conceptual acceptance scenarios, not an executable test suite.

### Scenario A — Inspectable scientific explanation

A participant proposes a physical mechanism with a conclusion.

SCIRE can identify the material premises and intermediate inferences, reveal missing justification, and explain which claims depend on the disputed step.

It must not invent a completed proof where none exists.

### Scenario B — Localized rebuttal

A reviewer disputes one inference.

SCIRE records the objection and identifies dependent argument contexts while preserving unaffected alternative support.

The disputed conclusion becomes qualified rather than automatically false.

### Scenario C — Competing theory–experiment explanations

An observation conflicts with a model prediction.

SCIRE preserves multiple explanations, including theoretical inadequacy, experimental error, missing assumptions, numerical problems, and other possibilities.

It does not presume exclusivity or assign unsupported probabilities.

### Scenario D — Discovery from an incomplete argument

Investigating a missing premise reveals an intermediate result that applies to another scientific problem.

SCIRE preserves the original motivation, the investigation, the resulting scientific claim, and the new research branch.

### Scenario E — Historical reconstruction

A user asks why an earlier hypothesis was rejected.

SCIRE retrieves the relevant argument version, challenge, evidence, reassessment, and later replacement without representing the rejected hypothesis as current support.

### Scenario F — Multi-participant disagreement

Two researchers and several AI agents disagree over an interpretation.

SCIRE preserves attributable assessments, unresolved objections, and minority explanations.

It does not resolve scientific truth through a participant vote.

### Scenario G — Scientific secretary correction

An AI mistakenly interprets a tentative question as an accepted scientific statement.

A participant corrects the reconstruction.

SCIRE preserves the correction and appropriate provenance, and prevents the false attribution from becoming accepted current scientific knowledge.

### Scenario H — Standalone operation

SCIRE runs without SSDS or a general memory connector.

Users can resume projects, inspect arguments, revise hypotheses, and preserve scientific history.

External computation functions may be unavailable, but core scientific deliberation remains functional.

### Scenario I — Governed external investigation

A participant authorizes an investigation through an available integration.

SCIRE produces an attributable request; the external execution system enforces its own authorization and returns identified evidence.

SCIRE does not interpret successful execution as automatic scientific confirmation.

### Scenario J — Privacy and permission separation

A participant can reference a restricted dataset without granting every meeting member or AI agent access to its contents.

Queries and summaries respect the source's access restrictions.

---

### Scenario K — A false contradiction becomes a productive discrepancy case

Two reports appear to disagree about a material property. A unit conversion, temperature regime, or definition difference may explain the mismatch. The system opens a scoped candidate SDC, makes the comparison inspectable, retains competing hypotheses, and allows a documented 'not directly comparable' conclusion without deleting either historical result.

### Scenario L — Summaries do not eclipse dissent or owner status

A project compass describes a favored mechanism, but a reviewer has raised an unresolved objection. The overview exposes that caveat and links to the relevant challenged inference. If its cache is stale or its source coverage incomplete, the UI cannot claim comprehensive current status.

### Scenario M — Source-to-derivative research disclosure

An agent reads a private draft and prepares a publication-intended scientific synthesis for a broader audience. Even if the text is paraphrased and a supervisor approved the draft, release must respect the underlying source owner's permission and publication policy; absent clearance or reliable ancestry, sharing is refused or escalated.

### Scenario N — Temporal scientific reconstruction

A researcher asks what was believed before an experiment and what is now believed about that earlier evidence. SCIRE reports the contemporaneous status and the later retrospective interpretation separately, including source correction and uncertain coverage.

### Scenario O — Independent review is not consensus evidence

Three agents favor a hypothesis based on one underlying paper. SCIRE shows their shared source dependency, protects an independent minority challenge, and does not report three independent confirmations.

---

## 18. Proposed Development and Review Sequence

The following stages are conceptual and do not prescribe repositories, branches, or implementation workplans.

### Stage 1 — Scientific-semantic formulation

Review the meaning of propositions, inference applications, argument contexts, evidence, challenges, questions, and scientific decisions.

Define the minimum distinctions required for correct scientific reasoning.

Evaluate failure cases involving ambiguity, incompatible assumptions, circular reasoning, and contradictory evidence.

The concept-level review should additionally challenge whether the proposed SDC and source/semantic distinction are scientifically meaningful, whether evidence ancestry can be inspected without a universal ontology, and what would falsify the presumed benefits of hierarchical overviews. No architecture is promoted by writing this draft.

### Stage 2 — Minimal argument-and-inquiry prototype

Demonstrate argument construction, localized challenges, alternative contexts, and historical revision.

Use representative scientific examples rather than a universal ontology.

### Stage 3 — Deliberation and scientific secretary

Add natural-language meetings, multi-participant attribution, correction of reconstructed reasoning, and basic facilitation.

### Stage 4 — Evidence and hypothesis management

Introduce evidence assessments, discrepancy analysis, competing explanations, applicability checks, and proposed discriminating investigations.

### Stage 5 — Long-horizon scientific project support

Add durable project continuation, scientific discovery lineage, retrieval, and history-aware research navigation.

Introduce only validated orientation hierarchies, coverage/recency indicators, limited change overlays and bounded full-region reconstruction if prototype evidence shows that they improve cognitive economy without losing minority challenges, source qualifications or historical distinctions.

### Stage 6 — Optional external integration

Add validated, permission-checked interfaces to computational systems, literature sources, and agent memory.

Each stage should permit independent review and reconsideration of upstream scientific semantics.

---

## 19. Explicit Open Design Questions

The following are intentionally unresolved:

1. What is the minimum formal scientific ontology required without suppressing exploratory reasoning?
2. How should semantic identity and equivalence be determined when scientific statements are revised?
3. Which inference classes permit deterministic validation, and which require expert scientific assessment?
4. How should uncertainty propagate across alternative arguments without manufacturing certainty?
5. How should simultaneous, partially compatible hypothesis contexts be represented efficiently?
6. How should scientific questions be prioritized without privileging well-connected but unimportant graph structures?
7. What is the appropriate threshold for human confirmation of AI-reconstructed argumentation?
8. How should multi-agent facilitation balance independent critique, participant fairness, and cognitive economy?
9. Which parts of historical conversation require verbatim preservation, and which may be consolidated?
10. How should project permissions and confidential evidence interact with shared scientific arguments?
11. What evidence is sufficient to treat a proposed cross-domain connection as scientifically meaningful?
12. What makes a candidate discovery ready for independent validation, publication preparation, or accepted scientific use?
13. How should large scientific graphs be partitioned and queried without destroying context?
14. Which future integrations genuinely require transactional coordination, and which need only durable references?
15. Which acceptance standards should be imposed before SCIRE itself is trusted for consequential scientific work?

16. Under which conditions should an apparent contradiction become a Scientific Discrepancy Case rather than a localized challenge or a corrected semantic identity?
17. What is the correct unit of scientific 'current state' when competing argument contexts each remain justified under different assumptions?
18. Can compact L0/L1 views preserve all material dissent, caveats and missing-source indicators without becoming unwieldy?
19. How can distinct evidence, discovery, justification and authorization lineages be represented without imposing an unnecessary ontology or claiming unsupported completeness?
20. Which temporal distinctions are required to reconstruct what was believed at a time versus what is now believed about that time?
21. What is a scientifically defensible threshold for claim-level source verification and for admitting AI-created semantic reconstructions?
22. What minimum mechanisms prevent restricted evidence from leaking through derived scientific summaries, including when collaboration crosses agents and projects?
23. How should conflict investigations distinguish a routing flag from actual evidentiary support and close without circular self-justification?
24. How would a reviewer demonstrate that hierarchy, provenance or discrepancy objects add more research value than a simpler searchable notebook plus structured decisions?

These questions should guide later scientific-formulation, numerical, software-design, and implementation reviews according to the earliest affected domain.

---

## 20. Conceptual Research Foundations

The following established ideas are relevant as intellectual references, not adopted technical dependencies:

- **Toulmin's model of argumentation:** Claims, grounds, warrants, backing, qualifications, and rebuttals.
- **Argument Interchange Format (AIF):** Distinctions among information, inference, conflict, and preference structures.
- **Abstract argumentation frameworks:** Formal approaches to attacks and acceptability among arguments; acceptability is not automatically empirical truth.
- **Assumption-Based Truth Maintenance Systems:** Tracking conclusions under alternative assumption environments.
- **Bayesian inference and experimental design:** Evidence-sensitive model comparison and selection of informative investigations.
- **Scientific provenance models such as W3C PROV:** Attribution, derivation, entities, activities, and agents.
- **Research knowledge graphs and electronic lab notebooks:** Persistent scientific relationships and experimental recordkeeping.

A future literature review should evaluate these foundations critically, identify which semantics are actually useful, and avoid wholesale adoption of incompatible formalisms.

---

## 21. Proposed Foundational Requirements

Subject to independent review, SCIRE should preserve the following invariants:

**SCIRE-01 — Scientific independence.** Core operation must not depend on SSDS or a general agent-memory substrate.

**SCIRE-02 — Argument inspectability.** Consequential conclusions must permit examination of their material premises, inference applications, evidence, assumptions, and declared gaps.

**SCIRE-03 — Explicit uncertainty.** Incompleteness and disagreement must remain visible rather than be automatically resolved.

**SCIRE-04 — Alternative contexts.** Competing and partially compatible explanations must be representable concurrently.

**SCIRE-05 — Localized challenge.** Objections must be targetable to specific claims, inferences, assumptions, evidence items, or applicability conditions.

**SCIRE-06 — Historical reconstruction.** Material scientific changes and their motivations must remain recoverable.

**SCIRE-07 — Discovery lineage.** New scientific questions and discoveries must remain traceable to the investigations and reasoning that generated them.

**SCIRE-08 — Evidence separation.** Observation, assessment, scientific interpretation, and authorized decision must remain distinguishable.

**SCIRE-09 — Human authority.** Consequential scientific decisions must remain attributable to the appropriate governing authority.

**SCIRE-10 — Faithful attribution.** AI-generated reconstructions must not be presented as statements originally made or approved by human participants without adequate basis.

**SCIRE-11 — Proportionate rigor.** The system must support informal inquiry while exposing material justification gaps before consequential use.

**SCIRE-12 — Independent collaboration.** Multiple human and AI participants must be supported without treating consensus as proof.

**SCIRE-13 — Permission boundaries.** Scientific collaboration and retrieval must respect project ownership and data-access restrictions.

**SCIRE-14 — Domain-owned semantics.** External systems may exchange evidence and requests with SCIRE but do not silently redefine its scientific objects or decisions.

**SCIRE-15 — Implementation freedom.** The conceptual specification does not mandate any database, event architecture, model provider, or shared memory kernel.

---

**SCIRE-16 — Source–interpretation distinction.** Original recorded contributions, attributable structured scientific interpretations, and disposable overview projections must be distinguishable; none alone establishes empirical truth.

**SCIRE-17 — Non-authoritative orientation.** Tiered project and inquiry views must be source-linked and explicit about scope, currentness, material dissent and incomplete coverage.

**SCIRE-18 — Two-stage discrepancy treatment.** Candidate inconsistency detection must not substitute for evidence-backed scientific reconciliation; consequential discrepancies may remain open or branch into new investigations.

**SCIRE-19 — Lineage distinctions.** Justificatory, discovery, evidentiary/production and governance relationships must not be conflated; incomplete ancestry cannot certify independence.

**SCIRE-20 — Temporal and applicability fidelity.** Scientific history must distinguish contemporaneous state from retrospective interpretation, and apply evidence within its material regime.

**SCIRE-21 — Restricted derivatives.** Publication of summaries or transformed claims must respect relevant source confidentiality and authorized release, not only the publishing agent's immediate access.

**SCIRE-22 — Independent assessment.** Critique should preserve source independence where material and retain unresolved minority challenges without treating consensus as proof.

**SCIRE-23 — Bounded impact, not truth propagation.** Material source, definition or assessment changes trigger review of affected scientific reasoning within known coverage, not automatic truth-value replacement.

---

## 22. Conclusion

SCIRE is proposed as a persistent scientific inquiry environment whose fundamental concern is the evolution of scientific understanding.

Its primary object is not the transcript, the task, or the final answer.

Its primary object is the evolving relationship among scientific claims, justifications, questions, evidence, alternatives, and discoveries.

It should help scientists reason more clearly, identify missing assumptions, preserve disagreement, select informative investigations, and reconstruct the intellectual paths by which new knowledge emerges.

Its success should not be evaluated merely by how quickly it closes questions or generates plausible conclusions.

A successful system should improve the quality, inspectability, creativity, and reliability of scientific inquiry while respecting human scientific authority.

**This document is a proposed conceptual foundation. It is not accepted scientific or architectural authority and does not authorize implementation changes to other systems.**

Its next step is independent scientific-semantic and architectural critique, followed by revision of the conceptual model before detailed implementation planning.
