# Agent-Centered Memory and Domain Knowledge Interoperability

**Conceptual Cross-System Architecture Proposal**

**Version:** 0.2 — UPMS-informed conceptual revision; supersedes v0.1 as a review candidate only  
**Date:** November 2, 2026  
**Status:** PROPOSED — Unratified; pending independent concept-level review and human decisions  
**Intended reviewers:** General Memory Substrate developer, SSDS developer, SCIRE developer  
**Related document:** *SCIRE: Scientific Collaborative Inquiry and Reasoning Environment — Conceptual Scientific and Architectural Proposal*

**Revision basis:** Incorporates independently assessed patterns observed in the public UPMS architecture proposals. Those documents remain proposals, and UPMS Candidate 4.1 received a same-family **NO-PASS** review highlighting private-source-to-published-derivative disclosure risk. No external proposal is imported as accepted engineering or scientific authority.

**Review boundary:** Domain autonomy, access control, source verification and acceptance remain owned by each project's actual governing authority. This cross-system document does not amend accepted SSDS D1–D4, UPMS policy or the unratified SCIRE scientific semantics.

---

## 0. Executive Summary

This document proposes an architectural integration model for three independently developing systems:

1. **General Memory Substrate:** A persistent, adaptive, agent-centered memory system intended to provide continuity of experience, context, commitments, and long-horizon activity across projects and tasks.
2. **SCIRE:** A specialized scientific reasoning environment that owns structured arguments, questions, alternative hypotheses, evidence assessments, collaborative deliberation, and scientific discovery history.
3. **SSDS and its Project Engineering Memory (PEM):** A governed scientific software development and orchestration system, including project-scoped learning from engineering failures, successful practices, and historical evidence.

Although all three systems possess capabilities that can be described as memory, they address fundamentally different computational problems.

The General Memory Substrate is organized around the agent's experience and operational continuity. Its purpose is to help an agent remember what occurred, what context matters, what commitments remain, and where relevant information resides.

SCIRE and SSDS/PEM are organized around externally meaningful domain subjects. Their records are not simply memories of an individual agent. They are canonical project knowledge and governed state that may be accessed by many humans or agents.

Consequently, this proposal rejects the presumption that all three should share a universal memory kernel, persistence engine, ontology, or lifecycle.

Instead, it recommends:

**Agent-centered cognitive memory; domain-centered knowledge systems; explicit, permission-checked, domain-native interoperability.**

The General Memory Substrate should help agents navigate between projects and operational modes. Specialized systems should independently own their scientific or engineering objects and expose appropriately authorized operations through tools, APIs, or MCP interfaces.

Each system must remain operational without the others.

Shared design principles and implementation utilities are permitted, but shared runtime infrastructure should be introduced only when a concrete, stable, independently justified requirement demonstrates its value.

This is a conceptual architectural proposal. It does not require immediate changes to the existing SSDS architecture or to the in-development General Memory Substrate. It proposes a future-compatible integration model for independent review and refinement.

---

### v0.2 changes and scope (non-normative)

The thin-interoperability position is preserved. The revision additionally specifies how navigation should distinguish owner-projected current state from narrative memory, why source/derived records and their release restrictions matter across connectors, which temporal and coverage metadata to carry, and how independent scientific critique can remain meaningful despite sharing tools and sources. These are interface-level concerns; the proposal does not create a common object schema, runtime, ontology, global ancestry database or centralized approval service.

---

## 1. Motivation

### 1.1 The problem with treating every persistent information system as one kind of memory

The term *memory* covers several substantially different capabilities.

An AI agent may remember a prior discussion, an unfinished task, and a researcher's goals.

A scientific argumentation environment may preserve the structure of a hypothesis and the justification supporting it.

An engineering system may retain recurring failure mechanisms and evidence-backed lessons from previous implementations.

All persist information across time, but their fundamental objects and operations differ.

The fact that they share persistence, retrieval, and historical relationships does not establish that they should share one semantic architecture.

### 1.2 The risk of premature consolidation

A universal memory kernel might initially appear attractive because it promises shared identity, history, retrieval, and provenance.

However, this consolidation can impose substantial costs:

- Different systems become coupled to the same lifecycle and object model.
- A domain-specific feature requires changes to an unrelated common component.
- Schema migrations affect multiple projects.
- Independent releases become harder.
- Scientific or engineering semantics may be distorted to fit generic representations.
- Common infrastructure becomes a new operational dependency and potential failure domain.
- A shared abstraction may accumulate domain-specific exceptions until it becomes more complex than separate implementations.

These risks are especially significant while the systems' requirements remain under active discovery.

### 1.3 The alternative

The proposed alternative is to separate systems according to the *subject and authority of their records*.

The General Memory Substrate remembers an agent's experience across activities.

SCIRE remembers a scientific project's reasoning and discovery.

SSDS/PEM remembers governed engineering work and reusable project experience.

Agents communicate with each domain through its own contract.

The architecture therefore prioritizes independent development and interoperable behavior over structural uniformity.

---

## 2. Foundational Architectural Distinction

### 2.1 Agent-centered cognitive memory

The General Memory Substrate is conceived as a persistent, adaptive memory associated with an agent or authorized group of agents.

Its purpose is to support:

- Recollection of past interactions and experiences.
- Recognition of recurring contexts.
- Continuity of long-running goals and commitments.
- Awareness of prior decisions and unfinished work.
- Contextual navigation between projects and tools.
- Consolidation of experiences into useful long-term knowledge.
- Retrieval of relevant background with bounded cognitive overhead.
- Cross-task associations and long-horizon coordination.

Its fundamental information is organized around the question:

**What should this agent remember from its experience to operate effectively now and in the future?**

The General Memory Substrate can contain factual and semantic knowledge, but its distinguishing role is agent-centered continuity.

It is not presumed to contain the complete canonical scientific or engineering record of every system the agent accesses.

### 2.2 Domain-centered project knowledge

SCIRE and SSDS are specialized external systems organized around their domains.

SCIRE manages scientific arguments, inquiry, evidence, and decisions.

SSDS manages governed engineering execution, scientific-software authority, project state, and qualification evidence.

PEM is a specialized, non-authoritative representation of evidence-backed engineering learning within SSDS's project governance.

Their central records are defined by domain semantics rather than an individual agent's subjective experience.

A project may exist before an agent joins it, continue after the agent leaves, and be accessed by multiple authorized participants.

These systems are consequently more analogous to domain-specific databases and knowledge environments than to components of an individual agent's cognitive memory.

### 2.3 Memory, agency, and authority are distinct

Three functions must remain separate:

**Memory:** Retains and retrieves information relevant to current activity.

**Agency:** Reasons about goals, proposes actions, selects tools, and interacts with the environment.

**Authority:** Determines which consequential actions or state changes are permitted and accepted within a domain.

The General Memory Substrate may inform an agent that a calculation was previously approved.

It must not independently create valid approval merely by recalling that claim.

SCIRE may identify a promising scientific investigation.

It must not thereby acquire authority to bypass SSDS's execution controls.

PEM may identify an applicable engineering lesson.

It must not promote that lesson into accepted engineering authority solely on the basis of historical success.

These distinctions remain valid whether the systems are integrated or standalone.

---

## 3. Responsibility and Ownership Matrix

| Responsibility | Primary owner |
|---|---|
| Agent experiences, contextual recollection, cross-project continuity | General Memory Substrate |
| Agent-associated goals, remembered obligations, navigation cues | General Memory Substrate, subject to external verification |
| Scientific propositions, arguments, inference applications | SCIRE |
| Scientific questions, hypothesis portfolios, and discovery lineage | SCIRE |
| Scientific deliberation contributions and attributable assessments | SCIRE |
| SSDS accepted D1–D4 and project execution state | SSDS and its respective authority owners |
| Engineering failure families, learning records, applicability | SSDS PEM |
| Numerical simulation and qualification artifacts | Their executing and governing domain systems |
| Cross-system tool invocation | Authorized agent and integration interfaces |
| Access-control enforcement | The resource-owning system |
| Consequential scientific or engineering approval | The designated governing authority |
| Cross-system references and contextual summaries | May be held by consumers, subordinate to the owning records |

The key principle is:

**A canonical record has one authoritative domain owner, even when many systems refer to, index, or summarize it.**

Physical storage may be distributed or reused, but storage location does not independently confer semantic or decision authority.

---

## 4. Independent Operation as a Foundational Requirement

### 4.1 General Memory Substrate independence

The General Memory Substrate must function as an agent-centered memory system without SCIRE or SSDS.

It may support ordinary interactions, contextual retrieval, experience consolidation, and task continuity for unrelated applications.

Scientific and engineering connectors are optional.

### 4.2 SCIRE independence

SCIRE must preserve its own scientific project records, argument history, collaborative discussions, and research continuity.

It must not depend on the General Memory Substrate to remember which arguments, decisions, or scientific questions exist.

Its core operations must remain available when SSDS is absent.

Some external investigation or evidence-import capabilities may be unavailable, but scientific discussion and argument management should remain usable.

### 4.3 SSDS independence

SSDS must continue to operate according to its own accepted scientific, numerical, architectural, and execution authority.

Neither SCIRE nor the General Memory Substrate may become a required runtime dependency for independently authorized work.

PEM retains its existing governance and applicability semantics unless separately changed through its governing process.

### 4.4 Failure isolation

A failure or upgrade of one system should not automatically stop the others.

Integration errors should degrade the associated optional capability rather than invalidate unrelated domain operations.

A system that is unavailable, unauthorized, or unreachable should be reported accordingly.

Absence of a response must never be interpreted as evidence that the remote record does not exist or that an outstanding obligation has been fulfilled.

### 4.5 Independent development lifecycle

Each system should be independently implementable, testable, versioned, reviewed, and released.

No system's internal representation should require approval from the developers of the other systems merely to evolve within its own domain.

Coordination is required only when changing an externally relied-upon interoperability contract.

---

## 5. Referential Cognitive Memory

### 5.1 General memory should retain navigational knowledge

When an agent participates in a scientific project, it need not duplicate the complete argument graph in its own memory.

Instead, it should remember enough to reconnect the agent to the relevant project.

A contextual memory may contain:

- Which project was being investigated.
- What broad scientific or engineering problem motivated the work.
- Which decisions or commitments were made.
- Which outstanding actions require attention.
- Which external domain records contain the authoritative details.
- Which source revision or historical context the recollection refers to.
- Whether the remembered information is a summary, hypothesis, or verified current state.

This is **referential cognitive memory**: memory that provides continuity and navigation without pretending to be the canonical representation of the referenced domain.

### 5.2 Why duplication is dangerous

An agent may remember that hypothesis H-014 was previously favored.

SCIRE may subsequently record that H-014 was challenged by new evidence.

The agent's historical memory remains meaningful, but it no longer establishes the hypothesis's current scientific status.

Likewise, an agent may remember that an SSDS workplan was approved. That recollection cannot prove that the approval remains applicable to the current branch, artifact revision, or scientific formulation.

### 5.3 Consequential dereferencing

When a consequential decision depends on current domain knowledge, the agent should retrieve the relevant object from its owning system.

Casual conversational continuity need not trigger comprehensive verification of every remembered detail.

However, scientific interpretation, execution authorization, publication claims, and material engineering decisions require current, applicable evidence and authority.

### 5.4 Source-linked contextual summaries

Agent-memory summaries referring to external projects should retain sufficient source identity to prevent silent ambiguity.

They may include a stable object reference, project identity, source revision, retrieval time, and a declaration that the information is a contextual summary.

Where exact revision information is unavailable, that limitation should remain visible.

The summary's existence must not manufacture confidence in the underlying domain claim.

---

### 5.5 Tiered orientation belongs to its respective owner

Hierarchical summaries are useful at two different levels, and must not be conflated. **UPMS** may maintain agent-centered overview layers of experiences, goals, outstanding commitments and links to other domains. **SCIRE** may maintain a project compass, inquiry hubs and detailed source-backed scientific objects. **SSDS** may expose governed current authority/workplan state and PEM-derived historical lessons under its own rules. These hierarchies do not need to share storage, generation algorithms or node types.

A memory-created orientation about a SCIRE project is a navigational derivative of a derivative, not a replacement for SCIRE's current assessment. A summary of an SSDS approval cannot authorize execution. The safest common capability is a permission-scoped path from an agent's recalled context to the owning project's exact current or historical reference.

### 5.6 Retrieval intent, scope and coverage

Cross-domain queries should explicitly or implicitly distinguish **orientation**, **historical recollection**, **current-state verification**, **explanation/justification**, **source inspection**, and **task resumption**. For a consequential request, the receiver returns the relevant owner-authenticated scientific/engineering records or qualified failure, not merely a plausible free-text answer.

Returned projections should identify their as-of status or revision when available, when the source was read, relevant assumptions/validity regime, and known limitations such as index watermark, inaccessible records, or excluded scopes. If no complete search was performed, 'not found' means 'not found in this searched coverage', not 'does not exist'. A caller must not downgrade a current verification request into an unchecked memory narrative merely to obtain an answer.

---

## 6. Conformal Messaging and Domain-Native Tool Use

### 6.1 Proposed definition

For this proposal, *conformal messaging* means:

**A communication pattern in which a caller interacts with a domain through that domain's declared interface and semantic contract, rather than requiring the domain to translate its internal knowledge into a universal memory ontology.**

The term is provisional. It describes a design principle rather than a required protocol.

### 6.2 Agent-mediated interaction

The principal expected interaction model is:

1. An agent uses general memory to recover relevant context.
2. The agent identifies an appropriate external domain system.
3. It discovers the domain's available operations and permissions.
4. It submits a request in the domain's accepted structure.
5. The domain validates the operation against its own rules.
6. The domain returns results, references, or an explicit failure.
7. The agent interprets the result in the current task context.
8. General memory may preserve a concise experience record and navigational references.

Neither the caller nor the memory system acquires control over the recipient's semantic authority.

### 6.3 Appropriate interfaces

Tools, APIs, and MCP servers are candidate integration mechanisms.

A SCIRE interface might expose argument inspection, hypothesis comparison, scientific challenge submission, and investigation proposal operations.

An SSDS interface might expose governed project state, evidence retrieval, workplan inspection, or authorized execution requests.

The General Memory Substrate might expose contextual recall, memory recording, or experience retrieval.

These operations should remain domain-native.

A universal `update_memory` API with unconstrained payloads should not become a means of modifying arbitrary scientific or engineering authority.

### 6.4 Shared outer envelope

Interoperability may benefit from a small common communication envelope containing:

- Originating system or actor identity.
- Intended recipient and domain operation.
- Request and correlation identity.
- Target object identity and relevant revision.
- Authorization context.
- Domain-specific payload.
- Result status and returned references.

The envelope provides routing and accountability.

It does not impose a common schema for scientific arguments, engineering lessons, or cognitive experiences.

### 6.5 Tool transport is not authority

MCP or another tool transport may provide structured access, but it does not automatically determine which scientific actions are authorized.

The receiving domain must independently verify permissions and governing conditions.

A tool call is a request, not proof of acceptance.

---

### 6.6 Optional cross-domain reference and projection contract

A minimal external read result might conceptually distinguish: (a) source-owner and object/revision identity; (b) **as recorded/as valid** time or a supported temporal qualifier; (c) type of output—historical event, source excerpt, structured domain record, confirmed decision, tentative assessment, or synthesized orientation; (d) scientific applicability and evidentiary qualifications where relevant; (e) retrieval/coverage/freshness; (f) receiving-actor visibility and release constraints; and (g) references needed to verify the material claim. This is a **semantic envelope candidate**, not mandatory fields for all messages or a universal serialized ontology.

If an interface cannot supply a field, it should declare that limitation where material; inventing a revision, source span, permission or scientific status is unacceptable. Interfaces may decline to return confidential evidence and instead return an authorized pointer, summary with properly limited disclosure, or denial. Routing metadata must not themselves leak private project names or descriptions to unauthorized recipients.

### 6.7 Cross-system ancestry and release checks

The shared envelope does not need to carry a global provenance graph, but a released derivative must respect its material **source/production exposure**. In a workflow involving memory, SCIRE and SSDS, assess both direct content and identifiable source ancestry before allowing material to enter a broader scope. Claims of independent review should likewise identify common upstream information; a separate agent context does not guarantee independence if it sees the same private draft or inherits another agent's conclusions.

Where an access/release decision needs provenance that the current integration cannot establish, the honest outcomes are bounded restricted use, source-owner review, or denial—not automatic release. A technically authenticated MCP tool invocation does not establish permission to redistribute the resulting information.

---

## 7. Proposed Cross-System Interaction Scenarios

### 7.1 Resuming a scientific investigation

An agent recalls from general memory that a scientific project contains unresolved hypotheses.

It queries SCIRE using a stable project or question reference.

SCIRE returns the current hypothesis portfolio, unresolved challenges, and applicable scientific decisions.

The agent prepares its next response based on the domain record, not solely its previous recollection.

### 7.2 Moving from deliberation to computation

Researchers identify a discriminating calculation in SCIRE.

An authorized participant approves an investigation request under the project's decision rules.

An agent submits the request through an SSDS-facing interface.

SSDS evaluates applicable accepted scientific and execution authority, performs or schedules the governed work as authorized, and publishes identified results and evidence.

SCIRE imports or references the results and prepares a scientific reassessment.

The general memory substrate may remember that the investigation occurred and that a follow-up discussion remains necessary.

### 7.3 Learning from engineering failure

An SSDS implementation encounters a recurring failure mechanism.

PEM may preserve an evidence-backed engineering lesson through its native governance.

An agent later remembers that the project encountered this class of problem and queries PEM for applicable guidance.

PEM performs its own applicability assessment.

The General Memory Substrate does not independently declare the lesson valid in a new project.

### 7.4 Cross-project scientific discovery

An agent recalls that one scientific project investigated a mechanism possibly relevant to another.

The agent queries the relevant SCIRE project records and presents a proposed connection.

SCIRE evaluates the scientific argument under the applicable definitions, assumptions, and evidence.

The general memory provides navigation and continuity; scientific validity remains domain-owned.

### 7.5 Operation without general agent memory

A researcher opens SCIRE directly.

The project loads its native scientific history and argument state.

The researcher resumes the discussion without needing an agent's personal memory.

This is a required standalone use case, not a degraded fallback.

### 7.6 Operation without SCIRE

An agent uses general memory while working on an ordinary software task or with SSDS directly.

The agent does not need SCIRE to interpret its experiences or maintain task continuity.

### 7.7 Unavailable or stale domain source

An agent remembers a previous SSDS approval but cannot retrieve its current governing state.

The agent may report the historical recollection, but must not treat the approval as verified.

A consequential action remains subject to the receiving domain's independent authorization.

---

### 7.8 Deliberation discrepancy versus engineering action

A SCIRE Scientific Discrepancy Case may record a conflict among predictions, experiments or interpretations and propose an SSDS calculation. SCIRE owns the scientific inquiry and its explanatory alternatives; SSDS independently determines whether the requested computation is permissible under accepted scientific, numerical and engineering authority. After results arrive, SCIRE may reinterpret their implications but does not rewrite SSDS's execution evidence or accepted D1–D4 authority.

A general-memory agent may remember the unresolved case, its requested follow-up and the reference to inspect. It must not publish a harmonized 'resolved result' when SCIRE's case remains contested or the SSDS result is stale, unavailable or regime-inapplicable.

---

## 8. Canonical Ownership and Synchronization

### 8.1 Avoid shadow authorities

The principal integration risk is duplicating domain state in ways that create competing authorities.

Examples include an agent memory that retains an outdated scientific conclusion, an external cache that appears to supersede an SSDS decision, or a SCIRE summary that misstates a source observation.

The architecture should identify one canonical owner for each material record.

Consumer-side summaries, caches, and indexes are derived representations.

### 8.2 Historical recollection versus present state

A memory statement such as "the team accepted hypothesis H last month" is a historical claim.

It is not necessarily a statement that H remains accepted.

Interfaces and retrieval results should support this distinction.

### 8.3 Cross-system synchronization

The architecture should not presume continuous replication of all scientific and engineering records.

In most cases, stable references and on-demand retrieval should be sufficient.

Notifications or subscriptions may be useful when changes materially affect pending agent actions, but are not mandatory for all integrations.

### 8.4 Delivery and idempotency

When a consequential operation crosses systems, the design should eventually distinguish:

- Request submitted.
- Request received.
- Request validated.
- Request accepted.
- Execution started.
- Execution completed or failed.
- Result durably published.

A repeated delivery should not unintentionally duplicate a computation or authorization.

Where retries are supported, request identities and idempotency rules must be defined at the relevant receiving boundary.

### 8.5 Partial failure

No globally atomic transaction across all three systems is presumed.

If an SSDS result is published but SCIRE fails to import its reference, the SSDS result remains authoritative in its own domain.

SCIRE can later reconcile the missing update.

If an agent's general memory fails to record an interaction, this does not undo an accepted SCIRE or SSDS operation.

The system should report incomplete synchronization rather than invent a globally consistent state.

---

### 8.6 Change awareness without creating shadow authority

Optional event notices, freshness hints and revision-bound links can tell a consumer that a referenced scientific/engineering object changed. They do not make the consumer's snapshot current, authorize mutation, or guarantee synchronized truth. On a materially changed definition, evidence source, authorization or SDC status, the caller should re-query the owning domain; any old memory remains a historical claim.

A bounded project overview may be incrementally refreshed and occasionally rebuilt from owning records, but the integration contract neither mandates a consolidation schedule nor endorses automatic overwrite of contested meaning. The owning domain determines which revisions and material retractions invalidate its exports. Cross-domain referential consistency is checked at use time or by specific reconciliation, not globally presumed.

### 8.7 Time, identity and applicability in exchanged assertions

A distinction between when an event was valid and when the system recorded it is particularly important when answering 'what did we know at the time?' versus 'what do we now conclude happened?'. Historical citations should preserve the supplied temporal basis. A scientific conclusion about one material/model regime should not silently become a universal fact when imported into general memory or an engineering request. Content similarity is not semantic identity: material changes in quantity, units, parameter values, scope or assumptions require owner review or an explicit equivalence mapping.

---

## 9. Multi-Agent Memory and Collaboration

### 9.1 Agent memory may be individually scoped

Different agents may have distinct experiences, responsibilities, context histories, or permissions.

The General Memory Substrate should not presume that all agents share an undifferentiated cognitive memory.

### 9.2 Shared projects remain domain-owned

Several agents may participate in the same SCIRE research project while maintaining different operational memories.

The canonical scientific argument graph remains project-owned.

Likewise, multiple engineering agents may work under the same SSDS project without owning separate incompatible versions of its accepted authority.

### 9.3 Shared operational memory is optional

A research group may benefit from shared contextual information, such as upcoming meetings or approved project priorities.

Such information can be represented through an explicitly authorized shared scope.

It must not silently merge private participant memory with public scientific records.

### 9.4 Identity and attribution

Cross-system interactions should distinguish:

- The authenticated actor invoking a tool.
- The human or AI participant that originated an assertion.
- The agent that interpreted or transformed the assertion.
- The participant authorized to approve the operation.
- The system that recorded or published the result.

These identities need not be the same.

A shared service account or tool credential must not erase contribution attribution or manufacture human authorization.

---

### 9.5 Independence and common-mode critique

Agents may perform independent scientific or engineering review, but independence has dimensions: distinct context, source exposure, model/provider, prompt, tools, evaluation standard, and external evidence. For a high-consequence claim, the review record should state the degree of separation supported by available ancestry, without pretending that instrumentation can detect all human or out-of-band influence. An agent that merely repeats another agent's assessment does not provide a new corroborating scientific observation.

A privately scoped reviewer may need restricted evidence; release of its eventual synthesis to a broader group is a **separate permission decision**. A supervisor's task approval or the reviewer's access is not proof that private upstream evidence may be republished in derived form.

---

## 10. Security, Privacy, and Trust Boundaries

### 10.1 Independent trust boundaries

Each system controls access to the resources it owns.

An agent's ability to access the General Memory Substrate does not imply permission to read every scientific project.

Access to an SSDS execution result does not imply authority to edit its accepted workplan.

Permission to inspect a SCIRE argument does not necessarily permit disclosure of the underlying confidential dataset.

### 10.2 Memory must not become an instruction channel

The General Memory Substrate, PEM, retrieved SCIRE arguments, and external documents may contain instruction-like language.

Such content must be treated as data unless separately authorized through the applicable instruction and action boundary.

A remembered instruction is not inherently a current authorization.

### 10.3 Confidential information propagation

Agents should not automatically copy complete project records, private research discussions, credentials, or sensitive experimental data into broad general memory.

Where cognitive continuity is useful, the preferred approach is a minimal contextual summary and an appropriately permission-bound reference.

### 10.4 Access revocation

When access to an external record is revoked, previously stored references and cached summaries must not create an unauthorized retrieval route.

The later implementation must define how revocation affects cached material, search indexes, and retained contextual memories.

### 10.5 Provenance and source integrity

Material imports should retain sufficient source identity, revision, and trust context.

A retrieved scientific interpretation must not silently supersede the original source.

A missing, stale, incompatible, or revoked source should degrade the usability of dependent conclusions rather than be silently replaced by similar material.

---

### 10.6 Derivative confidentiality: an explicit architectural challenge

The public UPMS Candidate 4.1 same-family review reported **NO-PASS**, with a serious challenge in which private team material could reach a wider audience through a published agent-generated derivative. The underlying issue is not only verbatim copying. A synthesized insight, extracted claim, anonymized explanation, or response that uses the private source can reveal protected knowledge even when the original source is not quoted. Source-owner release approval cannot be inferred from an agent's ability to read, a human overseer's ordinary task approval, or an output marked 'summary'.

An integration must distinguish at least three permissions where they are material: **read/use source**, **retain in a new memory or project scope**, and **disclose/publish derived content to a recipient**. These permissions may differ. The producer domain and consumer must each enforce the parts of the decision within their control, including downstream recipients, cross-scope agents, cached summaries and exports. Source and production ancestry should remain attributable through transformation as far as the authorized system can actually observe; unknown lineage is a coverage gap, not proof of unrestricted origin.

This proposal does **not** resolve the detailed release-policy language, information-flow enforcement, legal/privacy deletion semantics, or cross-organizational enforcement. A conservative concept-level outcome is to refuse or seek source-owner clearance when material lineage/release eligibility is unresolved. Review must test both direct quotations and scientifically novel-looking derived assertions. Merely adding citations or generic taint labels may be insufficient or overly restrictive; proportional, implementable alternatives deserve comparison.

---

## 11. Why a Shared Memory Kernel Is Not Recommended

### 11.1 Distinct fundamental data models

The General Memory Substrate is event- and experience-centered.

SCIRE is argument- and inquiry-centered.

PEM is engineering-lesson- and applicability-centered.

Their distinct semantics do not reduce cleanly to a universal memory object model.

### 11.2 Distinct lifecycle operations

General memory may consolidate experiences and adjust retrieval salience.

SCIRE may retain simultaneous alternative argument contexts, revise inference structures, and preserve epistemic history.

PEM may admit evidence-backed lessons, change maturity or applicability, and retain accepted-base versus candidate-overlay distinctions.

A shared lifecycle would likely require extensive domain-specific exceptions.

### 11.3 Coordination overhead

A common kernel can turn a local feature into a cross-project dependency.

This increases review, migration, testing, and release costs.

When the domain abstractions are still evolving, those coordination costs may exceed the value of shared implementation.

### 11.4 Acceptable duplication

Independently implemented stable identities, local journals, or indexing utilities are not inherently architectural defects.

Small duplication may be less expensive than a shared abstraction with incompatible clients.

### 11.5 Future extraction remains possible

The proposal does not prohibit shared utilities or later consolidation.

A common component may be extracted if its semantics are demonstrably stable across independent consumers, the total architecture becomes simpler, and domain-specific evolution remains possible without repeated shared-component changes.

Such extraction should be motivated by observed duplication or maintenance cost, not by the broad label *memory*.

---

## 12. Integration Architecture Alternatives

### Alternative A — Complete consolidation

One shared memory kernel owns all persistence, identity, semantics, and lifecycle operations.

**Assessment:** Not recommended. It creates substantial semantic and development coupling without demonstrated necessity.

### Alternative B — Independent domain semantics on a compulsory shared storage engine

Each domain owns its logic but must use the same infrastructure and persistence contract.

**Assessment:** Possible in a future deployment, but not an appropriate initial architectural requirement. Physical convenience should not become a universal dependency.

### Alternative C — Fully independent systems without standardized interoperability

Every project evolves independently and integrations are ad hoc.

**Assessment:** Better isolation, but risks brittle point-to-point connections and ambiguous authority.

### Alternative D — Independent systems with thin domain-native interoperability

Each system owns its semantic model, lifecycle, records, and operation.

Agents communicate through explicit, versioned, permission-checked interfaces.

Shared principles and selected utilities may be reused without mandatory infrastructure consolidation.

**Assessment:** Recommended conceptual baseline.

This alternative preserves both independence and purposeful integration.

---

## 13. Proposed Interface and Evolution Principles

### 13.1 Domain-owned contracts

Each system publishes only those operations necessary for external clients.

Its internal schemas and storage structures are not automatically public integration contracts.

### 13.2 Narrow interfaces

Prefer a small collection of domain-specific read, query, proposal, and authorized-command operations.

Avoid broad generic mutation APIs that bypass semantic validation.

### 13.3 Versioned interoperability

Materially changing an externally relied-upon operation requires explicit compatibility consideration.

Internal changes that preserve the exposed contract should remain local to the owning project.

### 13.4 No forced global consistency

The architecture should distinguish authoritative local state from potentially delayed cross-system observations.

A global synchronization barrier is not assumed.

### 13.5 Explicit degraded modes

Unavailability of an optional system should produce a defined capability limitation.

Other functionality should remain usable where its own requirements are satisfied.

### 13.6 Future-ready, not future-dependent

Systems may be designed with stable external references and optional connector boundaries before a complete integration exists.

They need not implement hypothetical future integrations or create placeholders for every conceivable external system.

---

### 13.7 Independent contract evolution and projection semantics

A domain may offer source-linked overview, exact current-status, historical reconstruction, discrepancy-case inspection, material evidence inspection, proposal submission and governed execution request as **distinct operations** where useful. Avoid a single generic operation that conflates conversational retrieval, inquiry, authority inspection and mutation. Different consumer intents may require different levels of evidence, identity, revision, permission and completeness.

Minimal contract evolution should preserve existing domain semantics and permit unsupported-feature responses. A consumer must not treat a missing operation or field as an approval, a negative scientific finding, or proof that no data exist. The domain owner is responsible for stable external behavior; downstream agents cannot redefine the meaning of 'accepted', 'in review', 'refuted', 'historical', or 'independently verified'.

---

## 14. Conceptual Acceptance Scenarios

### Scenario I — Independent SCIRE deployment

SCIRE is installed without the General Memory Substrate or SSDS.

It supports durable collaborative scientific projects, argument revisions, hypothesis portfolios, and historical reconstruction.

**Expected:** Core functionality succeeds.

### Scenario II — Independent general memory deployment

An agent uses general memory across unrelated tasks without SCIRE or SSDS.

**Expected:** Agent-centered context and experience continuity remain functional.

### Scenario III — Independent SSDS deployment

SSDS runs an authorized scientific software workflow with its own PEM and qualification records.

**Expected:** No SCIRE or general-memory dependency exists.

### Scenario IV — Cross-domain scientific investigation

An agent retrieves a scientific problem from SCIRE, submits an authorized request to SSDS, and returns identified results.

**Expected:** Each domain validates the operation according to its own contracts. Source evidence remains attributable.

### Scenario V — Stale recollection

The agent remembers that a scientific hypothesis was previously accepted, but SCIRE has subsequently revised it.

**Expected:** The agent distinguishes its historical recollection from current scientific state and uses the domain-owned record for consequential decisions.

### Scenario VI — Connection failure

SCIRE cannot reach SSDS.

**Expected:** SCIRE retains its scientific project and records the external operation as unavailable or pending as appropriate; it does not claim the calculation completed.

### Scenario VII — Duplicate tool request

A tool call is retried after an uncertain network response.

**Expected:** The receiving domain prevents unintended duplicate consequences or exposes a safe recovery mechanism.

### Scenario VIII — Unauthorized action

An agent's memory contains a purported instruction to modify accepted SSDS authority.

**Expected:** SSDS rejects the mutation absent current, independently valid authorization.

### Scenario IX — Agent-specific privacy

Two agents with different permissions participate in the same research environment.

**Expected:** Their cognitive memories remain appropriately separated, and domain access follows the authorized resource scope.

### Scenario X — Independent evolution

SCIRE adds a new scientific inference type.

**Expected:** No modification of the General Memory Substrate or PEM is necessary unless an existing external contract itself changes.

### Scenario XI — External evidence loss

A cited SSDS artifact becomes inaccessible or is discovered to be inapplicable.

**Expected:** SCIRE retains the historical reference but visibly qualifies dependent current assessments; general memory does not silently substitute another result.

### Scenario XII — Proposed shared utility

Developers identify equivalent, stable persistence functionality across projects.

**Expected:** Reuse is evaluated against compatibility, migration, independence, resource, and coordination costs. Shared implementation is optional rather than presumed.

---

### Scenario XIII — Restricted derivative across scopes

An agent with permission to inspect a confidential SCIRE meeting generates a result for a team-wide or public answer. The response might be paraphrased and technically novel. **Expected:** the consumer cannot infer publication rights from source read access or overseer approval; material source/production ancestry and target visibility are assessed, or disclosure is denied/pended for source-owner review.

### Scenario XIV — Cross-domain 'not found' is not 'none'

General memory asks whether a scientific claim has been challenged; SCIRE returns no result from a partial index or restricted search. **Expected:** the answer discloses the searched coverage and cannot claim globally that no contrary evidence exists.

### Scenario XV — Source chronology versus retrospective correction

A memory agent asks what was accepted before an experiment, then what the project currently concludes about that period. **Expected:** both queries preserve the owning domain's distinct temporal/status meanings; no retroactive rewrite of the historical record.

### Scenario XVI — Reviewer evidence is correlated

Two agents independently type a critique but both inherit the same generated synthesis. **Expected:** the system does not advertise epistemic independence without ancestry evidence; materially shared assumptions remain visible.

### Scenario XVII — Discrepancy-to-computation flow

SCIRE flags an apparent contradiction that may arise from different scientific regimes; SSDS is unavailable. **Expected:** SCIRE continues its discrepancy inquiry, distinguishes explanatory alternatives, and records external computation as not performed; no fabricated result or permission escalation occurs.

---

## 15. Development and Adoption Strategy

### Phase 1 — Independent system development

Allow each project to continue under its own accepted design and implementation processes.

SCIRE should prioritize its scientific argument and inquiry model.

The General Memory Substrate should prioritize persistent agent cognition.

SSDS should maintain its existing governance, engineering memory, and orchestration responsibilities.

### Phase 2 — Minimal interoperability discovery

Identify concrete use cases that require cross-system interaction.

Document the source owner, consumer, operation, necessary data, authorization requirements, and expected failure behavior.

Record separately whether a use case needs an orientation, exact owner state, historical source, derived synopsis, independently produced critique, or a mutation request. Identify source-to-derivative visibility before allowing a shared or public output.

Do not begin by designing a universal event bus or memory schema.

### Phase 3 — Narrow tool-based integration

Implement the smallest useful set of domain-native operations, potentially through MCP servers or equivalent tool interfaces.

Test independent operation before integration.

In contract tests, attempt to launder private source material through summaries; confuse remembered historical approval with present authorization; hide challenges through partial retrieval; and route a scientific discrepancy into unauthorized SSDS execution.

### Phase 4 — Long-horizon cognitive coordination

Where useful, allow the General Memory Substrate to retain contextual references and obligations arising from domain interactions.

Require verification of current authoritative state when consequential actions depend on it.

### Phase 5 — Evaluate common implementation mechanisms

After real deployments, inspect actual duplication, recurring defects, maintenance costs, and interoperability constraints.

Extract common utilities only when demonstrably beneficial.

### Phase 6 — Reconsider architecture only when evidence requires it

A future common service or kernel is not forbidden.

It must, however, satisfy the same standards of independence, semantic adequacy, and complexity reduction as any other architectural change.

The burden of justification lies with consolidation, not with continued domain separation.

---

## 16. Open Architectural Questions

These questions remain deliberately unresolved:

1. Should general cognitive memory be strictly agent-local, optionally group-shared, or organized into multiple explicit scopes?
2. How should an agent distinguish historical memory from current external domain state during automatic retrieval?
3. Which source references require immutable revisions, and when is a current-state reference appropriate?
4. What minimum metadata are necessary for cross-system provenance and authorization?
5. Which domain operations should be exposed through tools, and which should remain internal?
6. How should long-running cross-system requests handle retries, cancellation, partial completion, and recovery?
7. Under which conditions should domains emit change notifications rather than rely on on-demand queries?
8. How should revoked access affect cached context and persistent agent memories?
9. What constitutes sufficient evidence that shared implementation actually reduces total complexity?
10. Which capabilities, if any, warrant a future common utility library?
11. How should multiple agents with different permissions coordinate shared tasks without merging their private cognitive histories?
12. How should the system audit cross-domain actions without maintaining a redundant globally authoritative event record?
13. How should SSDS's existing PEM governance and accepted project state map to external read-only or proposal interfaces without altering their semantics?
14. What minimum scientific and security tests are necessary before automated agents can issue consequential cross-domain requests?

15. What minimally sufficient lineage can an optional connector expose for permission-sensitive derived content without imposing global tracking infrastructure?
16. Who authorizes publication of scientific summaries whose constituent sources have different owners and restrictions?
17. How can review independence be honestly described when shared models, prompts, evidence and missing out-of-band influences limit provable ancestry?
18. Which retrieval intents require exact live owner state, which permit historical snapshots, and how are stale or partial indexes signaled?
19. What semantic contract prevents an agent from confusing an L0/L1 scientific compass with a ratified scientific decision?
20. Which dual-time distinctions must survive cross-domain exports, especially after corrections and delayed imports?
21. What happens when a useful scientific summary cannot prove it is safe to disclose, and how is unnecessary over-restriction challenged?
22. What minimal interoperability capability is actually needed before meaningful scientific collaboration can begin, and what evidence would justify more coupling?

None of these questions requires a shared memory kernel as a prerequisite.

---

## 17. Foundational Integration Requirements

The following requirements are proposed for independent review.

**INT-01 — Domain autonomy.** Each system must retain independent ownership of its canonical domain objects and semantic operations.

**INT-02 — Standalone functionality.** Core functions of each system must remain usable without either of the other two systems.

**INT-03 — Agent-centered memory.** The General Memory Substrate is responsible for experiential continuity and cross-context navigation, not for duplicating all domain records.

**INT-04 — Domain-native interfaces.** Integration must respect each recipient's declared operation and validation model.

**INT-05 — No mandatory shared kernel.** No common memory schema, event lifecycle, database, or runtime is required.

**INT-06 — Single canonical ownership.** Cross-system references and summaries must not create competing scientific or engineering authorities.

**INT-07 — Source verification.** Consequential reliance on domain knowledge must use sufficiently current and applicable domain-owned records.

**INT-08 — Explicit authorization.** Retrieved memory and tool access alone do not authorize scientific or engineering state changes.

**INT-09 — Permission preservation.** Cross-system operations must not bypass the source's access and confidentiality boundaries.

**INT-10 — Historical/contextual distinction.** A remembered past state must be distinguishable from a claim about current domain state.

**INT-11 — Failure isolation.** Optional connector failures must not compromise unrelated native domain operations.

**INT-12 — Recoverable exchange.** Consequential cross-system operations require identifiable outcomes and a suitable retry or reconciliation strategy.

**INT-13 — Independent evolution.** Domain-internal changes should not require coordinated modification of unrelated projects when external contracts remain unchanged.

**INT-14 — Selective reuse.** Common implementation mechanisms may be adopted only when their benefits and stable shared semantics are established.

**INT-15 — Non-authoritative external content.** Imported memory, evidence, and discussion text remain data unless independently authorized by the receiving domain's governing rules.

---

**INT-16 — Derived-output release boundary.** Reading a source, receiving a summary, or overseeing an agent does not automatically authorize retention or publication of content derived from that source.

**INT-17 — Qualified coverage and freshness.** Cross-domain retrieval must distinguish not-found-in-scope from globally absent and identify material temporal or source-coverage limitations.

**INT-18 — Source–projection separation.** Tiered orientations are navigational derivatives, never substitutes for domain-owned source, scientific judgment or accepted engineering authority.

**INT-19 — Scientific qualification portability.** Cross-domain representations must preserve materially relevant definitions, regimes, uncertainty and proposal/acceptance distinctions or declare their loss.

**INT-20 — Truth and independence are not consensus.** Shared agent outputs or common underlying sources cannot be counted as independent scientific evidence merely because multiple agents agree.

**INT-21 — No global ancestry requirement.** Material lineage and release must be assessed at authorized interfaces to the extent observable; absence of a universal trace is neither proof of safety nor justification to manufacture one.

**INT-22 — Historical temporal fidelity.** Consumers must not confuse retrospective assessment with what was known or recorded at an earlier time.

---

## 18. Principal Risks and Mitigations

| Risk | Architectural failure | Proposed response |
|---|---|---|
| Universal memory abstraction | Domain semantics become distorted or overconstrained | Keep independent domain models |
| Duplication of canonical state | Conflicting versions of scientific or engineering truth | Reference the owning source |
| Cognitive memory mistaken for authority | Unauthorized or obsolete decisions | Reverify governing domain state |
| Shared infrastructure dependency | One failure disables all systems | Standalone operation and optional connectors |
| Cross-project release coupling | Local features require global coordination | Narrow, versioned external contracts |
| Incompatible source revisions | Stale scientific or engineering interpretation | Revision-aware references and applicability checks |
| Unbounded memory replication | Storage growth, leakage, conflicting summaries | Prefer referential contextual memory |
| Multi-agent information leakage | Unauthorized data propagation | Agent and project permission scopes |
| Tool misuse or prompt injection | Retrieved text induces unauthorized actions | Treat source content as data and validate actions |
| Distributed partial failure | Duplicate, missing, or misleading external results | Identifiable requests, outcomes, and reconciliation |
| Premature shared-library extraction | Common utilities become domain-specific frameworks | Evidence-driven consolidation |
| No integration conventions | Ad hoc connectors become brittle | Minimal stable identity and messaging expectations |

---

The v0.2 proposal also recognizes: **derived-content disclosure** (read-authorized inputs reappear in broader outputs); **projection laundering** (narrative summaries appear authoritative); **false absence** (partial search gives an exhaustive answer); **temporal flattening** (retrospective corrections masquerade as past belief); **pseudo-independent review** (common-source agreement inflated into corroboration); and **accidental interface ontology** (a minimal envelope quietly becomes a universal state schema). Review should test these risks while challenging whether the proposed mitigations add excessive complexity.

---

## 19. Reviewer Questions

The General Memory Substrate developer should examine:

- Whether referential cognitive memory fits the intended event-driven memory model.
- Whether any proposed navigation or source-reference capability conflicts with its consolidation semantics.
- Whether external domain operations can remain optional without degrading core memory behavior.
- Whether privacy, source freshness, and agent-specific scopes are adequately addressed.
- Whether the proposal silently introduces task-orchestration responsibilities into memory itself.

The SSDS developer should examine:

- Whether the proposed integration preserves existing D1–D4 authority and deterministic execution controls.
- Whether PEM remains project-scoped, non-authoritative, and governed by its own accepted lifecycle.
- Whether external evidence and work-request interfaces can be provided without changing internal governance.
- Whether proposed cross-system interactions introduce invalid assumptions about SSDS run, branch, qualification, or acceptance state.
- Whether optional integration preserves standalone operation and adequate failure isolation.

The SCIRE developer should examine:

- Whether scientific argumentation can evolve independently of episodic memory.
- Whether stable external references are sufficient for most scientific evidence and orchestration use cases.
- Whether agent-memory summaries can safely preserve project continuity without becoming duplicate scientific authority.
- Whether scientific approval and external computation authorization are adequately separated.
- Whether any required interaction has been omitted from the minimal interoperability model.

All reviewers should challenge the fundamental separation if they can demonstrate a more coherent alternative that preserves the required domain semantics, reduces total complexity, and does not introduce unacceptable coordination costs.

---

## 20. Conclusion

The proposed architecture does not treat memory as a single universal subsystem.

Instead, it distinguishes the persistent experiences needed for agent cognition from the structured knowledge and governed state owned by specialized domains.

The General Memory Substrate supports long-horizon continuity and helps an agent navigate among research projects, engineering workflows, and other activities.

SCIRE preserves scientific arguments, evidence, questions, and discovery history under its own scientific semantics.

SSDS and PEM preserve governed engineering execution and evidence-backed project learning under their own authority and applicability rules.

Agents connect these capabilities through explicit, permission-checked, domain-native interfaces.

The result is a collection of independently useful systems that can cooperate without sharing a common kernel or becoming mutually dependent.

**Foundational architectural statement:**

> The agent remembers enough to maintain context and know where to look. The owning domain system determines what is currently known, justified, applicable, and authorized.

This document proposes that principle as the basis for future interoperability. It does not ratify any cross-project architectural change, mandate implementation, or supersede existing accepted SSDS or memory-substrate authority.

The next step is independent review by the respective system developers, followed by reconciliation of material concerns before any detailed integration workplan is accepted.
