# Pegasus Subagent Definitions

## Purpose

This document defines the specialist subagents used within the Pegasus QA Framework.

Subagents are focused analysis engines that perform domain-specific tasks and generate structured artifacts for downstream skills and orchestration workflows.

Subagents do not produce final deliverables directly. Instead, they generate analysis outputs that are consumed, validated, and consolidated by Pegasus skills and orchestrators.

---

# qa-requirement-analyst

## Mission

Analyze and decompose business requirements into actionable QA intelligence.

## Responsibilities

* Requirement decomposition
* Business rule extraction
* Acceptance criteria identification
* Gap analysis
* Ambiguity detection
* Missing requirement detection
* Requirement dependency analysis
* Requirement risk identification
* Traceability preparation

## Inputs

* Business requirement documents
* Functional specifications
* User stories
* Work items and tickets
* Change requests
* Business process documentation

## Outputs

* requirement-analysis.md
* business-rules.md
* acceptance-criteria-analysis.md
* gap-analysis.md
* requirement-risk-assessment.md

---

# qa-field-traceability-specialist

## Mission

Analyze and document field-level data movement across systems, screens, workflows, integrations, APIs, and reports.

## Responsibilities

* Source field identification
* Destination field identification
* Transformation rule analysis
* Mapping validation
* Dependency identification
* Data lineage analysis
* Temporal and versioned data analysis
* Cross-system traceability validation

## Inputs

* Requirements documentation
* UI specifications
* Database mappings
* Integration specifications
* API contracts
* Report definitions

## Outputs

* field-traceability-matrix.md
* field-mapping-analysis.md
* data-lineage-report.md

---

# qa-workflow-specialist

## Mission

Analyze business workflows, user journeys, and state transitions to ensure complete process validation.

## Responsibilities

* Workflow discovery
* User journey analysis
* State transition analysis
* Multi-screen flow analysis
* Workflow dependency identification
* Exception path analysis
* Approval flow validation
* Workflow risk assessment

## Inputs

* Business process documentation
* User stories
* Workflow diagrams
* Application specifications

## Outputs

* workflow-analysis.md
* workflow-validation.md
* state-transition-matrix.md
* workflow-risk-assessment.md

---

# qa-ui-report-validator

## Mission

Validate consistency and accuracy between application interfaces, backend data, APIs, dashboards, exports, and generated reports.

## Responsibilities

* UI validation coverage analysis
* Report validation coverage analysis
* Cross-validation generation
* Field consistency verification
* Data reconciliation analysis
* Display-to-report mapping validation
* Aggregation validation
* Formatting validation

## Inputs

* UI specifications
* Report specifications
* Dashboard specifications
* Field traceability artifacts
* Business requirements

## Outputs

* ui-report-validation.md
* reconciliation-analysis.md
* report-consistency-matrix.md

---

# qa-test-designer

## Mission

Design comprehensive test coverage based on requirements, workflows, business rules, and traceability analysis.

## Responsibilities

* Scenario generation
* Test case generation
* Positive testing design
* Negative testing design
* Boundary testing design
* Workflow testing design
* Integration testing design
* Regression impact analysis
* Risk-based test prioritization

## Inputs

* Requirement analysis artifacts
* Workflow analysis artifacts
* Traceability artifacts
* Business rules
* Acceptance criteria

## Outputs

* test-scenarios.md
* test-cases.md
* regression-suite.md
* coverage-matrix.md
* risk-based-test-plan.md

---

# qa-defect-analyst

## Mission

Analyze defects and failures to support efficient triage and resolution.

## Responsibilities

* Defect classification
* Severity recommendations
* Priority recommendations
* Root-cause hypothesis generation
* Impact assessment
* Reproduction analysis
* Requirement traceability validation

## Inputs

* Defect reports
* Test execution results
* Logs and evidence
* Requirement artifacts

## Outputs

* defect-report.md
* defect-impact-analysis.md
* root-cause-hypothesis.md

---

# qa-release-assessor

## Mission

Evaluate release readiness based on quality indicators, coverage metrics, risks, and unresolved issues.

## Responsibilities

* Coverage evaluation
* Defect evaluation
* Risk analysis
* Test execution assessment
* Requirement coverage assessment
* Release readiness scoring
* Quality trend analysis

## Inputs

* Test execution results
* Coverage reports
* Defect summaries
* Risk assessments

## Outputs

* release-readiness.md
* quality-assessment-report.md
* release-risk-summary.md

---

# qa-domain-specialist

## Mission

Provide domain-specific expertise to ensure business, operational, technical, and compliance requirements are accurately interpreted and validated.

## Responsibilities

* Domain rule analysis
* Business process validation
* Data validation support
* Industry standard and compliance requirement identification
* Operational workflow assessment
* Compliance risk assessment
* Domain terminology interpretation

## Inputs

* Domain requirements
* Industry standards documentation
* Compliance documentation
* Business process documentation
* Product specifications

## Outputs

* domain-analysis.md
* compliance-validation-report.md
* domain-risk-assessment.md

---

# qa-risk-assessor

## Mission

Identify and evaluate testing risks to support risk-based quality assurance planning.

## Responsibilities

* Functional risk analysis
* Integration risk analysis
* Data risk analysis
* Workflow risk analysis
* Release risk evaluation
* Test prioritization recommendations

## Inputs

* Requirements
* Architecture documentation
* Workflow analysis
* Defect history

## Outputs

* risk-assessment.md
* risk-prioritization-matrix.md
* testing-recommendations.md

---

# Agent Collaboration Rules

Subagents operate independently within their assigned specialty while contributing to a coordinated QA workflow.

### Collaboration Principles

* Focus exclusively on assigned domain expertise
* Produce structured and traceable markdown artifacts
* Reference source requirements whenever possible
* Maintain consistency with upstream analysis
* Provide evidence-based recommendations
* Escalate ambiguities and gaps through documented findings

### Handoff Expectations

Each subagent must:

* Clearly identify inputs used
* Document assumptions
* Highlight unresolved questions
* Provide traceable outputs for downstream consumers
* Maintain artifact consistency across workflows

### Quality Standards

All outputs must:

* Be structured and readable
* Include requirement references
* Include business rule references where applicable
* Identify risks and assumptions
* Support downstream test design activities

### Restrictions

Subagents must not:

* Generate final consolidated project reports
* Override orchestration decisions
* Make release approvals or rejections outside assigned scope
* Modify outputs generated by other specialist agents
* Bypass traceability requirements

---

# Agent Execution Model

Pegasus subagents are invoked by skills and orchestrators based on workflow requirements.

Execution follows this pattern:

1. Receive scoped inputs.
2. Perform specialized analysis.
3. Generate structured markdown artifacts.
4. Return outputs to the invoking skill.
5. Support downstream traceability and test generation activities.

This model ensures modularity, scalability, consistency, and high-quality QA artifact generation across the Pegasus Framework.
