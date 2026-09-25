# Monday Status column — settings, composer, and visual stress states (S17–S22, S09/S10/S15/S16 completion)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25.
All states captured live in the dedicated Chrome tab (session "Status Parity W4"); PNG screenshots saved beside this note.

## S02/S10 — hover states
- monday_S02_cell_hover.png: pointer over the empty Status cell (no visible hover chrome beyond cursor; hover affordance is minimal).
- monday_S10_option_hover.png: pointer over the Done option inside the open dropdown (multi-column grid at 40 labels).

## S09 — editor cancel behaviour (IMPORTANT DIFF)
- monday_S09_editor_cancel.png (dropdown open, saved values visible).
- Method: renamed L02 -> L02X in the editor, pressed Escape (editor closed), reopened editor AND the dropdown.
- Result: L02X was RETAINED in both the editor draft and the SAVED dropdown values — the rename committed without an explicit Apply click (commit on close/blur; Escape does not discard).
- Monday has no "Escape discards unapplied edits" model. Pipeline documents exactly that model in its helper text. Functional DIFF (see W6).

## S15 — label description
- Added description to L03 via row "..." menu -> "Add label description"; editor shows an 80-character limit counter ("0 /80"); Save commits inside the editor; column Apply persisted it.
- monday_S15_description_hover.png: dropdown open, pointer over the i-icon next to L03; tooltip shows the description text.

## S16 — deactivate / reactivate round-trip (unused label L04)
- Deactivate via row menu -> Apply: L04 disappears from the cell dropdown (39 options, no L04) — monday_S16_deactivated_view.png.
- In the editor the row remains listed (grayed, no visible "Inactive" caption text in Monday).
- Deactivated row menu offers "Reactivate label" (Monday wording; Pipeline uses "Activate label") plus Delete label. Reactivate -> Apply restored L04 (40 options again).

## S17 — column header menu
- monday_S17_settings_menu.png: Status header "..." menu open. Items: Column ID: color_mm7bcxvk, Settings, Filter, Sort, Collapse, Group by, Duplicate column, Add column to the right, Change column type, Save as managed column, Column extensions, Rename, Delete.

## S18 — Settings submenu + Customize Status column
- monday_S18_settings_submenu.png: Settings submenu with Customize Status column, Add column description, Set status notifications, Set column as required, Set column validation (tagged New), Restrict column editing, Restrict column view, Show/Hide column summary, Save column as a template.
- monday_S18_customize_status.png: "Status column settings" panel — "Add or edit labels (40/40)" (counter confirms the 40 max live) and the done-colors picker ("Choose which colors indicate that an item is completed").

## S19 — column summary
- Summary row was already enabled on this board; the settings item reads "Hide column summary" when shown and "Show column summary" when hidden (toggle wording captured).
- monday_S19_column_summary.png: board with the summary row visible under the item row.

## S20 — status box update composer
- With L01 applied, the cell shows a small + icon at its top-right (class add-status-note). Clicking it opens the "Write a status note" composer bound to L01 with a rich-text toolbar (B/I/U/S, lists, alignment) and an "Update" post button; an (i) info icon next to the title.
- monday_S20_status_box_composer.png: composer open. Closed via its X without posting (no update created).

## S21/S22 — long content and narrow-column truncation
- L05 renamed temporarily to "Very long status label name for truncation and overflow parity testing S21 S22", applied to the item, then restored to L05 after capture (board state reverted).
- monday_S21_long_content_cell.png: cell chip renders the long text; column initially wide enough to show most of it; chip color + text persist.
- monday_S22_narrow_truncation.png: after dragging the column right edge narrower, the chip truncates with an ellipsis ("long ...") and a "Resize Column" tooltip appears near the drag handle. Summary row mirrors the truncated chip.

## Automation notes (not user-facing parity)
- Cell dropdown opens via CDP real pointer click on the cell; AXPress on the cell button does not open it.
- Label rename edits commit on editor close even without Apply (S09 finding); color edits save immediately per prior session.
- Board state after session: L01 applied to test_item_on_monday; L03 has description "Test description for parity research S15"; L04 deactivated then reactivated; L05 restored; column width restored (~141px); 40 labels intact (incl. duplicate L10 and textless label).
