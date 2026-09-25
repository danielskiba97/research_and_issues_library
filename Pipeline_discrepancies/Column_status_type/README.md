# Status Column Type — Monday vs Pipeline Parity Research

**Feature:** Status column type
**Run:** adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644 (research-only, no source amendments)
**Date:** 2026-09-25

## References

| | Monday | Pipeline |
|---|---|---|
| Board | essentials_column_types_board_on_monday (18431468439) | essentials_column_types_board_on_pipeline (board_8bl8zfas7tavq) |
| Column | color_mm7bcxvk | saxfuhjmdkkbk |
| Test item | test_item_on_monday (13065765942) | test_item_on_pipeline |
| Documentation | https://support.monday.com/hc/en-us/articles/360001269685-The-Status-column | — (live product only) |

## What was tested

- **States examined:** 22 (S01–S22): empty cell, hover, dropdown open/selected/reopen, editor structure/cancel, capacity stress (40/40+1), empty-text save, validation errors, description hover, deactivation, settings menus, customize panel, column summary, status-box composer, long content, narrow truncation.
- **Test cases executed:** 40 (TC-001–TC-040) covering standard, empty, long, capacity boundaries (39/40/41), empty/duplicate saves, settings open/save/cancel/reopen, state transitions, keyboard/mouse variations, and visual stress.
- **Discrepancies found:** 9 (D-001–D-009), each with its own file under [discrepancies/](discrepancies/).

## Key discrepancies (summary)

| D-ID | Area | Monday | Pipeline |
|------|------|--------|----------|
| D-001 | Label capacity | "+ New label" removed at 40 | 41st label created & persisted; button disabled after |
| D-002 | Empty-text label | Saved silently | Blocked with validation message |
| D-003 | Duplicate names | Allowed | Blocked with validation message |
| D-004 | Used-label delete | Enabled → post-click error | Disabled control + tooltip |
| D-005 | Editor Escape | Retains unapplied edits | Discards unapplied edits |
| D-006 | Default Label lock | Fully locked | Only colour swatch disabled |
| D-007 | Dropdown affordances | None | Helper text + (selected) marker |
| D-008 | Resize handle tooltip | "Resize Column" tooltip | None |
| D-009 | Editor structure | No reorder controls | Reorder handles + Move up/Move down + helper text |

## Important edge cases tested

- 40-label capacity boundary (documented max confirmed live on both products)
- Empty-text label saves (Monday: accepted; Pipeline: blocked)
- Duplicate label names (Monday: allowed; Pipeline: blocked)
- Used-label deletion (both block; different affordance models)
- Deactivate/reactivate round-trip (applied value survives on both)
- Long-content and narrow-column truncation
- Editor cancel semantics (opposite discard models)

## Blocked tests

- Monday 41st-label creation attempt: blocked by UI (affordance removed) — recorded as finding D-001 rather than a test failure.
- Deeper keyboard traversal inside dropdown editors: not exhaustively exercised; recorded as an unknown in research records.

## AI exclusion

No Monday AI functionality was tested or documented, per task scope (section 3 of the task specification).

## Prior-run independence

All findings were independently rediscovered this run via live computer-use sessions. No previous-run evidence was used.

## Research status

**COMPLETE** — evidence-backed, packaged, uploaded. See [board_claims/board_claims.md](board_claims/board_claims.md) for board ownership and [research_ledger/master_ledger.md](research_ledger/master_ledger.md) for the full ledger.
