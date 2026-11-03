# SCIRE Integration v0.2 — Concept-Level Review

2 November 2026 · requested by the product owner · reviewer: Claude (AI, Opus 5.5)

**Status:** reviewer assessment. This is not acceptance, ratification, a scientific gate or an implementation mandate. Neither proposal is promoted by it.

**Governing method:** SSDP 7.2.1 skills (scientific formulation for D1, software design for D3). The hand-off assigns no `protocol_version`.

## Objects under review

| File | SHA-256 | Role |
| --- | --- | --- |
| `SCIRE_Conceptual_Proposal_v0.2.md` | `3e71ebb39d57f5b9716a1a414991f0d6f7a330a5e902d20590d2c8f432d985bc` | Principal target 1 (read in full) |
| `Agent_Centered_Memory_and_Domain_Interoperability_Proposal_v0.2.md` | `634d4e8aeeb208e6d25e7136e196c098b0c6bfc79216934e0e92a3ae13f31c5e` | Principal target 2 (read in full) |
| `SCIRE_Integration_v0.2_Independent_Concept_Review_Handoff.md` | `9672bba7eafd84d8eb969bf48072e635af49cccadc1bbc1a36b1da0e6bce1dc2` | Reviewer instruction |
| `SCIRE_Conceptual_Proposal_v0.1.md` | `bd84fea48d7ce523a0528963278ad6d8221e9e87da9c6ef1ac5f0758ef56e960` | Predecessor; compared by structure and removed lines only |
| `Agent_Centered_Memory_and_Domain_Interoperability_Proposal_v0.1.md` | `eb9b17ac686d60becc7a3aafc30aa79179152077729fe1708a38546988755c37` | Predecessor; compared by structure only |

Source context I examined, which is not binding authority:

- UPMS `UPMS_Architecture_Manual_Review_Candidate_4_1.md` (SHA-256 `19a9e3ed…57df`), §1.2, §1.4, §5.2, §5.3 and §10.6.2, at local `hjin98/universal-persistent-memory-substrate` commit `22a7a49`.
- UPMS `UPMS_Candidate_4_Same_Family_Review.md` (SHA-256 `71f424c6…970c`), §1 and finding N-01 (SC-1).
- SSDS: `PROJECT-ENGINEERING-MEMORY.md` front matter and summary, the head of the SSDP 7.0 scientific-epistemic-closure workplan, and the SSDP 7.2.1 owner *Scientific Inspectability and Epistemic Initiative*: its terminology and its persistence and tension rules.

The drafts match the names the hand-off gives. v0.2 of each proposal adds to v0.1: only three lines of SCIRE v0.1 were removed (the version and status lines, and the v0.1 `Discrepancy` vocabulary row, which the Scientific Discrepancy Case replaces).

## Independence disclosure

This review is **not independent in the sense the hand-off asks for**, for three reasons:

1. **Authorship unknown.** The two proposals do not name their author or model family. If either was drafted with a Claude model, this is a same-family review.
2. **Shared ancestry with UPMS.** The UPMS Candidate 4.1 and its NO-PASS review were written by the same model family as this reviewer. Where this review borrows the N-01 repair (release-set propagation) or judges UPMS-derived ideas, it shares upstream reasoning with them.
3. **Common source.** Both this review and the proposals draw on the same UPMS documents.

No subagents or tools other than file reading were used. No realized scientific results, implementations or gate evidence exist or were examined. Every scenario, counterexample and test below is a thought experiment. The real-world scientific cases (§6.2) are cited from general knowledge as illustrations. Their numbers are approximate and were not checked against primary sources for this review.

---

## 1. Executive verdict

**SUBSTANTIAL REDESIGN, with two Serious Challenges to the three-system boundary.**

The proposals identify a real problem and many of the right failure modes: status inflation, hidden dissent, pseudo-independent agreement, laundering through summaries, and false contradiction. Most of the *negative* principles are sound and should be kept ("a flag is not evidence", "not found is not none", "agreement is not corroboration", "a summary is not a decision").

The *positive* architecture does not yet earn its machinery:

- **SCIRE v0.2 names the wrong primitive.** It names the argument as primitive, while its own operating unit (inquiry hubs, questions, discrepancy cases, portfolios) is the open question with its live alternatives.
- **It grew by addition.** v0.2 added 20 sections, 8 invariants, 9 open questions and 3 object types to v0.1, and consolidated none.
- **Half of it is a second UPMS.** It imports most of UPMS's mechanisms (tiered overviews, event versus claim versus judgment, discrepancy screening, ancestry, release checks) while denying any shared substrate. The integration proposal calls this "acceptable duplication". It is not small: these are the mechanisms on which UPMS failed review.
- **The boundary rests on a characterization the other systems do not share.** The integration proposal places UPMS on the "agent-centered" side and SSDS on the "engineering" side. The UPMS candidate describes itself as team project memory with epistemic judgments. SSDS's D1 layer and SSDP 7's feedback loop are scientific authority and scientific-finding persistence. With both mismatches, the "single canonical owner" principle (INT-06) cannot be applied as written.

The separation of **memory, agency and authority** (integration §2.3) and the rule **"dereference the owner before consequential reliance"** should survive any redesign. The recommended path is:

1. Settle the two boundary decisions (§8, decisions D-A and D-B).
2. Reduce SCIRE to a small inquiry record with demand-driven formalization.
3. Run three cheap falsification experiments (§10) before building any graph, ontology, overview hierarchy or multi-agent choreography.

---

## 2. Reconstructed first principles

### 2.1 The problem in my own model

A research group's scientific understanding is spread across people, conversations, notebooks, data and, increasingly, AI context windows. Over months, four things decay predictably:

1. **Status.** A hypothetical turns into an assumption, then into a fact, through repeated retelling (by humans and, faster, by LLM summarization).
2. **Open objections.** Dissent that was never answered stops being mentioned. Absence of mention is then read as resolution.
3. **Evidence basis.** It becomes unclear which observations actually bear on a claim, under which conditions, and whether they are independent or reused.
4. **Why.** Rejected paths and the reasons for rejection are lost, so they get re-explored or wrongly cited.

A capable LLM with search and a chat archive makes items 1 and 2 **worse**. It produces fluent syntheses that resolve tension, and it cannot tell a transcript's hypothetical from its conclusion without context. That is the defensible core of SCIRE's value proposition.

### 2.2 Non-negotiable invariants (my reconstruction)

| ID | Invariant | Why it is non-negotiable |
| --- | --- | --- |
| R1 | **Record ≠ interpretation ≠ decision.** What was said or observed, what someone takes it to mean, and what an authorized party decided are distinct, attributed and dated | Every failure in §2.1 is a collapse of one of these |
| R2 | **Status is explicit and changes only by an attributed act** (hypothesized / asserted / challenged / supported-under-conditions / decided-for-use / withdrawn) | Prevents status inflation by retelling |
| R3 | **An open objection stays open until an attributed disposition** (answered, withdrawn, overruled by a decision that keeps the dissent) | Prevents dissent loss by silence |
| R4 | **Evidential relations are conditional and contrastive**: an observation favors H₁ over H₂ under model M and conditions K; it does not "support C" absolutely | Fidelity to statistical and model-dependent inference (§3, F-04) |
| R5 | **Use-role of data is recorded**: used to generate, fit or select versus used to test | Exploratory evidence is not confirmatory |
| R6 | **Count of agreeing agents is never evidence**; independence is itself a claim with declared coverage | Pseudo-consensus |
| R7 | **Derivatives inherit the release constraints of what was observed to enter their production**; unknown lineage is a gap, never a clearance | Confidentiality |
| R8 | **Absence in a search is bounded by the searched scope** | False absence |

### 2.3 Questionable design preferences presented as invariants

- **SCIRE-01, standalone operation without UPMS.** This is a deployment preference. The underlying need is that scientific records must not be lost, reweighted or consolidated by a memory system's salience policy, and that authority must not live in memory. A shared source store could meet that need (§5).
- **"Material scientific objects should have stable identities" (SCIRE §4.3).** Achievable for *records*; not achievable for *meanings* (F-05).
- **The argument hypergraph `{P; A} --[I]--> C` as the central form (§4.1).** Useful for some deductive or mechanistic chains; wrong as the universal form (F-04).
- **Bitemporal valid/transaction time (§8.7).** A business-data idiom that fits decisions and observations, not scientific propositions (F-12).
- **Tiered L0/L1/L2 overviews (§8.6).** A UPMS mechanism adopted with a disclaimer but no evidence that it is needed in SCIRE (F-13).

---

## 3. Serious Challenges

### SC-A — The boundary premise mischaracterizes UPMS (demonstrated textual conflict between two unratified candidates)

**Claim under test.** Integration §2.1, §3 and INT-03: UPMS is "agent-centered cognitive memory" whose distinguishing role is an agent's experiential continuity. SCIRE and SSDS are "domain-centered project knowledge".

**Counter-evidence.** UPMS Candidate 4.1 §1.2 defines UPMS as "a model-independent memory service for continuing project work by people and agents". Its first journeys include "multi-user and multi-agent access under scope permissions" and "team coordination through shared memory, including blind and independent work". Its §5.2 `Claim` carries modalities (asserted, hypothesized, …). Its §5.3 `Judgment` carries `epistemic_status: supported | refuted | contested | unknown`, supporting and opposing references, and a ruleset defining "correlated-source treatment". Its §10.6.2 publishes items into team scopes.

**Consequence.** A research team that uses UPMS team scopes for project work, which is UPMS's stated first journey, produces UPMS Judgments that mark scientific claims "supported" or "refuted". The same team using SCIRE produces SCIRE evidence assessments about the same claims. Then:

- There are two epistemic-assessment owners over one subject matter.
- INT-06 ("one canonical owner") cannot be applied, because the integration proposal assigns the territory by a criterion ("agent versus project") that UPMS does not satisfy.
- UPMS §1.4 itself says that D1 authority is required first if UPMS "becomes the retention home for realized scientific records". The integration proposal neither notices nor resolves this trigger.

**Earliest owner.** Interoperability and governance (cross-system D3), with a product decision on what UPMS is (decision D-A).

**Replacement principle.** Draw the boundary by **semantic commitment**, not by "agent versus project":

> UPMS may record *who said what, when, under which access and release constraints*, and may hold assessments that are explicitly non-authoritative for any domain that has an owner. A scientific assessment that carries project standing is made only in SCIRE.

UPMS's own §1.4 ("records attributed statements … certifies none of them") already states half of this. Under it, a UPMS `Judgment` over a scientific claim in a SCIRE-governed project is a recollection or a pointer, never a status.

**Local or foundational?** Foundational for the integration proposal: §2, §3, §11 and INT-03 need rewriting. Local for SCIRE.

### SC-B — Two scientific authorities: SCIRE "ratification" versus SSDS D1 (demonstrated ownership gap)

**Claim under test.** Integration §3 assigns "scientific propositions, arguments" to SCIRE and "SSDS accepted D1–D4" to SSDS, as if they were disjoint. SCIRE P8 and §9.5 have SCIRE record "accepted scientific formulations", "adoption of a material scientific assumption" and "ratification of a scientific conclusion for governed use".

**Counter-evidence.** SSDS D1 *is* accepted scientific meaning: observables, models, assumptions and validity regimes, owned by a Scientific Method Paper. SSDP 7 also already runs a **scientific feedback loop**: question → D1–D4 → execution → realized record → bounded search for anomaly or tension → human judgment → persisted next question or Challenge. Its persistence rule sends material findings to "one existing authorized writable home". Neither proposal mentions this loop, although it is the closest existing analogue of SCIRE's discovery loop and the most natural integration point.

**Counterexample.** A SCIRE meeting decides "adopt the harmonic approximation; valid below 300 K". The SSDS project's accepted D1 paper says it is valid below 250 K. An agent asks for an SSDS run at 280 K, citing the SCIRE decision.

- SCIRE §14.1 says SSDS "independently validates", so SSDS refuses or runs under its own D1. That part is correct.
- But nothing says whether the SCIRE decision is (a) a proposed D1 amendment to route to the D1 owner, (b) a scope-limited inquiry decision that never governs software, or (c) a competing current authority.
- An L0 compass will show "harmonic approximation adopted (≤300 K)" as a major scientific decision.

**Consequence.** Authority confusion at exactly the point where SCIRE claims to add value: moving from deliberation to governed computation.

**Earliest owner.** Interoperability and governance, with D1 semantics of "decision" in SCIRE.

**Replacement principle.**

> For any use governed by SSDS, the SSDS D1 owner is the sole authority. A SCIRE decision is an attributed *input* to that owner (a proposed D1 amendment or a Challenge) and records the D1 acceptance by reference.

SCIRE decisions otherwise govern only inquiry actions: what to investigate, what to treat as a working assumption within SCIRE, and what to prepare for publication. Separately, SCIRE should be offered as a candidate **authorized writable home for SSDP findings and tensions** about a project's science. That is a concrete, low-coupling integration with real value, and it is absent from both drafts.

**Local or foundational?** Local to the integration proposal (§3 matrix, §7.2, §7.8) and SCIRE §3 P8, §9.5 and §14.1. It does not reopen SCIRE's premise.

### High-priority risk (not a demonstrated defect): derivative confidentiality has no conservative floor

Both proposals say the right things: read ≠ retain ≠ disclose (integration §10.6), and withhold when lineage is unknown (SCIRE §15). Enforcement is explicitly deferred, so there is no contradiction to demonstrate. But SCIRE's central workers are an LLM secretary and an LLM synthesizer that read *everything visible in a project session*. Without a stated lineage unit, the withhold-when-unknown rule leaves two outcomes:

- **Over-restriction.** Every synthesis is "unknown lineage", so nothing produced by an agent can be shared beyond its most-privileged reader. L0/L1 views become per-person artifacts, and collaborative orientation dies.
- **Under-protection.** Implementations quietly treat "unknown" as "clean". This is UPMS N-01 again: the system knows what it released to the session, but records nothing.

**Required floor (proposed).**

1. **Session release-set lineage.** SCIRE records which restricted records it released into each production context. Every output of that context inherits their constraints until a validated reset. This is UPMS N-01's repair, adopted on its merits and not by reference.
2. **Audience-scoped generation as the preferred path.** Any derivative meant for audience X (an L0 view, a team summary, a publication draft) is produced in a context built only from sources X may see. This turns most leakage questions into access questions.
3. **Owner review on crossing the project boundary.** Publication beyond the project is gated by review from the source owners named in the release set.

Content an agent or human carries in from outside the instrumented system remains a declared gap and a human responsibility, as in ordinary scientific confidentiality. Details and adversarial cases are in §6, case 7.

---

## 4. Conceptual findings

Ordered by consequence. "S" means the SCIRE proposal and "I" means the integration proposal.

| ID | Where | Claim or assumption under test | Counterexample or reasoning | Consequence | Recommended disposition | Confidence |
| --- | --- | --- | --- | --- | --- | --- |
| F-01 | I §2.1, §3, INT-03 | UPMS is agent-centered | SC-A | Two assessment owners | Boundary by semantic commitment; decision D-A | High (textual) |
| F-02 | I §3; S P8, §9.5, §14.1 | SCIRE decisions and SSDS D1 are disjoint | SC-B | Competing scientific authority for governed use | SCIRE decision = input to D1 owner; SCIRE as SSDP finding home | High |
| F-03 | S §0, §4.1, §22 | The argument is the primitive; loop Argument → Question → Investigation → Evidence → Argument | Instrument-led discovery (an anomaly in a routine scan) starts with an observation and no argument. Model exploration starts with a parameter sweep. A failed program ends with a question, not an argument. SCIRE's own operating units (L1 hubs, SDCs, portfolios, §5.1 questions) are inquiry-centered | Bias toward formalized, publishable reasoning; elicitation of arguments that don't exist | Make the **open question (inquiry)** primary: it holds live alternatives, observations, objections and decisions. Arguments are optional structured content inside it. The loop is a graph of question ↔ observation ↔ position, entered anywhere | High |
| F-04 | S §4.1, §4.6, §7 | Support is premise → conclusion | Statistical evidence is contrastive: a datum with likelihood ratio 3 favors H₁ over H₂ yet may be improbable under both, and adding an H₃ changes what it "supports". Model-dependent inference is conditional on M, and many inferences share M (common mode) | "Supported" edges overstate and cannot represent "favors H₁ over H₂ under M" | Evidential links are **contrastive and conditional** (R4). Keep the hypergraph form for deductive or mechanistic chains only. Make model or assumption context explicit conditioning, not a free-floating "argument context" | High |
| F-05 | S §4.3, §4.3A | Material scientific objects can have stable identities | "Tc" by resistivity onset, midpoint or Meissner onset; "the gap" as spectroscopic gap or order parameter. Meanings split and merge as understanding changes; equivalence is itself contested | Either false merges or a growing pile of near-duplicates; dependency analysis over wrong identities | **Record identity is stable** (who said what, when). **Semantic identity is a claim**: equivalence or refinement links are attributed, dated, contestable assertions with conditions. Default is "unresolved possible match". Dependency analysis runs over asserted links with declared coverage | High |
| F-06 | S §4.2 | A 19-type vocabulary is "illustrative" | Duplications: Argument / Argument context / Hypothesis portfolio / Hypothesis; Evidence record (table) versus specification / realization / observation / assessment (§7.1); Historical revision as an object versus versioning; Discovery candidate versus a status on a proposition. *Warrant* is referenced everywhere but is not a type | Unstable ontology; high elicitation cost; reviewers cannot tell which distinctions are binding | Core of about six: **source record, statement (with modality and conditions), question, objection, observation-use link, decision**. Everything else is a status, a view or optional structure. Keep specification / realization / observation / assessment only where SSDS or a lab system supplies it | Medium-high |
| F-07 | S §4.8, §6.7; I §7.8 | The SDC is a first-class type | Its unique value is the **comparability analysis**: same estimand, definition, units, regime, conditioning? A challenge lacks this. Everything else in an SDC (alternatives, tests, status history, dependents) is already a question with a portfolio | A parallel object type with its own lifecycle; risk of bureaucracy for trivial mismatches | Demote the SDC to a **question kind "discrepancy"** with a mandatory comparability record before any "contradiction" status. Lifecycle rules in §6.2 | Medium-high |
| F-08 | S §6.7, §7.7 | Separating routing flags from evidence prevents self-confirmation | A workflow can still bootstrap: flag → LLM assessment A₁ citing source records but *selected* by the flag → flag on A₁'s consequences → A₂ cites A₁. Each step is formally admissible | Machine-generated closure or machine-generated controversy | Add: **no machine-to-machine status bootstrapping**. A machine assessment cannot be the sole basis of another machine assessment's status change, and selection by flag is recorded as use-role (R5) | Medium |
| F-09 | S §9.3, §6.7 | Dissent states listed (raised … deferred) preserve dissent | Closure of a case or decision does not *require* disposition of every open objection, and L0 can show a decision without its open objections | Hidden dissent (scenario 2) | **R3 as a structural invariant**: an item cannot reach "decided" or "resolved" while an objection targeting it is open without an attributed disposition. A decision may *overrule*, and the overruled objection stays visible on the decision | High |
| F-10 | S §4.7 | Four relation families suffice | Missing: **use-role** of data relative to a hypothesis (generate, fit, select versus test). It is neither pure production provenance nor justification, and it decides whether agreement is confirmatory | Post-hoc fitting counted as validation | Add use-role on observation-to-hypothesis links. Keep the four families as semantics, not storage | High |
| F-11 | S §9.7, §7.5; I §9.5 | Independence can be assessed from ancestry | Agents in separate contexts share model family, retrieval engine and top-k results, prompt templates and evaluation rubric. A human reviewer read the AI synthesis first. None of this is a recorded edge | Pseudo-independent corroboration | Independence is a **claim with declared dimensions** (context, sources, model family, method, data). Valuable independence is a **different evidence route or method**, not a different context window. Report agent agreement as one opinion with its shared inputs | High |
| F-12 | S §8.7; I §8.7, INT-22 | Event/valid time versus record/transaction time for scientific claims | Scientific propositions are about regimes, not time intervals; "when a claim was intended to hold" is ill-defined for "X suppresses ferroelectricity". Needed: (a) append-only record history, (b) observation time, (c) decision effective interval | Over-machinery; confusing semantics | **"As known then"** = append-only history read at record time t. **"As now assessed about then"** = current assessments of records dated ≤ t. Valid time only for observations (when measured) and decisions (effective from/until) | Medium-high |
| F-13 | S §8.6–§8.8, §12.5; I §5.5 | L0/L1 hierarchies aid long-horizon cognition | No evidence yet. The "exact current-at-read projection" is well-defined only for deterministic fields (counts, statuses, open-objection lists), not for "current explanation" when several incompatible hypotheses are live. Persisted, incrementally refreshed overviews create the staleness, revocation and leakage problems that UPMS spent four candidates on | A second de-facto authority and a leakage channel | **No persisted narrative overviews in the first product.** Compass = deterministic queries (open questions, live alternatives per question, open objections, recent decisions, untested assumptions, stale evidence) plus on-demand, labeled, audience-scoped synthesis. Persist only after experiment E2 (§10) shows a gain | High |
| F-14 | S §10.2, §10.6, OQ7 | The threshold for human confirmation of AI reconstruction is open | It can be closed now: confirmation is needed **only to attribute content to a human** or to reach **decision-bearing use**. AI interpretations may exist unconfirmed, labeled as the AI's | Without this, either mandatory confirmation fatigue or silent attribution | Adopt: only the speaker confirms "I meant X". The AI is never the confirming party for human attribution. Unconfirmed AI interpretations are never shown with human attribution and never feed decisions | High |
| F-15 | S §11.4, SCIRE-11; scenario 10 | Proportionate rigor prevents a complexity inversion | No mechanism says who decides proportionality, or when | Over-formalization of every utterance, or none at all | **Demand-driven formalization.** Structure is created only on triggers: (a) a challenge is raised, (b) a decision is made, (c) content is exported, published or sent to SSDS, (d) someone asks. Default is the raw record plus an AI index | High |
| F-16 | S whole; I whole | Additive v0.2 is reviewable | 23 SCIRE and 22 INT invariants, 24 + 22 open questions; many v0.2 invariants restate v0.1 ones (SCIRE-12 / SCIRE-22, SCIRE-02 / SCIRE-19 partly) | Reviewers cannot tell which statements are binding | Consolidate in v0.3: one invariant list (§7 below suggests about 12), one vocabulary, removal of restated principles | High |
| F-17 | I §6.1, §6.4, §6.6 | A "conformal messaging" envelope and a semantic envelope candidate | The authors flag the accidental-ontology risk themselves. The envelope fields (temporal basis, output type, applicability, coverage, release constraints) are a de-facto shared schema | Interface ontology by stealth | Drop the neologism. Specify only per-operation contracts for the 3–5 operations that the first use case actually needs (§5, minimal variant) | Medium |
| F-18 | S §14.1; I §7.2 | Computation flows through SSDS | Most scientific evidence is not produced under SSDS: a postdoc's quick script, a collaborator's measurement, a literature value. An urgent re-evaluation (case 9) will not wait for governed execution | SCIRE either refuses real evidence or launders ungoverned results as governed | Evidence carries a **production class** (SSDS-governed / project-recorded / external-reported / uninstrumented). SCIRE accepts all classes with honest labels; only SSDS-governed results inherit SSDS qualification | High |
| F-19 | S §8.4, §10.6, §15 | Deletion and audit can be reconciled later | Deleting a transcript span orphans the structured claims derived from it, and attribution to a person who asked for removal cannot stay | Either broken history or a privacy violation | **Tombstones**: "a source attributed to role R existed; removed on date D under policy P", without content. Derived interpretations get "source withdrawn" and must be re-substantiated or re-attributed to the interpreter | Medium |
| F-20 | S §8.5 | Novelty to the group versus to the literature | Sound as stated. Missing: novelty claims are where derivative leakage is most likely, since "new insight" is often a paraphrase of a confidential source | — | Link the novelty check to the release-set floor: a discovery candidate lists the restricted sources in its production context | Medium |

---

## 5. Alternative architectures

The hand-off asks which alternative minimizes **total** complexity, authority confusion, migration burden and failure coupling while preserving scientific inspectability. In the table, "SCIRE scope" means what SCIRE itself must build.

| # | Alternative | SCIRE scope | Authority confusion | Failure coupling | Derivative-leak control | Migration burden | Scientific inspectability |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | **Proposal**: independent systems, thin domain-native interfaces | Very large: its own source plane, access control, release lineage, overviews, screening, plus semantics | Medium today (SC-A, SC-B unresolved); low once fixed | Lowest | Weak across systems: each system sees only its own releases | Low | High if built |
| 2 | **Shared event, provenance and release substrate**, separate domain semantics (UPMS-like store holds source records, access and release log; SCIRE owns only the semantic plane) | Medium: semantics only | Low if R1 and the SC-A rule hold | Higher: the substrate is a shared failure domain | **Strongest**: one release log sees all cross-system flows | High: two products co-evolve | High |
| 3 | **Common identity and query layer**, independent state | Large | Medium: a query layer tends to become a de-facto truth layer | Medium | Medium | Medium | Medium-high |
| 4 | **ELN- or notebook-first** with argument and question views (pages are the canonical record; SCIRE adds typed annotations, objection tracking and decision log over them) | Small to medium | Low | Low | Inherits the ELN's access model; release lineage still needed for AI output | Low | Medium: depends on discipline in annotation |
| 5 | **Minimal collaboration and retrieval**, postponing formalization (transcripts + AI index + explicit decisions, objections and questions only) | **Smallest** | Low | Lowest | Audience-scoped generation only | Lowest | Medium: answers the decay problems in §2.1 if R1–R3 hold |

### Ranking

**Now:** a **5 → 4 hybrid** as SCIRE's first product.

- Raw record plus AI index.
- Five explicit record kinds: question, statement-with-modality, objection, decision and observation-use link.
- Statuses governed by R1–R3.
- Audience-scoped generation for any shared output.
- No persisted overview hierarchy, no SDC type, no general argument hypergraph, no multi-agent choreography.

This tests the product premise at the lowest cost and keeps every migration path open.

**Second:** alternative 1, *with SC-A and SC-B fixed*, if SCIRE must ship as a self-contained product, for example for groups that will never run UPMS.

**Ambitious alternative worth keeping alive:** alternative 2. Cross-system derivative leakage (case 7) is the one problem that thin interfaces structurally cannot solve, because no single system observes the whole flow. If SCIRE and UPMS are both built, each will otherwise implement scopes, revocation, release lineage and overview maintenance, and these are the hardest parts of UPMS.

### What would change the ranking

- Move **up to 2** if experiment E3 (§10) or early use shows that ordinary research workflows routinely cross UPMS ↔ SCIRE ↔ SSDS with restricted material, and per-system release checks either leak or over-block. Also move up if the owner decides that UPMS *is* team project memory (decision D-A, option b).
- Move **down to 1 or 4** if UPMS stays agent-local (D-A, option a) and cross-system restricted flows are rare.
- Abandon SCIRE as a separate system (fold its R1–R3 rules into an ELN plugin or into UPMS rulesets) if experiment E1 shows no reduction in status-inflation errors over a capable LLM with archive and notebook.

---

## 6. Stress-test cases

Each case traces expected behavior under v0.2 as written, its point of failure or survival, and the earliest owner.

### 6.1 The ten required scenarios

**1. False contradiction.** Dataset A reports a property at 10 K. Dataset B reports it at 300 K under a different parameter definition.

- *v0.2:* §6.7 screening flags it, a candidate SDC opens, and Scenario K allows a "not directly comparable" conclusion. **Survives**, provided the comparability check runs *before* any "contradiction" status.
- *Failure point:* nothing forces that order. Deterministic checks need typed units and regimes, which free-text extraction may not provide, so a semantic screener may label the pair "contradiction" directly.
- *Owner:* scientific semantics. *Fix:* F-07 (mandatory comparability record). Local.

**2. Hidden dissent.** L0 says "mechanism M accepted". A low-frequency objection (M fails for doped samples) is unresolved.

- *v0.2:* §8.6 says such a caveat "cannot be omitted … must remain visible or be explicitly signaled". This is an aspiration over a narrative generator, not an enforceable property.
- *Failure point:* the summarizer ranks by salience and drops it; nothing detects the omission.
- *Owner:* scientific semantics plus domain architecture. *Fix:* F-09 (no "decided" status with an open objection lacking disposition) plus F-13 (compass fields are deterministic queries, so the open objection appears by construction). Local.

**3. Mistaken secretary.** A participant says "what if strain drives it?". The secretary records "Strain drives the transition (Dr. X)". Months later an agent cites it as a fact.

- *v0.2:* §10.6 distinguishes quotation, paraphrase, inferred premise, formalization and substantiated claim, and Scenario G has a participant correct it. **Survives only if someone notices.**
- *Failure point:* the attribution to Dr. X happened without confirmation, and the reuse path (agent memory → citation) never dereferences the modality.
- *Owner:* scientific semantics. *Fix:* F-14 (no human attribution without the speaker's confirmation), R2 (modality "hypothesized" survives every copy), and I §5.3 dereferencing extended to modality, not just to "current status". Local.

**4. Shared ancestry.** Three agents agree, all from the same review paper surfaced by one search.

- *v0.2:* Scenario O shows the shared dependency **if** retrieval provenance was recorded per agent.
- *Failure point:* the shared retrieval engine, model family and prompt are not edges, so the report counts three.
- *Owner:* evidence methodology. *Fix:* F-11 (independence as a claim with dimensions; agent agreement reported as one opinion with shared inputs). Local.

**5. Unexpected discovery.** An investigation of hypothesis H fails, but the calibration data reveal an unrelated anomaly.

- *v0.2:* discovery relations (§4.7) can link the anomaly to the investigation, and §5.3 says the original investigation is not the "parent". But the argument-first loop has no place for an observation with no argument.
- *Failure point:* the anomaly is either forced into H's argument as "contrary evidence", which is wrong, or lost.
- *Owner:* scientific semantics (foundational premise). *Fix:* F-03 (an inquiry can be opened from an observation; the failed investigation closes H's question with a null outcome and spawns a new question linked by "arose-from"). **Reopens the primitive.**

**6. Scientific retraction.** A cited paper's key result is retracted.

- *v0.2:* §7.7 and SCIRE-23 route dependents to review without falsifying history. **Survives in principle.**
- *Failure point:* dependents reached via *asserted equivalence* ("our result X is the same as their result Y") are missed if equivalences are not first-class links (F-05). The review obligation also has no owner or deadline, so it becomes a permanent badge nobody clears.
- *Owner:* evidence methodology. *Fix:* F-05, and review obligations carry an assignee and appear in the compass. Local.

**7. Private-source derivative.** A model writes a public explanation drawing on confidential project evidence, with no quotation. Adversarial variants:

- (a) **Multi-owner.** A's private dataset and B's confidential draft feed one team summary. Two owners must clear it; one owner's approval does not cover the other's content.
- (b) **Partial paraphrase.** Only one key number appears, rounded.
- (c) **Intermediate summary.** An L1 hub built by a session that could see the restricted draft is shown to members without access, so the leak happens *before* any publication.
- (d) **Independent reviewer.** A reviewer with private evidence publishes the verdict "the claim is unsupported". The verdict itself discloses one consequential bit.
- (e) **Revocation.** B revokes after the summary was shared. Revocation can only be prospective; readers are not "unseen".

Under v0.2, §15 and Scenario M require "release must respect the underlying source owner"; unknown lineage → withhold. Failure points:

- (c) is not covered at all, because overview projections are treated as internal navigation, not as disclosure.
- Without session release-set lineage, (a), (b) and (d) are all "unknown lineage", so the system either withholds everything or nothing.

*Owner:* interoperability and governance plus domain architecture. *Fix:* the floor in §3: release-set lineage, audience-scoped generation, which closes (c) by construction, and owner review across the project boundary. State (e) as prospective-only. For (d), treat a reviewer's verdict on restricted evidence as derived from it.

What the comparison of control approaches shows:

| Approach | Under-protection | Over-restriction |
| --- | --- | --- |
| Explicit owner approval per item | Low | Severe: approval fatigue leads to rubber-stamping |
| Scoped information flow (taint) | Low | Severe when applied at token or document granularity |
| Conservative withholding | Low | Kills collaboration |
| Review on publication | Medium; matches co-author sign-off norms | Low |
| Context-limited, audience-scoped generation | Low for instrumented content | Low; costs regeneration per audience |

The recommendation combines the last two, with session-level taint as the fallback when regeneration is impossible.

**8. Temporal ambiguity.** A later correction shows that a decision made in March relied on a mis-calibrated observation.

- *v0.2:* Scenario N reports the contemporaneous and the retrospective view separately. **Survives**, but through bitemporal machinery heavier than needed.
- *Owner:* domain architecture. *Fix:* F-12 (append-only history plus a decision effective interval). The March decision stays "valid when made"; a new review obligation records "basis later found defective". Local.

**9. Broken connector.** UPMS and SSDS are unreachable.

- *v0.2:* SCIRE-01 and I §4.4 keep core deliberation working, and Scenario XVII records the computation as not performed. **Survives.**
- *Residual risk:* a researcher runs the calculation locally and pastes the number. Without a production class (F-18) it looks like SSDS evidence.
- *Owner:* interoperability. *Fix:* F-18. Local.

**10. Complexity inversion.** A two-person project spends its meetings formalizing utterances.

- *v0.2:* SCIRE-11 and §10.3 say "progressive", but every v0.2 addition (SDCs, four relation families, L0/L1, bitemporality, ancestry coverage statements) adds per-utterance pressure, and no mechanism caps it.
- *Owner:* domain architecture. *Fix:* F-15 (demand-driven formalization) plus the 5 → 4 minimal variant. **Reopens scope**, not the premise.

### 6.2 Discrepancy counterexamples: reconciliations that would be wrong

**(i) The averaging reconciliation.** The neutron lifetime measured by beam methods (about 888 s) and by bottle methods (about 878 s) disagree by roughly 4σ. The obvious data-cleaning reconciliation, a weighted mean with an inflated error (a scale factor), yields one number and closes the case. That is scientifically wrong in two ways:

- It hides that the methods measure different things (total lifetime versus a specific decay channel), so the discrepancy *is* the scientific content. It bears on unknown systematics or new decay channels.
- It presupposes a shared estimand.

The correct SDC behavior:

- The comparability record says "different operational estimands under hypothesis H_dark; same estimand under the standard model".
- The case **stays open**, with the alternatives "unidentified systematic in method A or B" and "beyond-standard-model channel".
- The discriminating tests are named.

**(ii) The stratification reconciliation.** Two cohorts show opposite treatment effects. The obvious reconciliation stratifies by a third variable Z, and the reversal disappears (a Simpson's-paradox story). If Z is affected by both treatment and outcome (a collider), stratifying *creates* bias, and the pooled analysis was right. A "different regimes" reconciliation is therefore itself a causal hypothesis needing its own justification (the causal graph), not a bookkeeping move.

**(iii) The post-hoc regime reconciliation.** Theory and experiment disagree. A parameter is introduced so that they agree "in the doped regime". Agreement with the same data is not confirmation (R5): the case should be **split** into "is the regime distinction real?", which needs new data, and the original tension, still open until that data arrives.

**Lifecycle rules (proposed):**

- **Remain open** while no available observation discriminates the live alternatives. Closing by fiat is a decision, recorded as such, with dissent.
- **Split** when the comparability record reveals more than one independent tension.
- **Link (never destroy-merge)** when two cases share a root-cause hypothesis or a discriminating test.
- **Spawn** a new question when resolution needs something not about the original pair.
- **Not an SDC at all** when the mismatch is a semantic-identity error (units, definitions). Record it as a corrected equivalence claim (F-05).

### 6.3 Three-system break attempts

| Workflow | Expected behavior | Breaks? | Fix |
| --- | --- | --- | --- |
| Multi-year project transfer between agents | Agent memory leaves; SCIRE holds the project; the new agent dereferences | Survives, unless decisions were made off-SCIRE (chat, email) | "Decision import with attestation": a human records an external decision with its source |
| Contradictory memories of two agents | Both dereference SCIRE | Survives if SCIRE has the record. If UPMS team scope holds a Judgment, SC-A bites | SC-A rule |
| Urgent re-evaluation needing a calculation | SSDS queue too slow; local script used | v0.2 has no category for ungoverned evidence | F-18 |
| Shared laboratory evidence | Owned by ELN or LIMS; SCIRE references | Survives; references need the production class and a revision | F-18 |
| Cross-project discovery | An agent sees a link between projects A and B | **Leak risk**: the proposed link reveals B's content to A's members | Present the connection only to people with access to both; otherwise route it as a request to B's owner (release-set floor) |
| Publication | SCIRE drafts a paper section | Needs consent from all owners in the release set, and SSDS D1 for any governed claim | Floor in §3 plus SC-B; SCIRE produces a **source-owner manifest** with declared gaps |

---

## 7. Specific revision recommendations

### 7.1 SCIRE proposal (v0.3)

**Retain**

- P1–P10, rewritten as about eight non-redundant principles.
- §1, motivation, which is strong.
- §6.4 (no false precision), §6.6 (exploratory versus confirmatory), §7.1 (observation ≠ assessment), §7.5–§7.6, §8.5 (novelty levels), §9.3 (dissent states), §10.2 (reconstruction is fallible), §11.4 (avoid over-intervention).
- The negative half of §6.7 (flag ≠ evidence) and of §8.8 (not found ≠ none).

**Change**

- §0, §4.1 and §22: make the **inquiry (open question)** the primitive; arguments become optional structure (F-03).
- §4.3: separate record identity from semantic identity (F-05).
- §4.6 and §7: contrastive, conditional evidential relations (F-04); add use-role (F-10).
- §8.7: replace bitemporality with append-only history, observation time and decision interval (F-12).
- §9.5 and §14.1: SCIRE decisions are inputs to SSDS D1 for governed use (SC-B).
- §10.6: close OQ7 with F-14.
- §15: add the confidentiality floor (release-set lineage, audience-scoped generation, owner review) and tombstones (F-19).

**Remove or merge**

- The §4.2 table, down to the six-kind core (F-06).
- The SDC as a type, which becomes a question kind (F-07).
- "Argument context", which becomes explicit model or assumption conditioning.
- "Discovery candidate" and "Historical revision" as types, which become statuses and versioning.
- The v0.2 amendment-map duplication.
- SCIRE-16 to SCIRE-23, merged into one list (F-16).

**Defer**, until experiments E1–E3 justify them:

- Persisted L0/L1 overviews (F-13).
- Incremental overlays and periodic full synthesis.
- The general argument hypergraph.
- Multi-agent facilitation choreography.
- Cross-domain analogy discovery (§5.4).

**Add**

- R3 as a structural invariant (F-09).
- Demand-driven formalization triggers (F-15).
- Evidence production classes (F-18).
- No machine-to-machine status bootstrapping (F-08).

A suggested consolidated invariant list for v0.3: R1–R8 (§2.2), plus standalone integrity (rephrased per §2.3), human authority for decisions, permission boundaries, and demand-driven rigor. That is about 12 instead of 23.

### 7.2 Integration proposal (v0.3)

**Retain**

- §2.3 (memory ≠ agency ≠ authority).
- §5.1–§5.3 (referential memory, consequential dereferencing).
- §6.5 (transport ≠ authority).
- §8.1–§8.5 (no shadow authority, partial failure, idempotency at the receiver).
- §10.2 (memory is not an instruction channel).
- §10.6's three permissions.
- §11.5 (extraction allowed when evidenced).
- §15's phase order.
- The closing statement ("the agent remembers enough … the owning domain determines …").

**Change**

- §2.1, §3 and INT-03: boundary by semantic commitment (SC-A), pending decision D-A.
- §3 matrix and §7.2/§7.8: SSDS D1 is the sole scientific authority for governed use, and SCIRE is a candidate SSDP finding home (SC-B).
- §11.4: acknowledge that the duplicated mechanisms (scopes, revocation, release lineage, overviews) are *not* small, and state alternative 2 (§5) as a live option with its trigger.

**Remove**

- "Conformal messaging" and the generic envelope (§6.1, §6.4, §6.6). Replace them with per-operation contracts for the first use case only (F-17).

**Add**

- The cross-system release-set problem as the one stated reason that could justify shared infrastructure.
- Ungoverned-evidence production classes at the SCIRE ↔ SSDS boundary (F-18).

**Defer**

- §8.6 change notifications.
- The §8.4 seven-state delivery model, which is D4-level detail until a concrete cross-system operation exists.

---

## 8. Decisions requiring human scientific or governance authority

| ID | Decision | Options | Why reasoning alone cannot settle it |
| --- | --- | --- | --- |
| D-A | **What is UPMS?** | (a) agent-local and agent-group continuity only; (b) team project memory, as Candidate 4.1 says, with the SC-A rule that its judgments carry no domain standing; (c) the shared source, access and release substrate for SCIRE (alternative 2) | A product-scope choice across two products owned by the same person, with different roadmaps and review states |
| D-B | **Status of SCIRE decisions for SSDS-governed use** | Input to the D1 owner (recommended) or co-authority | Governance allocation; SSDS's accepted D1 process is not this review's to amend |
| D-C | **Is SCIRE standalone (SCIRE-01) a requirement or a preference?** | Requirement: build the full source plane. Preference: allow the alternative-2 deployment | Deployment and market judgment |
| D-D | **Who may confirm, decide and overrule** in a project | Per-project roles; minimum rule: only the speaker confirms their own meaning | Institutional responsibility, authorship norms and conflicts of interest differ across groups |
| D-E | **Default posture for unknown-lineage derivatives** | Withhold, review, or allow-with-label inside a project | A risk appetite; it trades confidentiality against collaboration |
| D-F | **Retention versus right to removal** for transcripts | Tombstones (F-19) with which retention periods | Legal and institutional policy |
| D-G | **Minimum evidence before SCIRE is trusted for consequential work** | E1–E3 thresholds | Choosing acceptable error rates is a value judgment |

---

## 9. Uncertainty, coverage and assumptions

- **Coverage.** I read both v0.2 proposals and the hand-off in full. I compared v0.1 to v0.2 by headings and removed lines only, so I did not review v0.1 content on its own.
- **UPMS.** I examined only the cited sections of Candidate 4.1 and its same-family review. I did not examine UPMS's other candidates or its Codex reviews, and nothing in UPMS is implemented.
- **SSDS.** I examined only the PEM front matter and summary, the head of the SSDP 7.0 epistemic-closure workplan, and the SSDP 7.2.1 inspectability owner. I did **not** examine the SSDS 8.0 graph-native orchestration architecture (accepted at G1 per its front matter). It may already define a graph or event substrate relevant to alternative 2. That is a coverage gap, and SC-B's details should be checked against it.
- **Assumptions.** The hand-off's characterization of UPMS NO-PASS SC-1 matches the review text I read. The proposals' readers include working scientists, not only protocol authors.
- **Scientific examples.** The neutron-lifetime figures and the Simpson/collider pattern are cited from general knowledge as illustrations. They are not sourced for this review and must not be reused as evidence.
- **Independence.** See the disclosure at the top. An independent (different-family) reviewer should in particular re-examine SC-A, which partly rests on Claude-authored UPMS text, and the recommended release-set floor, which is borrowed from a Claude-authored review.

---

## 10. Proposed next intellectual experiments

All three are cheap, use existing material, need no ontology or graph, and can falsify the product premise.

**E1 — Status-inflation and attribution fidelity (tests the premise).**

- *Input:* three or more real long-running project histories (meeting transcripts plus notes), with a human-annotated gold set of hypotheticals, open objections, decisions and null results.
- *Comparison:* (a) a capable LLM with search over the archive, answering routine questions (what's open, why was H rejected, what is the evidence basis, who claimed X); (b) the same LLM plus the 5 → 4 minimal record (R1–R3 statuses).
- *Measures:* the rate at which hypotheticals are reported as assertions, the misattribution rate, and recall of open objections and null results.
- *Falsifies the premise if* (b) is not materially better than (a).

**E2 — Overview compression loss (tests F-13 before any L0/L1 build).**

- *Input:* plant five decisive items in a project record: a minority objection, an invalidated assumption, a negative study, stale evidence and a permission-restricted source.
- *Comparison:* on-demand deterministic compass plus labeled synthesis, versus a persisted, incrementally refreshed narrative overview, after N updates.
- *Measure:* recall of the planted items, and whether the restricted source's content leaks into the view shown to a lower-access reader.
- *Persisted overviews are justified only if* they win on reader time without losing planted items.

**E3 — Cross-system derivative trace (tests the integration boundary and decision D-A).**

- *Input:* the adversarial set in §6, case 7(a)–(e).
- *Method:* trace each case on paper through (1) the proposal, (2) the proposal plus a per-system release-set floor, and (3) alternative 2's shared release log.
- *Measures:* how many cases each arrangement leaks, over-blocks or cannot decide.
- *If* (2) cannot decide at least one ordinary research workflow that (3) can, alternative 2 moves up the ranking.

A fourth, optional experiment: **E4 — Elicitation cost.** Have the secretary propose structure for a recorded meeting under demand-driven triggers. Measure the corrections per hour scientists make, and whether they accept the result. This bounds the complexity-inversion risk.

---

## Reporting obligation

- **Material findings:** SC-A, SC-B, the confidentiality-floor risk and F-01 to F-20 above. No tools or agents beyond file reading were launched.
- **Realized results and gate evidence:** none produced, run or reviewed. The examined material was design proposals and their cited source context (§9). Unexamined material areas are listed in §9.
- **Variants:** I evaluated no analysis or model variants. The architecture comparison in §5 is qualitative reasoning, not a measured selection.
- **Common-source limits:** disclosed under *Independence disclosure* and in §9.
