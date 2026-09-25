# MASTER RESEARCH LEDGER — Status Column Type

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644
Run identifier: run_2026_09_25_status_parity_orchestrator
Started: 2026-09-25
Status: IN PROGRESS

> This ledger is the operational source of truth for this run. Every state, test case,
> observation, screenshot, and discrepancy must be registered here. Blank-slate rule:
> no content is carried from previous runs; all findings are independently rediscovered.

Traceability chain: STATE -> TEST CASE -> MONDAY EVIDENCE -> PIPELINE EVIDENCE -> DISCREPANCY

---

## 1. STATE REGISTRY

## 1. STATE REGISTRY

States are discovered and refined during exploration; this registry is updated as testing proceeds.

| State ID | State Name | Previous State | Trigger / Action | Documentation Basis | Related TCs | Monday Screenshot(s) | Monday Behaviour | Monday Visual Observation | Pipeline Screenshot(s) | Pipeline Behaviour | Pipeline Visual Observation | Related Discrepancy IDs |
|----------|-----------|----------------|------------------|---------------------|-------------|----------------------|------------------|---------------------------|------------------------|--------------------|-----------------------------|-------------------------|
| S01 | Empty/default cell | Board loaded | Item created / label cleared | Doc: gray default label | TC-001, TC-005 | monday_S01_default_empty_cell.png | Cell shows blank gray pill, no status text | Blank gray rounded rectangle, uniform grey (#666-alpha look), same height as row | pending | pending | pending | |
| S02 | Cell hover | S01/S04 | Mouse over Status cell | Real-user | TC-030 | monday_S02_cell_hover.png | Hover shows minimal chrome; no tooltip/underline observed | Cursor-only hover affordance | pending | pending | pending | |
| S03 | Cell dropdown open (empty) | S01 | Click empty Status cell | Doc: cell opens label dropdown | TC-002, TC-007, TC-028 | monday_S03_S05_dropdown_flow.md | Dropdown opens below cell: Done (green), Working on it (orange), Stuck (red), unnamed grey clear option, Edit Labels footer button. Keyboard cell focus + Enter required in automation; cell becomes ARIA button. | 4-option list + Edit Labels; grey blank chip = clear/default; caret points up to cell | pending | pending | pending | |
| S04 | Label selected/populated | S03 | Click a label | Doc | TC-003, TC-032 | monday_S03_S05_dropdown_flow.md | Clicking Done sets green chip with leading emoji; AX description 'Status ... Done'; summary row mirrors selection. | Green chip w/ emoji; narrow column truncates text but chip color + icon persist | pending | pending | pending | |
| S05 | Dropdown open with existing value | S04 | Click populated cell | Real-user | TC-004, TC-006, TC-007, TC-028 | monday_S03_S05_dropdown_flow.md | Reopen shows same 4-option list; selected value in AX cell description; visible checkmark not confirmed in capture. | List identical to S03; value proven via AX + chip | pending | pending | pending | |
| S06 | Editor opened (Edit Labels) | S03/S05 | Click Edit Labels | Doc | TC-008..TC-012, TC-018, TC-027, TC-029, TC-038, TC-039 | monday_S06_S08_editor_structure.md | Editor opens inline below cell: per-label color swatch + text field + '...' menu (Add label description / Deactivate label / Delete label); Default Label row locked (no menu); + New label; Apply. | Rows: Done/Working/Stuck w/ emoji swatches, locked grey Default Label, + New label, Apply | pending | pending | pending | |
| S07 | Editor modified (unsaved) | S06 | Change labels without Apply | Doc (Apply commits) | TC-036 | pending | pending | pending | pending | pending | pending | |
| S08 | Editor applied | S07 | Click Apply | Doc | TC-009..TC-013, TC-035, TC-037 | monday_S11_S12_capacity_stress.md | One Apply commits adds/renames/colors; surface returns to dropdown view (Apply position becomes Edit Labels again). | 40-label set saved via single Apply; AX list shows all 40 with stable IDs | pending | pending | pending | |
| S09 | Editor cancelled | S07 | Close without Apply | Real-user | TC-036 | monday_S09_editor_cancel.png | Escape closes editor but the rename (L02->L02X) was RETAINED in draft and SAVED dropdown values; no discard model | Editor closed, edit persisted without Apply | pending | pending | pending | |
| S10 | Label option hover | S03/S05 | Hover a label option | Real-user | TC-030 | monday_S10_option_hover.png | Option hover inside multi-column grid | Hover highlights option row | pending | pending | pending | |
| S11 | At max capacity (40 labels) | S08 | Add labels up to 40 | Doc: up to 40 labels | TC-013, TC-014, TC-040 | monday_S11_S12_capacity_stress.md | 40 labels saved (3 defaults + 1 empty-text + 35 custom incl. 1 duplicate). At 40 the '+ New label' button disappears. | Editor renders 40 labels as multi-column grid with horizontal scrollbar; Apply pinned bottom | pending | pending | pending | |
| S12 | Beyond-max attempt | S11 | Attempt 41st label | Guidance | TC-015 | monday_S11_S12_capacity_stress.md | 41st label cannot be attempted: '+ New label' button removed entirely at 40 — no error message, no disabled state. | Blocked by affordance removal, not validation | pending | pending | pending | |
| S13 | Empty-text label editing | S06 | Clear label text in editor | Guidance (undocumented) | TC-016, TC-017 | monday_TC016_S13_empty_label_save.md | New label left with empty text + Apply: SAVED with no validation. Dropdown gains textless blue chip (label ID 3). | No error; textless colored chip selectable in dropdown | pending | pending | pending | |
| S14 | Validation/error state | S12/S13 | Trigger invalid input | Guidance | TC-015..TC-018 | pending | pending | pending | pending | pending | pending | |
| S15 | Label description hover | S06 | Hover i icon | Doc | TC-019 | monday_S15_description_hover.png | Description editor shows 0/80 counter; i-icon tooltip shows description | Tooltip with saved description text | pending | pending | pending | |
| S16 | Deactivated label view | S06 | Deactivate via three-dot menu | Doc | TC-020, TC-021 | monday_TC021_S16_delete_used_blocked.md | Used label menu still offers Delete; clicking it yields inline error 'You can't delete a label while in use'. Deactivate remains available. Default Label row has no menu (locked). | Error message exact wording captured; matches docs + adds wording | pending | pending | pending | |
| S17 | Settings menu open | Board loaded | Column header three-dot menu | Doc | TC-023 | monday_S17_settings_menu.png | Header menu: Column ID, Settings, Filter, Sort, Collapse, Group by, Duplicate, Add to right, Change type, Save as managed, Extensions, Rename, Delete | Full header menu captured | pending | pending | pending | |
| S18 | Customize Status column (done) | S17 | Settings -> Customize Status column | Doc | TC-023 | monday_S18_settings_submenu.png + monday_S18_customize_status.png | Submenu + Status column settings panel; labels counter (40/40); done-colors picker | Panel with label list and completed-colors picker | pending | pending | pending | |
| S19 | Column summary visible | S17 | Settings -> Show column summary | Doc | TC-023, TC-024, TC-034 | monday_S19_column_summary.png | Summary row visible; menu item reads Hide/Show column summary as toggle | Summary row under item row | pending | pending | pending | |
| S20 | Status box update composer | S04 | + icon in Status box | Doc | TC-033 | monday_S20_status_box_composer.png | + icon opens Write a status note composer bound to L01 with Update button | Composer with rich-text toolbar | pending | pending | pending | |
| S21 | Long-content cell | S04 | Label with very long text | Visual stress | TC-025, TC-026 | monday_S21_long_content_cell.png | Long label chip renders in cell; text persists | Wide chip with long text | pending | pending | pending | |
| S22 | Narrow column truncation | S21 | Resize column narrow | Doc | TC-025 | monday_S22_narrow_truncation.png | Narrow column truncates chip with ellipsis; Resize Column tooltip | Truncated chip long ... | pending | pending | pending | |

---

## 2. TEST CASE REGISTRY

| Test Case ID | Title | Source | Description | Related States | Monday Result | Pipeline Result | Discrepancies |
|--------------|-------|--------|-------------|----------------|---------------|-----------------|---------------|
| PLACEHOLDER_TC

---

## 3. DISCREPANCY LEDGER

| Discrepancy ID | Related States | Related TCs | Category | Affected Element | Summary | Monday Behaviour | Pipeline Behaviour | Evidence | Severity |
|----------------|----------------|-------------|----------|------------------|---------|------------------|--------------------|----------|----------|
| (to be populated during comparison) | | | | | | | | | |

---

## 4. COVERAGE MATRIX

(to be maintained as STATE x TEST CASE matrix during testing)

---

## 5. EVIDENCE REFERENCES

| Evidence ID | Product | Description | File Path | Collected At | Related State/TC |
|-------------|---------|-------------|-----------|--------------|------------------|
| (to be populated during exploration) | | | | | |

---

## 6. BOARD / WORKSPACE CLAIM INFORMATION

| Agent / Run ID | Product | Board Name | Board ID | Purpose | Claim Status | Time |
|----------------|---------|------------|----------|---------|--------------|------|
| (to be populated when boards are claimed) | | | | | | |

---

## THEORETICAL MODEL

## THEORETICAL MODEL (documentation basis: monday.com article 360001269685, read live 2026-09-25, last modified 2026-06-23)

### Purpose
- Visual status tracking: colored labels let a team plan, organize, and track work by status (e.g., not started, in progress, done, or custom statuses).

### Adding the column
- Click the + sign at the far right of the board's column header section; choose Status from the dropdown menu.

### Label management (Edit Labels)
- Entry point: click a Status cell, then click "Edit Labels" at the bottom of the label dropdown.
- Capabilities inside the editor: reorder labels, edit label text, change label color, add additional labels.
- LIMIT: up to 40 status labels, each with a different color.
- Commit: changes take effect via the "Apply" button.
- Default label: the gray label is the default assigned when an item is created; monday recommends leaving the gray label blank.
- Label description: three-dot menu next to a label -> "Add label description". After adding, an "i" icon appears next to the label; hovering shows the description.
- Deletion/deactivation: a label used in board items cannot be deleted; it can be deactivated via the label's three-dot menu -> "Deactivate". Deactivated labels do not appear as options in the cell dropdown; they appear grayed out in label settings.
- Empty-text labels: documentation does not explicitly describe saving labels without text (to be probed live on both products).

### Column interactions
- Resizing: drag the right edge of the Status column near the column title; long label text may be cut off when the column is narrow.
- Cell dropdown: clicking a Status cell opens the label selector (with Edit Labels at bottom).

### Done labels
- Per-board configuration: column header three-dot menu -> Settings -> "Customize Status column" -> choose the color(s) that count as "done".

### Column summary
- Settings -> "Show column summary". Two display choices: a thumbnail of what's done, or all status labels; clicking the summary switches the display.

### Status box updates
- A + sign in the top-right corner of any Status box allows posting an update tied to that status; updates also appear in the item's Updates section.
- If the status is changed while an update exists, the update disappears from the status box but remains in the item's Updates section.

### Account-level default labels (admin only)
- Avatar -> Administration -> Customization -> Boards tab.
- Pick from over 40 color labels; changes apply ONLY to new Status columns, never to existing ones.

### Settings entry points summary
- Cell: label dropdown with "Edit Labels" at bottom.
- Column header three-dot menu: Settings -> "Customize Status column" (done colors), "Show column summary".

### Limits and boundaries (documented)
- Maximum 40 status labels per Status column.
- Used labels cannot be deleted, only deactivated.
- Account default label changes do not retroactively modify existing columns.

### AI exclusion
- The article contains no AI-specific functionality; nothing to exclude. Monday automations are mentioned only as a general tip and stay out of scope unless directly tied to Status behaviour under test.

### Keyboard/mouse specifics documented
- The article documents mouse-driven interactions (click, hover for description icon, drag to resize). No keyboard-specific interactions are documented (to be probed live).

---

## 5. MONDAY EXPLORATION LOG — W4 capacity stress (2026-09-25, rev 111+)

Executed TCs this session (board 18431468439, column color_mm7bcxvk, item 13065765942):

| TC | Result (Monday) | Evidence |
|-----|-----------------|----------|
| TC-002 (S03 dropdown open, empty) | PASS — dropdown opens below cell: Done/Working on it/Stuck + grey clear + Edit Labels. Automation note: keyboard cell focus + Enter opens it; synthetic pointer emulation does not. | monday_S03_S05_dropdown_flow.md |
| TC-003 (S04 select label) | PASS — Done applied; chip green w/ emoji; summary mirrors. | monday_S03_S05_dropdown_flow.md |
| TC-005 (clear via Empty) | PASS — grey unnamed option clears; AX returns to 'no status selected'. | monday_S03_S05_dropdown_flow.md |
| TC-006 (S05 reopen w/ value) | PASS — same list; value in AX description; visible checkmark not confirmed. | monday_S03_S05_dropdown_flow.md |
| TC-008 (S06 editor open/structure) | PASS — inline editor; per-label swatch+text+'...' menu; Default Label locked; Apply commits. | monday_S06_S08_editor_structure.md |
| TC-013 (reach 40 labels) | PASS — 40 label definitions saved (docs limit = 40 CONFIRMED live). | monday_S11_S12_capacity_stress.md |
| TC-014/TC-040 (max-capacity interactions) | PASS + NEW — dropdown and editor switch to multi-column grid with horizontal scrollbars at 40 labels. | monday_S11_S12_capacity_stress.md |
| TC-015 (attempt 41st / S12) | BLOCKED BY UI — '+ New label' button removed entirely at 40; no error or disabled state. | monday_S11_S12_capacity_stress.md |
| TC-016/TC-017 (empty-text label) | SAVED WITHOUT VALIDATION — textless blue chip (ID 3) appears in dropdown. Undocumented behavior. | monday_TC016_S13_empty_label_save.md |
| TC-018 (duplicate names) | ALLOWED — two independent 'L10' labels coexist (IDs 14, 15). | monday_S11_S12_capacity_stress.md |
| TC-020/TC-021 (used-label delete) | BLOCKED WITH MESSAGE — Delete menu item present for used label; clicking yields "You can't delete a label while in use". Deactivate available. | monday_TC021_S16_delete_used_blocked.md |

THEORY MODEL corrections from live probing (docs vs live):
1. Max 40 labels CONFIRMED; manifest = "+ New label" button removal (docs silent on how the limit manifests).
2. Undocumented: empty-text labels are accepted and save with no validation.
3. Undocumented: duplicate label names are allowed (no uniqueness check).
4. Undocumented: at high label counts the dropdown/editor render as a multi-column grid with horizontal scrolling.
5. Error wording added: "You can't delete a label while in use" (docs say used labels cannot be deleted without the wording).
6. Default Label (grey empty) row is locked in the editor: no '...' menu, cannot be renamed/recolored/deleted/deactivated.
7. Labels carry default emoji icons on their swatches; new-label chips show color + emoji glyph.
8. Automation note (not user-facing parity): Monday cells require real pointer interaction or keyboard cell focus for the dropdown; wrapper-level synthetic clicks do not trigger it.

Board state after session (intentional, for Pipeline-side capacity comparison): column color_mm7bcxvk now has exactly 40 labels (Done, Working on it, Stuck, grey Default Label, textless blue label, L01..L34 with duplicate L10), and item test_item_on_monday has L01 applied. All state changes documented above; no code amendments made (research-only run).


## 6. MONDAY COMPLETION SESSION — W4 settings/visual states (2026-09-25, rev 118+)

Executed TCs this session (board 18431468439, column color_mm7bcxvk, dedicated Chrome tab):

| TC | Result (Monday) | Evidence |
|-----|-----------------|----------|
| TC-030 (S02 cell hover) | PASS — minimal hover chrome (cursor only). | monday_S02_cell_hover.png |
| TC-030 (S10 option hover) | PASS — option hover in multi-column grid. | monday_S10_option_hover.png |
| TC-036 (S09 editor cancel) | DIFF FOUND — Escape does NOT discard: L02->L02X rename retained in draft and saved values without Apply. | monday_S09_editor_cancel.png |
| TC-019 (S15 description) | PASS — description editor with 0/80 counter; i-icon tooltip shows text; Apply persists. | monday_S15_description_hover.png |
| TC-020 (S16 deactivate/reactivate) | PASS — deactivate hides L04 from dropdown (39 options); row grayed, no Inactive caption; menu offers "Reactivate label" (wording DIFF vs Pipeline "Activate label"); reactivate restores (40 options). | monday_S16_deactivated_view.png |
| TC-023 (S17/S18 settings) | PASS — header menu + Settings submenu (incl. Set column validation tagged New, Restrict editing/view) + Customize panel with (40/40) counter and done-colors picker. | monday_S17_settings_menu.png, monday_S18_settings_submenu.png, monday_S18_customize_status.png |
| TC-024/TC-034 (S19 summary) | PASS — summary row visible; menu toggle wording Hide/Show column summary. | monday_S19_column_summary.png |
| TC-033 (S20 status box composer) | PASS — + icon (add-status-note) opens Write a status note composer bound to L01; rich-text toolbar; Update button; closed without posting. | monday_S20_status_box_composer.png |
| TC-025/TC-026 (S21 long content) | PASS — long label applied to item; chip renders full text at wide column. | monday_S21_long_content_cell.png |
| TC-025 (S22 narrow truncation) | PASS — chip truncates with ellipsis ("long ..."); Resize Column tooltip at drag handle; summary mirrors truncated chip. | monday_S22_narrow_truncation.png |

NEW model corrections (docs vs live):
9. Escape in the label editor does NOT discard edits; renames commit on close without explicit Apply (S09 DIFF vs Pipeline helper text "Escape discards unapplied edits").
10. Label description editor enforces an 80-character limit with a live counter.
11. Deactivated-label menu wording is "Reactivate label" (not "Activate label"); deactivated rows stay in the editor list grayed with no caption text.
12. Settings submenu includes Set column validation (New), Restrict column editing, Restrict column view, Save column as a template — no direct Pipeline equivalents observed in its editor.
13. Status box composer: + icon only appears with a selected status; composer bound to that label; closing via X discards silently (no draft warning).

Board state after session: L01 applied; L03 description present; L04 reactivated; L05 restored; column width ~141px; 40 labels (incl. duplicate L10, textless label). All mutations reversible and documented; no source amendments.
