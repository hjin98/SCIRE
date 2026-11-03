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

## 2026-11-02 — SCIRE v0.3 conceptual model (proposed)

- **Previous:** argument as the primitive; a 19-type vocabulary; a separate Scientific Discrepancy Case type; bitemporal history; persisted L0/L1/L2 overviews; progressive formalization without triggers.
- **Replacement (proposed):** the open question as the unit; six record kinds; evidence links that are conditional and comparative, with use-role and production class; discrepancy as a question kind with a comparability record; append-only history with observation times and decision intervals; a compass built from queries; demand-driven formalization; release floors.
- **Trigger:** review findings F-03 to F-20. The owner delegated their disposition to the author's discretion.
- **Affected:** `SCIRE_Conceptual_Proposal_v0.3.md` (whole); change map in its Appendix A.
- **Disposition:** proposed, unratified; written by the same model family as the review, so it needs a different-family review.
