---
name: pegasus-from-jira
description: Generate acceptance test coverage from a Jira story, epic, feature, or change request — story analysis, acceptance-criteria validation, acceptance test scenarios and cases, and regression impact. Use when working a sprint story or ticket.
---

# /pegasus-from-jira

Turn a Jira work item into acceptance-focused test coverage and regression scope.

## When to use
The input is a Jira story/epic/feature/ticket (number or text), typically smaller in scope than a full BRD.

## Inputs
Ticket text or ID and acceptance criteria. If only an ID is given, ask the user to paste the content (this skill does not call Jira).

## Orchestration (Jira workflow — Test Design Team)
Create `output/`, then spawn via the **Task tool**:

1. `qa-requirement-analyst` — parse story & acceptance criteria, identify impacted functionality, dependencies, gaps. → `jira-analysis.md`
2. `qa-workflow-specialist` — workflow impacts and affected paths. → contributes to coverage
3. `qa-test-designer` — acceptance scenarios + cases, and regression impact/selection. → `acceptance-test-scenarios.md`, `acceptance-test-cases.md`, `regression-impact-analysis.md`
4. `qa-risk-assessor` *(optional)* — flag high-risk areas for prioritization.
5. Assemble → `output/FINAL_QA_PACKAGE.md`

## Outputs (`output/`)
`jira-analysis.md`, `acceptance-test-scenarios.md`, `acceptance-test-cases.md`, `regression-impact-analysis.md`, `FINAL_QA_PACKAGE.md`.

## Templates
Use `.claude/skills/pegasus/templates/` (test-scenario, test-case, regression-suite).

## Rules
Every acceptance criterion maps to at least one test; flag criteria that are untestable or missing.
