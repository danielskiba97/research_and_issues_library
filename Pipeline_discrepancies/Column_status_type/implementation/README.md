# Implementation — Column Status Type (Pipeline amendments A-001..A-009)

Additive implementation area for run adaptive_7b2673742dce428e538e1a58d633e54d9841e250b2445ee037c7ded108ec4e4d. The original research package content (README, ledger, discrepancies, evidence, board_claims) is preserved untouched.

## Contents
- `implementation_ledger.md` — per-D-ID implementation/verification/regression tracking.
- `amendments/A-001.md` … `A-009.md` — one amendment note per CONFIRMED discrepancy: root cause, files, approach, expected result, shared-component impact, verification required, and replay result.

## Summary
All 9 CONFIRMED D-IDs were implemented on the Pipeline working tree (branch main, HEAD e104f32, uncommitted — committed state remains with the product repo owner):
- A-001 hide + New label at 40 saved user labels (capacity enforced pre-creation).
- A-002 allow empty-text Status label saves (blank chips).
- A-003 allow duplicate label names (ID-based uniqueness; dropdown-only uniqueness retained in lib/model.ts).
- A-004 enable delete for used labels with post-click inline error.
- A-005 retain unapplied editor edits on Escape (draft cache).
- A-006 fully lock the Default Label row.
- A-007 remove dropdown helper text and (selected) marker.
- A-008 add "Resize Column" title on column splitters.
- A-009 remove editor reorder handles/Move items/helper text.

Verification: per-D-ID checks C4-d001..C4-d009 recorded; automated suite 507 pass / 0 fail; typecheck and build clean; lint has 8 pre-existing errors unrelated to the amendments.
