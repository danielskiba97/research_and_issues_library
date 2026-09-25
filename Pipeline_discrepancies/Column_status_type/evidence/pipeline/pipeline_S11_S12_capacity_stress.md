# Pipeline Status column — label capacity stress past 40 (S11/S12, TC-013/014/015/040)

Run: adaptive_5884e5d2836ad7e27e6ea4d26d3ded2866d4ad731aa05683042df618050bc644. Date 2026-09-25. THE core guidance-ask test.

## Method
- Interactive UI stress via the Edit Labels editor: repeated "New label" -> type name (L01..L36) -> single "Apply" commit.
- Labels verified both from the accessibility tree AND the persisted SQLite payload (data/pipeline.sqlite workspace JSON, board board_8bl8zfas7tavq, column saxfuhjmdkkbk).

## Result: 40-label ceiling NOT enforced (S12 DIFF)
- Pipeline reached and PERSISTED 41 labels: Done, Working on it, Stuck, Default Label, zz_long, L01..L36 (41 rows in the saved payload; each with a distinct color).
- At exactly 40 labels the "+ New label" button was STILL PRESENT (Monday removes it). Clicking it created a 41st editable row; only THEN did the button become disabled with tooltip "Status columns support up to 40 labels."
- Apply with 41 labels SUCCEEDED — the persisted payload contains 41 label definitions and the dropdown lists all 41 (verified in AX and in the SQLite payload: label_gxt6m4aii8qa9 ... label_b04n6br6kuxtl).
- Monday at 40: the affordance is removed entirely and no 41st label can be attempted. Pipeline: cap enforced only after the over-limit row exists, and one over-limit label leaked through the UI into the data store.

## At-capacity / over-capacity UI behaviors (TC-040)
- The editor renders the label set as a multi-column grid (3+ columns at 41 labels) with its own scroll container; Apply pinned at the bottom.
- The cell dropdown lists all labels (41) in a vertical list; each option is a full chip (color swatch + name).
- The disabled "+ New label" tooltip documents the limit ("Status columns support up to 40 labels.") — Monday shows no message at all (affordance simply gone).
