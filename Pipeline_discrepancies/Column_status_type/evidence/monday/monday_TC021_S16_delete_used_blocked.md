# Monday Status column — used-label delete blocked (S16, TC-020/TC-021)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25.

## Setup
- Label L01 was applied to the item's Status cell (cell chip purple "L01"), then the Edit Labels editor was opened and the L01 row's "..." menu opened.

## Finding (TC-021)
- The "..." menu of a USED label still shows all three items: Add label description / Deactivate label / Delete label.
- Clicking "Delete label" on the in-use label does NOT delete it; Monday shows an inline error: "You can't delete a label while in use".
- This matches the docs model (used labels cannot be deleted, only deactivated) and adds the exact error wording, which the docs do not include.

## Unused-label delete (TC-018/TC-020 context)
- The same three-item menu appears for unused labels; "Delete label" is expected to remove them (not exercised to destruction to preserve the 40-label capacity state for Pipeline-side comparison).
- The "Default Label" row has no "..." menu at all (cannot be deleted or deactivated).
