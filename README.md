# Biomedical Inventory Reporting

Transforming an existing inventory into a structured Excel report for client delivery.

## Why this project was developed

A new report was requested by a client. The biomedical management team needed support designing the report structure from its existing inventory.

The source inventory did not need to be corrected or redesigned. My contribution was to structure the transformation into a consolidated Excel workbook that could support the requested delivery.

This is a reporting and data-transformation project, not a machine-learning project.

## Public demonstration

[Open the guided notebook](notebooks/biomedical_inventory_reporting.ipynb).

The notebook defaults to a fictional 12-record example. It creates a consolidated sheet and separate functional-unit sheets. One valid inventory row represents one asset; a quantity column is not used. Brands and models are counted separately.

Expected sample totals: **12 assets, three units, four assets per unit**. These are test expectations, not verified execution results.

## Run

Requires Python 3.10 or newer.

```bash
pip install -r requirements.txt
jupyter notebook
```

Open the notebook and run all cells. Demo mode generates `synthetic_inventory.xlsx` and `demo_inventory_report.xlsx` locally. In Google Colab, install pandas and openpyxl if needed, then run the notebook directly.

## Transformation rules

- Preserve the original workbook.
- Detect standard inventory headers within the first 20 rows.
- Reject equally ranked candidate tables rather than selecting one silently.
- Count by functional unit, functional space, description, brand, and model.
- Keep distinct brand/model combinations separate.
- Do not deduplicate rows automatically: repeated descriptions may represent distinct assets.
- Reconcile valid input counts with grouped totals.
- Keep unavailable installation and useful-life fields blank.

The public copy is adapted from the reviewed V2 notebook. Organization-specific unit mappings, original outputs, and notebook author metadata are removed.

## Scope and status

| Item | Status |
|---|---|
| Business context and original V2 grouping logic | Reviewed |
| Fictional demonstration notebook | Published |
| Python execution and workbook inspection | Pending |
| Useful-life reference dictionary | Not implemented in this V2 adaptation |
| Actual inventories or client reports | Not published |
| Measured time savings | Not claimed |

## Files

- `notebooks/`: ordered explanation and demo-enabled notebook.
- `docs/validation.md`: checks to perform before declaring the demo verified.
- `docs/privacy.md`: public-release rules.
- `requirements.txt`: dependencies for local execution.
- `.gitignore`: keeps local workbooks and credentials out of git.

## Privacy

No real inventory, asset serial numbers, customer identity, company name, or original report is included. Demo unit names, brands, and models are fictional. Changing labels alone is not sufficient anonymization; public data must be generated independently.

## Limitations

This repository is a portfolio demonstration in validation, not a production release. The V2 classification grouping uses the most frequent non-empty value. Empty fields are not inferred. A source-specific useful-life table and other business rules require a separate approved implementation.
