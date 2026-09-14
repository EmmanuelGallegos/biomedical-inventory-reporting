# Validation checklist

Status: source reviewed; Python execution and workbook review pending.

## Fictional sample

Run every cell in order with DEMO_MODE=True. Confirm:
- Exactly 12 valid source records.
- Grouped counts total 12.
- Three functional-unit sheets, each totaling four assets.
- Consolidated totals also sum to 12.
- Distinct brand/model combinations are not merged.
- Original input workbook is unchanged.
- Missing useful-life and installation values remain blank.
- Workbook opens without repair warnings.

## Transformation edge cases

Check blank unit/description rows, TOTAL rows, absent optional classification, conflicting classifications within one combination, missing brand/model, Unicode/whitespace normalization, headers beyond row 20, ambiguous candidate sheets, and sheet names that collide after sanitizing or truncating.

Do not delete repeated-looking asset rows unless an approved asset-ID rule defines a duplicate.

## Layout

Inspect headers, filters, frozen panes, widths, wrapping, numeric counts, and each unit total. Verify the consolidated sheet against all unit detail sheets, not just the in-memory detail dataframe.

## Publish verification

Record actual execution output before changing validation status. Do not present planned assertions or expected sample values as passed tests.
