# Workplans

This index lists the coordination records in `workplans/`. It routes to the documents and is not itself authority: each document states its own status. As of 2 November 2026 no SCIRE scientific semantics or architecture is accepted-current.

## Lifecycle

- `active/` holds records whose obligations are still open, including superseded revisions that open review packages still cite.
- `archive/` holds records that are complete, or whose remaining obligations an accepted successor owns.
- Review packages bind inputs by file name and SHA-256, so files are not renamed or edited in place. A revision is a new file.

## Active records

| File | Kind | Note |
| --- | --- | --- |
| `SCIRE_Conceptual_Proposal_v0.1.md` | Proposal | Initial scientific and architectural concept, SHA-256 `bd84fea4…6e960` |
| `SCIRE_Conceptual_Proposal_v0.2.md` | Proposal | UPMS-informed revision of v0.1, SHA-256 `3e71ebb3…985bc`; reviewed, superseded by v0.3 |
| `SCIRE_Conceptual_Proposal_v0.3.md` | Proposal, review candidate | Consolidated revision under owner decisions D-A to D-D and the review findings, SHA-256 `02c5ece2…211459`; open for independent (different-family) review |
| `Agent_Centered_Memory_and_Domain_Interoperability_Proposal_v0.1.md` | Proposal | Initial UPMS / SCIRE / SSDS integration concept, SHA-256 `eb9b17ac…8755c37` |
| `Agent_Centered_Memory_and_Domain_Interoperability_Proposal_v0.2.md` | Proposal | UPMS-informed revision of v0.1, SHA-256 `634d4e8a…31c5e`; reviewed, superseded by `Memory_and_Domain_Interoperability_Proposal_v0.3.md` |
| `Memory_and_Domain_Interoperability_Proposal_v0.3.md` | Proposal, review candidate | Consolidated revision under D-A to D-D; renamed because UPMS serves an agent or a team, not only an agent; SHA-256 `b4a594ae…64c916`; open for independent review |
| `SCIRE_Integration_v0.2_Independent_Concept_Review_Handoff.md` | Review request | Requests an independent concept-level review of both v0.2 proposals |
| `SCIRE_Integration_v0.2_Independent_Concept_Review.md` | Review record | Claude (Opus 5.5) review of both v0.2 proposals: SUBSTANTIAL REDESIGN, Serious Challenges SC-A and SC-B, findings F-01–F-20; independence limited (proposal authorship unknown, shared UPMS ancestry) |
| `SCIRE_v0.3_Independent_Concept_Review_Handoff.md` | Review request | Requests an independent (ChatGPT) concept-level review of both v0.3 proposals, binding them by SHA-256 |
| `SCIRE_v0.3_Independent_Concept_Review.md` | Review record | Codex (OpenAI-family) review of both bound v0.3 proposals: NO-PASS / SERIOUS CHALLENGE; SC-31–SC-33 and findings V3-01–V3-13; supports the core direction but requires revisions; no ratification or implementation qualification |
