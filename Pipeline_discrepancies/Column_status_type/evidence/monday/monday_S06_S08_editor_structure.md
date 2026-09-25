# Monday Status column — Edit Labels editor (S06/S07/S08, TC-008)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25.

## Entry point
- Dropdown footer button "Edit Labels" (pencil icon) opens the inline label editor below the cell (same popover surface as the dropdown; not a modal).

## Editor structure (per label row)
- Color swatch button ("Click to edit color for label") — clicking opens the color picker.
- Text field for the label name (click to edit).
- "..." popup menu per label with exactly three items:
  1. Add label description
  2. Deactivate label
  3. Delete label
- The "Default Label" row (grey, empty) has NO "..." menu — it is locked and cannot be edited, recolored, or removed.

## Rows at first open
- Done, Working on it, Stuck (each with emoji icon on the swatch: green/orange/red), Default Label (grey, locked), "+ New label" button, "Apply" button.
- New rows are appended at the bottom of the list; a new row's text field is auto-focused.

## Apply / cancel behavior
- "Apply" commits all pending editor changes (adds, renames, colors, deletions) and returns the surface to the dropdown view (the Apply button position becomes the Edit Labels button again).
- Pressing Escape with a menu open closes the menu; pressing Escape with no menu open closes the whole editor (discard path — S09).

## New-label default styling (undocumented)
- New labels get a color swatch with a default emoji icon; new-label chips in the editor show a colored square with an emoji glyph.
