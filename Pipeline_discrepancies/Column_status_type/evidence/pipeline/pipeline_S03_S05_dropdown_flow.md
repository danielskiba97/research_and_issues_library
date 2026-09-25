# Pipeline Status column — cell dropdown flow (S03/S04/S05, TC-002..TC-007, TC-028)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25.

## Setup
- Board: essentials_column_types_board_on_pipeline (board_8bl8zfas7tavq), localhost:5188, item test_item_on_pipeline, Status column saxfuhjmdkkbk.
- Board claimed for testing per board-claim rule (board_claims.md).

## S03 — dropdown open on empty cell
- Clicking the empty Status cell opens a popover list below the cell with a helper line: "Choose a status to save immediately. Escape closes without changing it."
- Initial 5 labels: Done (#00c875), Working on it (#fdab3d), Stuck (#e2445c), Default Label (#c4c4c4, isDefault), zz_very_long_status_label_name_for_truncation_testing_purposes (#037f4c).
- The "Empty" option is marked "(selected)" in the accessibility tree when the cell is empty.
- Footer button "Edit Labels" present (same entry point as Monday).
- DIFF vs Monday: Monday shows no selected marker on the grey clear option; Pipeline marks it selected.

## S04/S05 — selection and reopen
- Clicking a label (e.g. Done) saves immediately and renders a colored chip in the cell; no separate confirm step (same immediate-save model as Monday).
- Summary row updates instantly ("No status: 1/1 (100%)" -> "<Label>: 1/1 (100%)").
- Reopening the dropdown shows the same list; the current value carries the "(selected)" AX marker; a checkmark is not visually confirmed.
- Selecting "Empty" clears the cell (grey, summary "No status: 1/1 (100%)") — same as Monday's clear option.
- Helper text documents Escape behavior, which Monday does not expose.

## Keyboard (TC-028, partial)
- The cell is exposed as a pop up button; automation opened it via AX click. Dedicated keyboard traversal of the list (Arrow keys within the popover) was not separately exercised; no blocker observed.
