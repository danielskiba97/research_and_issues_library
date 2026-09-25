# Monday Status column — label capacity stress to 40 and beyond (S11/S12, TC-013/014/015/040)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25. THE core guidance-ask test.

## Method
- Interactive UI stress via the Edit Labels editor: click "+ New label" -> type name (L01..L34) -> repeat. All adds committed with one "Apply" click.
- Labels counted from the accessibility tree (each row exposes "container <name>").

## Result: 40-label hard ceiling CONFIRMED
- Final saved set: Done, Working on it, Stuck, Default Label (grey, locked), 1 empty-text label (blue, see TC-016), L01..L34 including one duplicate L10 = exactly 40 label definitions.
- At 40 labels the "+ New label" button DISAPPEARS from the editor entirely. There is no error, no disabled button, no counter — the affordance is simply gone. The 41st label cannot be attempted through the UI (S12: blocked by affordance removal, not by a validation message).
- This matches the docs value ("up to 40 status labels") and adds the UI detail the docs omit: how the limit manifests (button removal).

## At-capacity UI behaviors (TC-040, undocumented)
- The cell dropdown with 40 labels switches from a vertical list to a MULTI-COLUMN GRID (6+ columns visible) with its own horizontal scrollbar inside the popover. Labels remain full chips with color + emoji icon.
- The editor likewise renders labels in a multi-column grid with a horizontal scrollbar and keeps "Apply" pinned at the bottom.
- Dropdown still lists every label; selection of a custom label (L01) works normally; AX exposes the full ordered list (Done, Working on it, Stuck, Empty x2, L01..L34) with stable label IDs (Done=1, Working on it=0, Stuck=2, empty default=5, empty-text=3, L01=4, L02=6, ..., L34=160).

## Related observations during the stress
- Duplicate label names are accepted (two independent rows both named "L10", IDs 14 and 15) — no uniqueness validation (TC-018).
- The editor occasionally re-renders/virtualizes mid-edit (AX indices reset); typing continues into the focused field without data loss.
