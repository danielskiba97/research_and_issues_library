# Monday Status column — empty-text label save (S13, TC-016/TC-017)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25. Guidance-flagged (undocumented).

## Test
- In the Edit Labels editor, clicked "+ New label", left the new label's text field EMPTY, clicked "Apply" immediately.

## Result: SAVED WITHOUT VALIDATION
- No error, no validation message, no blocked save. The editor closed via Apply and the dropdown immediately showed a FIFTH option: a solid blue chip with NO text (AX list: two "Empty" values — ID 5 default grey empty, ID 3 the new textless label).
- The textless label behaves as a selectable value: it renders as a colored chip with no label text in the dropdown grid.
- Discrepancy-relevant: neither the Monday support article nor the in-product editor prevents empty label names; the product silently accepts them.
