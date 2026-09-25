# Monday Status column — dropdown flow (S03/S04/S05, TC-002/003/005/006)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644
Environment: live monday.com board 18431468439, column color_mm7bcxvk, item 13065765942 (test_item_on_monday), session date 2026-09-25 (America/Toronto). Interactive browser session (Chrome tab "Status Parity Research"), evidence captured via accessibility tree + screenshots in the run transcript.

## S03 — empty cell dropdown (TC-002)
- Trigger: keyboard navigation onto the Status cell (name cell -> Escape -> ArrowRight -> Enter). Direct mouse-click emulation on the cell wrapper did NOT open the dropdown; Monday requires real pointer interaction or keyboard cell focus. When keyboard-focused, the cell renders as an ARIA button (ID row-pulse-...-focus-color_mm7bcxvk-) and Enter opens the dropdown.
- Dropdown contents (fresh board, default column): Done (green), Working on it (orange), Stuck (red), an unnamed grey option (= default/empty), and an "Edit Labels" affordance with pencil icon.
- The dropdown opens directly below the cell with a caret pointing up to the cell.
- A separate option row renders as a blank grey chip — the "clear/default" choice.

## S04 — label selected (TC-003)
- Clicking Done sets the cell chip to green with a leading emoji icon; AX description becomes "Status test_item_on_monday Done".
- The group summary row Status cell mirrors the selection with the same green chip.

## S05 — reopened dropdown with existing value (TC-006)
- Reopening (Enter on focused cell) shows the same 4-option list; the selected label (Done) is the current value. A visible checkmark indicator on the selected option was not confirmed in capture (options look identical pre/post selection in the screenshots); AX cell description is the reliable selected-value signal.

## TC-005 — clear via Empty
- The grey unnamed option clears the cell; AX description returns to "no status selected" and both cell and summary return to grey.

## Notes
- Column width 140px; with horizontal scroll the sticky Item column can cover the Status cell, so clicks must target the un-occluded part. This is a layout interaction, not a dropdown behavior.
- Empty-cell dropdown is identical whether the cell has a value or not (S03 vs S05 same list), matching docs.
