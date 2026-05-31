---
name: pegasus-bug-report
description: Convert an issue description, failure, logs, or screenshot into a structured, triage-ready defect report — severity, priority, deterministic reproduction steps, expected vs actual, business impact, and root-cause hypotheses. Use to create bug reports.
---

# /pegasus-bug-report

Turn a raw issue into a structured, developer-ready defect report.

## When to use
The input describes a bug, failure, unexpected behavior, or includes error logs/screenshots.

## Inputs
Issue description plus any evidence (logs, screenshots, steps observed, environment).

## Orchestration (Defect workflow)
Create `output/`, then spawn via the **Task tool**:

1. `qa-defect-analyst` — establish expected vs actual and the violated requirement/rule; reconstruct deterministic reproduction steps; assess severity and priority; generate root-cause hypotheses. → `defect-report.md`, `root-cause-analysis.md`, `defect-impact-analysis.md`
2. Assemble / present → `output/FINAL_QA_PACKAGE.md` (or output the defect report directly for quick single-bug requests).

## Outputs (`output/`)
`defect-report.md`, `root-cause-analysis.md`, `defect-impact-analysis.md`.

## Templates
Use `.claude/skills/pegasus/templates/bug-report.md`.

## Rules
Reproduction steps must be deterministic and numbered; severity (impact) and priority (urgency) are assessed separately and justified.
