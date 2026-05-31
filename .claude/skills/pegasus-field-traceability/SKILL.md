---
name: pegasus-field-traceability
description: Build field-level traceability and validation across screens, databases, integrations, APIs, reports, and exports — mapping each field source-to-destination with transformations, plus validation test cases. Use when validating data accuracy end to end.
---

# /pegasus-field-traceability

Map and validate how fields move and transform across the whole application.

## When to use
The request centers on fields, data mappings, transformations, integrations, or UI-to-report data flow.

## Inputs
Field list and context: screens, entities, integration/report definitions, mappings. Ask for any missing mapping source.

## Orchestration (Field Traceability workflow)
Create `output/`, then spawn via the **Task tool**:

1. `qa-field-traceability-specialist` — build the field inventory and full source-to-destination lineage with transformations. → `field-traceability-matrix.md`, `data-lineage-report.md`, `transformation-analysis.md`
2. `qa-ui-report-validator` — cross-validate each field's value across UI, DB, report, export, API. → `field-validation-report.md`
3. `qa-test-designer` — generate field/transformation/integration validation cases. → `test-cases.md`
4. Assemble → `output/FINAL_QA_PACKAGE.md`

## Outputs (`output/`)
`field-traceability-matrix.md`, `data-lineage-report.md`, `transformation-analysis.md`, `field-validation-report.md`, `test-cases.md`, `FINAL_QA_PACKAGE.md`.

## Templates
Use `.claude/skills/pegasus/templates/field-traceability-matrix.md` and `test-case.md`.

## Rules
Every field gets an ID and a complete chain; flag any lossy or assumed transformation as a test target.
