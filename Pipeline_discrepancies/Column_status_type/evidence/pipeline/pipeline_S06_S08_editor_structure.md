# Pipeline Status column — label editor structure (S06/S08, TC-008..TC-012, TC-037)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25.

## Entry point
- Cell dropdown -> "Edit Labels" footer button opens the editor popover below the cell (same flow as Monday).

## Editor anatomy (per label row)
- Reorder handle: "Reorder label N; use Up or Down arrow" with Help "Drag to reorder; use arrow keys to move" (keyboard-accessible reorder).
- Color swatch: pop up button "Color for label N", Help shows the hex (e.g. #00c875).
- Name: text field "Label N name" (settable).
- Options: pop up button "Options for label N" -> menu with: Add label description (pop up), Deactivate label / Activate label, Move up, Move down, Delete label.
- Footer: "+ New label" button and "Apply" button.
- Helper line: "Existing label colors save immediately. Apply saves other edits; Escape discards unapplied edits."

## Default Label row behavior (DIFF vs Monday)
- Pipeline: color swatch DISABLED, but the NAME FIELD IS EDITABLE and the options menu IS PRESENT.
- Monday: Default Label row is locked entirely (no menu, no rename).

## Save model (S08)
- Color changes save immediately (per helper text); structural edits (add/rename/delete/deactivate) require Apply; Escape discards unapplied edits.
- One Apply committed the full 41-label set (see pipeline_S11_S12_capacity_stress.md); after Apply the editor closes back to the dropdown view.

## Documented vs Monday
- Pipeline documents its save model in the helper text; Monday exposes no equivalent helper.
- Pipeline adds keyboard reorder (handles + arrow keys) and explicit Move up / Move down menu items; Monday relies on drag without documented keyboard affordance.
- Pipeline exposes "Add label description" inside the editor options menu.
