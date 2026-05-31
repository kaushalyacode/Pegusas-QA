# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project: Pegasus — Enterprise QA Copilot Skill

Pegasus is an AI-powered Claude Code skill suite for enterprise quality assurance. It is not a test framework or automation tool. It is a set of Claude Code skills (`/pegasus*` commands) that help QA engineers, business testers, and product teams perform end-to-end functional testing — from requirement analysis through release sign-off.

**Master Specification:** See `README.md` — this is the authoritative architecture specification. All other docs are derived from it.

---

## What Pegasus Does

- **BRD Analysis:** Parse business requirements → generate test plans, test cases, workflow analysis, traceability
- **Jira Story Analysis:** Given a Jira ticket → generate acceptance test cases
- **Field Traceability:** Trace data fields across systems, databases, reports, APIs
- **Workflow Testing:** Multi-screen validation, state transitions, approval workflows, end-to-end tests
- **UI/Report Validation:** Verify consistency between UI, reports, exports, APIs
- **Bug Report Generation:** Transform failure descriptions → structured Jira-ready defect reports
- **Release Assessment:** Test execution results → release readiness recommendation (Go/No-Go)

---

## Core Documentation

| File | Purpose | Audience |
|------|---------|----------|
| **README.md** | **MASTER SPEC** — Full architecture, 5 design principles, 8 skills, 9 subagents, team structure, deliverables | Architects, leads |
| **PEGASUS_SKILLS.md** | How skills & subagents are implemented, input/output per skill, template requirements | Developers implementing skills |
| **PEGASUS_SUBAGENTS.md** | Specialist subagent profiles, responsibilities, inputs/outputs for each agent | Developers working with agents |
| **PEGASUS_WORKFLOWS.md** | 7 workflow patterns with agent sequencing and artifact flow | QA engineers using Pegasus |

---

## Skills (User-Facing Commands)

All skills are in `.claude/skills/` and invoked via `/skill-name`:

| Skill | Input | Output | Use When |
|-------|-------|--------|----------|
| `/pegasus` | Any QA artifact (BRD, ticket, results, etc.) | Auto-routes to best skill; shows menu if unclear | You're unsure which skill to use |
| `/pegasus-from-brd` | BRD, Functional Spec, user story | Full QA package: scenarios, cases, traceability, risk | Analyzing a business requirement |
| `/pegasus-from-jira` | Jira ticket number or text | Story analysis, acceptance test cases, regression scope | Working on a sprint story |
| `/pegasus-field-traceability` | Field names + context | Field mapping across all systems, validation test cases | Validating data accuracy end-to-end |
| `/pegasus-workflow-testing` | Workflow description + screens | Workflow tests, state transitions, exception paths | Testing multi-step processes |
| `/pegasus-ui-report-validation` | Report/dashboard specs | UI↔Report validation, reconciliation analysis | Validating report accuracy |
| `/pegasus-bug-report` | Issue description + logs | Structured defect report, ready for Jira | Creating bug reports |
| `/pegasus-test-summary` | Test execution results + defect counts | Release readiness report, Go/No-Go recommendation | Deciding if ready to ship |

---

## Subagents (Specialist Engines)

Located in `.claude/agents/`, spawned by skills via the Task tool (`subagent_type` = agent name):

1. **qa-requirement-analyst** — Decompose requirements, extract business rules, identify gaps
2. **qa-field-traceability-specialist** — Map fields across systems, trace data lineage
3. **qa-workflow-specialist** — Analyze workflows, state transitions, exception paths
4. **qa-ui-report-validator** — Validate UI↔Report consistency, reconciliation
5. **qa-test-designer** — Generate test scenarios and cases (happy path, negative, edge cases)
6. **qa-defect-analyst** — Classify defects, assess severity, generate root-cause hypotheses
7. **qa-release-assessor** — Evaluate release readiness, Go/No-Go decisions
8. **qa-domain-specialist** — Domain expertise: compliance, business rules, industry patterns
9. **qa-risk-assessor** — Identify testing risks, prioritize high-risk areas

---

## Design Principles

Pegasus follows 5 core principles (from README.md):

1. **Workflows > Screens** — Enterprise defects cross workflows, not screens. Test end-to-end paths.
2. **Field Traceability First** — Every field traceable: source → screen → DB → report → export → API
3. **Temporal Logic** — Automatic detection/testing of effective dates, historical data, versioning
4. **Reports = UI** — Report validation is equally important as UI validation
5. **Business Rules Drive Tests** — Extract rules; generate positive, negative, boundary, exception tests

---

## Workflow Patterns

7 standard workflow patterns are defined in `PEGASUS_WORKFLOWS.md`:

1. **BRD Analysis** — Full testing coverage from business requirement
2. **Jira Story** — Acceptance test cases from sprint story
3. **Field Traceability** — Trace a field across all systems
4. **Multi-Screen Workflow** — End-to-end workflow validation
5. **Defect Analysis** — Bug report generation
6. **Release Readiness** — Go/No-Go assessment
7. **Enterprise Patterns** — Auto-detect effective dating, approvals, compliance

See `PEGASUS_WORKFLOWS.md` for sequencing, inputs, and outputs.

---

## Output Deliverables

Pegasus generates structured markdown artifacts:

- `requirement-analysis.md` — Requirements decomposed
- `business-rules.md` — Extracted business rules
- `test-scenarios.md` — 50-100+ scenarios per feature
- `test-cases.md` — 200-500+ test cases per feature
- `field-traceability-matrix.md` — Fields mapped across systems
- `workflow-analysis.md` — Workflows, actors, state transitions
- `ui-report-validation.md` — UI↔Report consistency validation
- `defect-report.md` — Structured Jira-ready bug report
- `release-readiness.md` — Go/No-Go recommendation
- `FINAL_QA_PACKAGE.md` — Consolidated executive summary

---

## Key Commands

Skills auto-trigger by description, or can be invoked explicitly. Use `/pegasus` when unsure which applies:

```bash
# Example: Analyze a BRD
/pegasus-from-brd

# Example: Generate tests from Jira story
/pegasus-from-jira

# Example: Bug report from failure
/pegasus-bug-report

# Example: Release readiness
/pegasus-test-summary
```

---

## Project Structure

```
.claude/
├── agents/                       # specialist subagents, spawned via the Task tool
│   ├── qa-requirement-analyst.md
│   ├── qa-field-traceability-specialist.md
│   ├── qa-workflow-specialist.md
│   ├── qa-ui-report-validator.md
│   ├── qa-test-designer.md
│   ├── qa-defect-analyst.md
│   ├── qa-release-assessor.md
│   ├── qa-domain-specialist.md
│   └── qa-risk-assessor.md
└── skills/
    ├── pegasus/                  # orchestrator + shared assets
    │   ├── SKILL.md
    │   ├── templates/
    │   │   ├── test-scenario.md
    │   │   ├── test-case.md
    │   │   ├── regression-suite.md
    │   │   ├── field-traceability-matrix.md
    │   │   ├── requirement-traceability-matrix.md
    │   │   ├── workflow-validation.md
    │   │   ├── ui-report-validation.md
    │   │   ├── bug-report.md
    │   │   ├── risk-assessment.md
    │   │   └── release-readiness.md
    │   ├── knowledge/
    │   │   └── enterprise-testing-heuristics.md
    │   └── workflows/
    │       └── workflow-patterns.md
    ├── pegasus-from-brd/
    │   └── SKILL.md
    ├── pegasus-from-jira/
    │   └── SKILL.md
    ├── pegasus-field-traceability/
    │   └── SKILL.md
    ├── pegasus-workflow-testing/
    │   └── SKILL.md
    ├── pegasus-ui-report-validation/
    │   └── SKILL.md
    ├── pegasus-bug-report/
    │   └── SKILL.md
    └── pegasus-test-summary/
        └── SKILL.md
```

---

## Implementation Status

**Phase 0 (Planning) — COMPLETE**
- ✓ Architecture designed (README.md)
- ✓ Skills defined (PEGASUS_SKILLS.md)
- ✓ Subagents defined (PEGASUS_SUBAGENTS.md)
- ✓ Workflows documented (PEGASUS_WORKFLOWS.md)
- ✓ Documentation synchronized across README, skills, subagents, and workflows

**Phase 1 (Implementation) — COMPLETE (scaffolded)**
- ✓ 9 subagents implemented in `.claude/agents/`
- ✓ 8 skills implemented as `.claude/skills/*/SKILL.md`
- ✓ 10 output templates + knowledge & workflow assets under `.claude/skills/pegasus/`

**Phase 2 (Validation) — NEXT**
- Exercise each skill against a sample artifact; refine agent/skill prompts based on output quality

---

## Key Files to Understand

Before implementing, read these in order:

1. `README.md` — Understand the 5 design principles and full vision
2. `PEGASUS_SKILLS.md` — Understand what each skill does
3. `PEGASUS_SUBAGENTS.md` — Understand subagent responsibilities
4. `PEGASUS_WORKFLOWS.md` — Understand how skills/agents work together

---

## Common Tasks

### "I need to add a new skill"
→ Refer to `PEGASUS_SKILLS.md` for naming and output requirements
→ Define input triggers in `PEGASUS_WORKFLOWS.md`
→ Create `.claude/skills/pegasus-name/SKILL.md`

### "I need to fix a subagent"
→ Refer to `PEGASUS_SUBAGENTS.md` for mission and responsibilities
→ Check `PEGASUS_WORKFLOWS.md` to see where it's invoked
→ Update `.claude/agents/qa-name.md`

### "I need to update a workflow"
→ Check `PEGASUS_WORKFLOWS.md` for the pattern
→ Validate against `README.md` design principles
→ Update both files consistently

---

## Critical Rules (from README.md)

1. **Workflows first, screens second** — Design tests around business workflows
2. **Traceability is mandatory** — Every test must link back to a requirement or business rule
3. **No skipped upstream analysis** — Test design can't skip workflow analysis
4. **Domain-aware** — Consider compliance, temporal logic, business patterns
5. **Standardized outputs** — All artifacts use templates from `.claude/skills/pegasus/templates/`

---

## Next Steps When Starting Development

1. Read `README.md` completely (understand the vision)
2. Read `PEGASUS_SKILLS.md` (understand the plan)
3. Implement Phase 1: Start with `/pegasus-from-brd` (highest value)
4. Create `.claude/skills/pegasus-from-brd/SKILL.md` with full instructions
5. Test the skill with a sample BRD
6. Iterate based on output quality
7. Move to next skill

---

## For Questions or Debugging

- **Architecture questions** → Check `README.md`
- **Skill behavior** → Check `PEGASUS_SKILLS.md` and `PEGASUS_WORKFLOWS.md`
- **Subagent issues** → Check `PEGASUS_SUBAGENTS.md`
- **Workflow logic** → Check `PEGASUS_WORKFLOWS.md`
