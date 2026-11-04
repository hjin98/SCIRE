# SCIRE Semantic Evolution History

This file preserves concise reasons for material semantic changes to SCIRE that ordinary Git chronology cannot explain economically. It is historical context, not current authority. Current normative truth lives in the accepted owners; until SCIRE's scientific semantics and architecture are accepted, the records in `workplans/` carry the design lineage.

Each entry names the previous semantics, the replacement, the triggering evidence or rationale, the affected surfaces and the disposition.

---

## 2026-11-02 — System boundary: separation by responsibility (owner decision D-A)

- **Previous:** the v0.2 integration proposal separated UPMS from SCIRE and SSDS as "agent-centered" memory versus "domain-centered" project knowledge.
- **Replacement:** separation by responsibility for the content. UPMS holds an agent's or team's general contextual record and logistics; SCIRE holds scientific discussion and argument. The number of users and private versus shared play no part.
- **Trigger:** review challenge SC-A (`workplans/active/SCIRE_Integration_v0.2_Independent_Concept_Review.md`): UPMS Candidate 4.1 describes itself as team project memory, which the "agent-centered" criterion could not place. Decided by the product owner in conversation.
- **Affected:** `Memory_and_Domain_Interoperability_Proposal_v0.3.md` §0, §3 and INT-01; `SCIRE_Conceptual_Proposal_v0.3.md` §2.1.
- **Disposition:** owner decision; the v0.3 texts that apply it are unratified proposals.

## 2026-11-02 — SCIRE is the proposal layer (owner decision D-B)

- **Previous:** SCIRE v0.2 had SCIRE record "accepted scientific formulations" and "ratification of a scientific conclusion for governed use".
- **Replacement:** SCIRE is the proposal layer. SSDS owns the decided model and its implementations; SCIRE's outputs are SSDS's inputs. SCIRE's own decisions are inquiry decisions only.
- **Trigger:** review challenge SC-B: two owners of accepted scientific meaning for governed use. Decided by the product owner in conversation.
- **Affected:** `SCIRE_Conceptual_Proposal_v0.3.md` §2.2, §10 and SCIRE-10; `Memory_and_Domain_Interoperability_Proposal_v0.3.md` §3.3, §6.2 and INT-02.
- **Disposition:** owner decision; the v0.3 texts that apply it are unratified proposals.

## 2026-11-02 — The PI finalizes; SSDS builds on request (owner decision D-C)

- **Previous:** v0.3 as first issued had SCIRE send investigation requests, model proposals and challenges to SSDS, with SSDS "deciding" them; it left open what ends scientific work that never reaches SSDS.
- **Replacement:** SCIRE's end product is a scientific model finalized by the PI and backed by arguments. The PI decides what goes to SSDS to be built. A transfer hands over the model and never requests a build. SSDS executes only the implementation a user requests. SCIRE never executes.
- **Trigger:** open question 1 of the first v0.3 interoperability text. Decided by the product owner in conversation.
- **Affected:** `SCIRE_Conceptual_Proposal_v0.3.md` §0, §2.2, §4.2, §10.1, SCIRE-10; `Memory_and_Domain_Interoperability_Proposal_v0.3.md` §3.3, §6.2, §8.2–§8.4, INT-02.
- **Disposition:** owner decision; applied by amending both v0.3 texts before any review bound them.

## 2026-11-02 — Independent systems; links for traceability (owner decision D-D)

- **Previous:** integrations were "optional connectors" whose operations were described as requests between systems.
- **Replacement:** SCIRE, SSDS and their projects are independent, stand-alone systems with their own governing authorities. Cross-references are citation-like links; automated transfer of models and feedback is allowed. Both serve traceability and developmental data flow and are never operation requirements.
- **Trigger:** owner clarification in conversation.
- **Affected:** `SCIRE_Conceptual_Proposal_v0.3.md` §0, §2.5, §10, SCIRE-14; `Memory_and_Domain_Interoperability_Proposal_v0.3.md` §0, §4, §6.2, INT-04.
- **Disposition:** owner decision; applied as above.

## 2026-11-02 — Review framings D-E to D-J approved; v0.4 repairs (proposed)

- **Previous:** v0.3 treated an unresolved link as never limiting anything; made the finalized model the end state of all scientific work; counted acknowledgement and deferral as objection dispositions; retained unknown-lineage content wherever the writer could write; confirmed only with held-out data; banned machine-to-machine assessment.
- **Replacement:** the owner approved, as the framing for v0.4, the six recommendations answering the Codex review's open decisions: availability versus eligibility (D-E); outcomes other than finalized models (D-F); scoped multi-PI authority (D-G); scoped overrides that never resolve (D-H); retention, metadata and revocation owned by source owners (D-I); smallest first product with owner-set limits (D-J). v0.4 also proposes: handling versus resolution of objections; a basis statement before consequential use; use history with an inference-specific warrant; separate origin, qualification and usability; target-relative comparability; retention checked before storing, trusted carried constraints and protected metadata.
- **Trigger:** `workplans/active/SCIRE_v0.3_Independent_Concept_Review.md` (Codex; NO-PASS, SC-31–SC-33, V3-01–V3-13). The owner answered "Yes, draft v0.4" to drafting with the recommended framings.
- **Affected:** `SCIRE_Conceptual_Proposal_v0.4.md` and `Memory_and_Domain_Interoperability_Proposal_v0.4.md`, with change maps in their Appendix A.
- **Disposition:** D-E to D-J are owner-approved framings; the v0.4 texts are unratified proposals pending independent re-review.

## 2026-11-02 — SCIRE v0.3 conceptual model (proposed)

- **Previous:** argument as the primitive; a 19-type vocabulary; a separate Scientific Discrepancy Case type; bitemporal history; persisted L0/L1/L2 overviews; progressive formalization without triggers.
- **Replacement (proposed):** the open question as the unit; six record kinds; evidence links that are conditional and comparative, with use-role and production class; discrepancy as a question kind with a comparability record; append-only history with observation times and decision intervals; a compass built from queries; demand-driven formalization; release floors.
- **Trigger:** review findings F-03 to F-20. The owner delegated their disposition to the author's discretion.
- **Affected:** `SCIRE_Conceptual_Proposal_v0.3.md` (whole); change map in its Appendix A.
- **Disposition:** proposed, unratified; written by the same model family as the review, so it needs a different-family review.

## 2026-11-02 — Memory moves to UPMS; SCIRE becomes its front end (UPMS owner decisions D-20 to D-25; proposed)

- **Previous:**
  - SCIRE was an independent system that held scientific discussion and argument itself.
  - It was separated from UPMS by responsibility (D-A) and linked to UPMS and SSDS only by citation-like links (D-D).
  - It kept its own read, retain and disclose floors.
- **Replacement (proposed):**
  - UPMS becomes one theory–evidence memory that stores both evidence and theory.
  - SCIRE becomes the front end that owns the actual discussion process: meetings, facilitation, the secretary, inquiry policy (objection rule, basis statements, finalization, multi-PI authority, overrides) and the model hand-off to SSDS. UPMS is its memory engine.
  - SSDS stays outside. D-B, D-C and D-E to D-J stand; D-E now applies only to SSDS links.
  - SCIRE's confidentiality floors are replaced by UPMS's simplified scopes and an opt-in strict profile.
  - Time-based retention gives way to recommended-retention flags.
- **Trigger:** the owner's conversation of 2 November 2026, following the same-family re-review of v0.4.
- **Affected:**
  - The SCIRE v0.4 proposal and the interoperability v0.4 proposal become frozen inputs.
  - The next SCIRE document is a front-end specification.
  - The re-review findings are carried or dissolved as mapped in the UPMS proposal (§13.2).
  - The governing text is `universal-persistent-memory-substrate/workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md`.
- **Disposition:**
  - The owner decisions partly reverse D-A (as to memory) and the UPMS–SCIRE half of D-D.
  - The UPMS proposal applying them is unreviewed and unaccepted.

## 2026-11-03 — Mathematics and tools extension (proposed)

- **Previous:** SCIRE v0.4 covered discussion of empirical and theoretical claims, with no mathematical notation, derivation workflow or tools.
- **Replacement (proposed, unreviewed):** SCIRE is extended, rather than joined by a second front end, to support:
  - LaTeX in discussion;
  - derivations as records;
  - registered, sandboxed tools whose runs are recorded in UPMS as relative evidence;
  - agent derivation and checking, with human inspection and end-to-end verification by designated verifiers;
  - an inspection brief that ranks objective signals first and never omits a mandatory item.

  Pure mathematics with Lean follows later.
- **Trigger:** UPMS owner decisions D-57 to D-62 (3 November 2026).
- **Affected:** `workplans/active/SCIRE_Mathematics_and_Tools_Extension_Proposal_v0.1.md`; `workplans/README.md`.
- **Disposition:** proposal only. SCIRE v0.4 is unchanged.

## 2026-11-03 — Mathematics and tools extension v0.2 (proposed)

- **Previous:** v0.1 let the derivation agent assess its own steps and judge its own renderings, cited UPMS D-52 for tool registration, called full verification a property of the result, and proposed a seeded-error study without a primary outcome, blinding or a frozen catalogue.
- **Replacement (proposed, unreviewed):** agents never record inspections or clear their own work from the brief (UPMS D-73); a same-family checking agent is allowed and labeled (D-78); tools are registered by an operator act (D-77); artifacts are never executed by UPMS; "verified in full" is a property of the derivation, shown with premises and conditions; the brief lists carried conditions, discharges and self-assessed steps; deterministic tests are separated from a study registered before any data.
- **Trigger:** a same-family review of the mathematics package by Claude Fable 5.1 (UPMS `UPMS_Mathematics_Package_Same_Family_Review.md`), and UPMS owner decisions D-71 to D-78.
- **Affected:** `workplans/active/SCIRE_Mathematics_and_Tools_Extension_Proposal_v0.2.md`; `workplans/README.md`.
- **Disposition:** proposal only. v0.1 is unchanged.
