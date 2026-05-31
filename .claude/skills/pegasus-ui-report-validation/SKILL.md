---
name: pegasus-ui-report-validation
description: Validate consistency between UI, backend data, APIs, dashboards, reports, and exports — displayed values, calculations, aggregations, formatting, and reconciliation. Use when validating report/dashboard/export accuracy or that the UI matches the report.
---

# /pegasus-ui-report-validation

Validate that values are consistent across UI, data, reports, and exports.

## When to use
The request involves reports, dashboards, exports, analytics outputs, or a "does the UI match the report/export?" question.

## Inputs
UI and report/dashboard/export specifications and, where available, a field traceability matrix.

## Orchestration (Validation Team)
Create `output/`, then spawn via the **Task tool**:

1. `qa-field-traceability-specialist` *(if no matrix exists)* — establish the source of truth per reported value. → `field-traceability-matrix.md`
2. `qa-ui-report-validator` — UI validation, report validation, and cross-validation (UI = DB = report = export = API), plus reconciliation. → `ui-validation-report.md`, `report-validation-report.md`, `ui-report-validation.md`, `reconciliation-analysis.md`
3. `qa-test-designer` — executable validation and reconciliation test cases. → `test-cases.md`
4. Assemble → `output/FINAL_QA_PACKAGE.md`

## Outputs (`output/`)
`ui-validation-report.md`, `report-validation-report.md`, `ui-report-validation.md`, `reconciliation-analysis.md`, `test-cases.md`, `FINAL_QA_PACKAGE.md`.

## Templates
Use `.claude/skills/pegasus/templates/ui-report-validation.md` and `test-case.md`.

## Rules
Every reported value names its single source of truth and the surfaces it must match, with tolerance rules where defined.
