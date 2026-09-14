# Biomedical Inventory Reporting

Transforming an existing inventory into a structured Excel report for client delivery.

## Why this project was developed

A new report was requested by a client. The biomedical management team needed support designing the report structure from its existing inventory.

The source inventory did not need to be corrected or redesigned. My contribution was to structure the transformation into a consolidated Excel workbook that could support the requested delivery.

This is a reporting and data-transformation project, not a machine-learning project.

## Public demonstration

[Open the V3 notebook](notebooks/biomedical_inventory_reporting_v3.ipynb) · [Previous V2](notebooks/biomedical_inventory_reporting.ipynb).

V3 adds an embedded useful-life lookup, unmatched-description coverage, and reconciliation of the saved workbook. The original company catalogue is excluded; two fictional reference values demonstrate the functionality. See [version notes](docs/versions.md).

The notebook defaults to a fictional 12-record example. It creates a consolidated sheet and separate functional-unit sheets. One valid inventory row represents one asset; a quantity column is not used. Brands and models are counted separately.

Expected sample totals: **12 assets, three units, four assets per unit**. These are test expectations, not verified execution results.

## Run

Requires Python 3.10 or newer.

```bash
pip install -r requirements.txt
jupyter notebook
```

Open the notebook and run all cells. V3 demo mode generates `synthetic_inventory_v3.xlsx` and `demo_inventory_report_v3.xlsx` locally. In Google Colab, install pandas and openpyxl if needed, then run the notebook directly.

## Transformation rules

- Preserve the original workbook.
- Detect standard inventory headers within the first 20 rows.
- Reject equally ranked candidate tables rather than selecting one silently.
- Count by functional unit, functional space, description, brand, and model.
- Keep distinct brand/model combinations separate.
- Do not deduplicate rows automatically: repeated descriptions may represent distinct assets.
- Reconcile valid input counts with grouped totals.
- Keep unavailable installation fields blank; V3 assigns useful life only on normalized exact description matches.

Both public copies are adapted from reviewed source notebooks. Organization-specific unit mappings, original outputs, and notebook author metadata are removed.

## Scope and status

| Item | Status |
|---|---|
| Business context and original V2 grouping logic | Reviewed |
| Fictional demonstration notebook | Published |
| Python execution and workbook inspection | Pending |
| Useful-life reference dictionary | V3 public example published; original private catalogue excluded |
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

This repository is a portfolio demonstration in validation, not a production release. The V2 classification grouping uses the most frequent non-empty value. Empty fields are not inferred. The V3 fictional lookup values are demonstration assumptions, not company policy or biomedical guidance. A private approved catalogue is required for real use.
