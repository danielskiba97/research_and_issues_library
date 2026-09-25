# Pipeline Status column — used-label delete blocked / deactivate round-trip (S16, TC-020/TC-021)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25.

## Setup
- L01 was applied to test_item_on_pipeline (cell chip blue "L01", summary "L01: 1/1 (100%)"), then the Edit Labels editor was opened and L01's options menu ("Options for label 6") expanded.

## TC-021 delete a USED label
- The options menu shows: Add label description / Deactivate label / Move up / Move down / Delete label.
- "Delete label" is DISABLED with tooltip: "This label is in use. Make it inactive instead."
- DIFF vs Monday: Monday keeps Delete enabled and shows an inline error AFTER clicking ("You can't delete a label while in use"); Pipeline prevents the click entirely and explains why via the disabled-state tooltip.

## TC-020 deactivate / reactivate round-trip
- Clicking "Deactivate label" flips the row in place: an "Inactive" caption appears under the label name and the menu item becomes "Activate label".
- The applied value SURVIVES deactivation: the item cell still displays the L01 chip and the summary still counts "L01: 1/1 (100%)" while deactivated.
- Clicking "Activate label" restores the row (caption gone, menu back to "Deactivate label"). State restored after the test.

## Extra affordances in the menu (DIFF vs Monday)
- "Add label description" is offered inside the editor options menu (Monday adds descriptions from the same menu but documents the i-icon hover).
- "Move up" / "Move down" give explicit keyboard-free reordering in addition to the drag handle.
