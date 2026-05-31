---
name: pegasus-from-brd
description: Generate a full enterprise QA package from a BRD, PRD, functional/technical spec, or business requirement document — requirement analysis, business rules, gap analysis, domain & compliance review, field traceability, workflow analysis, test scenarios and cases, UI/report validation, and risk. Use when the user provides or points to a requirements document and wants test coverage.
---

# /pegasus-from-brd

Produce comprehensive manual-testing coverage from a business requirements document.

## When to use
The input is a BRD, PRD, functional or technical specification, or a substantial business requirement / change request.

## Inputs
The document text or path. Ask for the file if only a reference is given.

## Orchestration (BRD workflow — Requirement + Test Design Teams)
Create `output/`, then spawn these subagents via the **Task tool** (`subagent_type` = agent name), respecting dependency order. Run independent steps in parallel.

1. `qa-requirement-analyst` — decompose requirements, extract rules, find gaps. → `requirement-analysis.md`, `business-rules.md`, `gap-analysis.md`
2. `qa-domain-specialist` — domain & compliance lens (can run alongside step 1). → `domain-analysis.md`
3. `qa-field-traceability-specialist` — field lineage across systems. → `field-traceability-matrix.md`
4. `qa-workflow-specialist` — workflows & state transitions. → `workflow-analysis.md`
5. `qa-test-designer` — scenarios + cases from steps 1–4. → `test-scenarios.md`, `test-cases.md`
6. `qa-ui-report-validator` — UI/report validation where outputs exist. → `ui-report-validation.md`
7. `qa-risk-assessor` — risk + prioritization. → `risk-assessment.md`
8. Assemble → `output/FINAL_QA_PACKAGE.md`

Do not let any step skip its upstream inputs.

## Outputs (`output/`)
`requirement-analysis.md`, `business-rules.md`, `gap-analysis.md`, `domain-analysis.md`, `field-traceability-matrix.md`, `workflow-analysis.md`, `test-scenarios.md`, `test-cases.md`, `ui-report-validation.md`, `risk-assessment.md`, `FINAL_QA_PACKAGE.md`.

## Templates
Use `.claude/skills/pegasus/templates/` (test-scenario, test-case, field-traceability-matrix, workflow-validation, ui-report-validation, risk-assessment).

## Rules
Traceability is mandatory; prefer end-to-end workflow tests over per-screen tests; surface every gap and assumption.
