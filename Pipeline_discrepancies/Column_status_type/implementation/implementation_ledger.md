# IMPLEMENTATION MASTER LEDGER — Status Column Type

Implementation run: adaptive_7b2673742dce428e538e1a58d633e54d9841e250b2445ee037c7ded108ec4e4d
Baseline: v1 b01e1fcfe75611a6452eeaf285582f791ebfa0d94b9571b4472d91f2adcd202b (approved; recovery baseline v2 431340484ff733f7c8559bc227d5bff2a5b8bb6bb0a5c718cdb8b3c599647a38 also approved)
Started: 2026-09-26
Research source: ../README.md + ../research_ledger/master_ledger.md (preserved, untouched)

Reproduction statuses (fresh, 2026-09-26): all 9 D-IDs CONFIRMED on the current Pipeline working tree before implementation. Evidence: Pipeline UI computer-use session (13 screenshots + AX records).

| D-ID | Reproduction | Implementation | Amendment | Files/Components | Notes | Affected tests | Pipeline-after evidence | Verification | Regression | Commit/PR |
|------|--------------|----------------|-----------|------------------|-------|----------------|-------------------------|--------------|------------|-----------|
| D-001 | CONFIRMED | DONE | A-001 | pipeline-status-labels.tsx | Hide + New label at 40 saved (Monday affordance-removal model) | status-label-editor.test.ts (cap), capacity tests | after_A001_editor_41rows_no_add.png | PASS (C4-d001) | pending M3 | pending M4 |
| D-002 | CONFIRMED | DONE | A-002 | lib/column-configuration.ts (status-only) | Allow empty-text Status label save (Monday parity) | status-unnamed-labels.test.ts | after_A003_genuine_duplicate_saved.png (blank state pre-rename) | PASS (C4-d002) | pending M3 | pending M4 |
| D-003 | CONFIRMED | DONE | A-003 | lib/model.ts (dropdown-only), lib/column-configuration.ts | Allow duplicate label names; ID binding preserves cells | duplicate-save tests | after_A003_genuine_duplicate_saved.png | PASS (C4-d003 v2 replay) | pending M3 | pending M4 |
| D-004 | CONFIRMED | DONE | A-004 | pipeline-status-labels.tsx | Delete enabled for used labels; post-click inline error (Monday text) | delete-used tests | computer-use session | PASS (C4-d004) | pending M3 | pending M4 |
| D-005 | CONFIRMED | DONE | A-005 | pipeline-status-labels.tsx, pipeline-status-cell.tsx | Escape retains unapplied edits (module-level draft cache) | escape-retains tests | computer-use session | PASS (C4-d005) | pending M3 | pending M4 |
| D-006 | CONFIRMED | DONE | A-006 | pipeline-status-labels.tsx | Fully lock Default Label row (no menu, no editing) | status-label-editor.test.ts | after_A006_fresh_ax_locked.png | PASS (C4-d006) | pending M3 | pending M4 |
| D-007 | CONFIRMED | DONE | A-007 | pipeline-status-cell.tsx | Remove dropdown helper text + (selected) AX marker | dropdown-parity tests | computer-use session | PASS (C4-d007) | pending M3 | pending M4 |
| D-008 | CONFIRMED | DONE | A-008 | pipeline-column-resize.tsx | Add "Resize Column" tooltip on splitter | resize-tooltip tests | after_A008_splitter_title.png | PASS (C4-d008 v2 replay) | pending M3 | pending M4 |
| D-009 | CONFIRMED | DONE | A-009 | pipeline-status-labels.tsx, pipeline-status-cell.tsx | Remove reorder handles, Move up/Move down, editor helper text | status-label-editor.test.ts, column-parity tests | computer-use session | PASS (C4-d009) | pending M3 | pending M4 |

## Verification addendum (2026-09-26, A-006)

A-006 was verified with two independent methods:
1. **AX-tree** (`Options for label 4` text still present in the AX tree after the code change). Investigation showed this is an **accessibility-tree caching artifact** of the automation AX layer — the live DOM (inspected via in-page JS) confirms `hasMenuTrigger: false` (the Popover.Trigger is not rendered for the Default Label row) and `nameInputDisabled: true`.
2. **Live DOM inspection** (browser evaluate) — authoritative for A-006.

The AX text likely originates from the aria-label of the previously rendered trigger cached by the AX snapshot; the DOM-level source of truth was used to confirm the amendment. Recorded per feedback §19 evidence chain requirements.

## Verification addendum 2 (2026-09-26, A-001 boundary semantics)

A-001 UI verification at the leaked 41-label state: "+ New label" is hidden when `userCount>=draftLimit` (Monday model — affordance removed). The research board's 41st label was created by the prior run's leak; A-001 prevents a NEW 41st creation when 40 user labels are saved. The over-cap data state is intentionally preserved as research evidence (feedback §12: original evidence stays available). Boundary test evidence (40→41 creation blocked) is verified in the automated suite and will be re-verified at the clean 40-label state during M3 verification.

## Verification addendum 3 (2026-09-26, stale-server replay for A-003/A-008)

The dev server on port 5188 had been running since before the A-003 amendment; its server-side model code was stale, so the first genuine UI duplicate save was rejected ("Labels must be unique and nonempty.") while the client draft was retained. Honest handling:
- The failed attempt is preserved (draft-retention observation, invalid D-010 screenshot discarded).
- The stale server (PID 44152, started Sep 24 21:11) was killed and relaunched via `npm run dev` (fresh vite instance).
- The genuine duplicate save was replayed and PASSED end to end: server-side board state shows two independent L03 labels (separate IDs/colors); the item picker renders both chips with no dedupe.
- Potential D-010 (duplicate names render once) is therefore NOT reproduced on the amended Pipeline; Monday parity holds. The invalid screenshot was removed and replaced by the honest capture after the real duplicate existed.

## Suite state (2026-09-26)

- `npm test`: 507 pass / 0 fail
- `tsc --noEmit`: OK
- `npm run build`: OK
- `npm run lint`: 8 pre-existing errors (7 in tests/status-unnamed-labels.test.ts, 1 unused import in components/pipeline-board.tsx) — left untouched per §11 (no unrelated cleanup).
