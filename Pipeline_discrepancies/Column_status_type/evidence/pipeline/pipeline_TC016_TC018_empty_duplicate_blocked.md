# Pipeline Status column — empty and duplicate label names blocked (S13/S14, TC-016/017/018)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25.

## TC-018 duplicate names (renamed L36 -> "L35", Apply)
- Apply is BLOCKED. Inline message below the editor: "Labels must be unique and nonempty. Your label draft is kept." plus a "Dismiss message" affordance.
- Both "L35" rows remain in the editor; the draft (including the conflicting rename) is retained for correction.
- Monday equivalent: duplicates are ACCEPTED silently (two "L10" labels coexist in the 40-label set). DIFF.

## TC-016/TC-017 empty label name (cleared label 41's name, Apply)
- Apply is BLOCKED with the same message: "Labels must be unique and nonempty. Your label draft is kept."
- Additionally the native HTML validation bubble "Please fill out this field." appears on the cleared name field.
- The empty-name draft is kept (field remains empty, editor stays open). Monday equivalent: empty-text labels SAVE with no validation (textless chip appears in the dropdown). DIFF.
- Note: with 41 labels on the board, "Empty" remains a valid selectable dropdown option and the item cell shows a grey "no status" state — the blocked empty-name rule applies to label definitions, not to the empty cell value.

## State note
- The 41-label set (with L36 restored) was left saved on the board intentionally as the over-capacity state for the capacity discrepancy (see pipeline_S11_S12_capacity_stress.md).
