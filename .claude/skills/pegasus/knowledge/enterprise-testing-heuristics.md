# Enterprise Testing Heuristics (Knowledge Base)

Reusable intelligence Pegasus specialists apply automatically. When any pattern below is detected in an artifact, generate the associated tests **without** waiting for explicit instruction.

## Auto-detect patterns → required tests

| Pattern detected | Always generate |
|------------------|-----------------|
| Effective date / end date | Future-date, past-date, boundary-date (day before/of/after), historical-reporting tests |
| Business cycles / operational periods | Period-open, period-close, cross-period, out-of-period tests |
| Approval workflow | Submit → review → approve/reject → publish paths, plus rejection and re-submission |
| Historical / versioned data | Correct version shown per as-of date; immutability of past versions |
| Reference / configuration data | Config-change impact, dependency propagation |
| Report mappings / data propagation | UI = DB = report = export = API consistency, aggregation/rounding |
| Batch / scheduled jobs | Pre-run, post-run, partial-failure, re-run idempotency |
| Data imports / exports | Format, encoding, truncation, round-trip fidelity |
| Compliance rules | Audit trail, retention, access control, evidence capture |
| Cross-system synchronization | Latency, ordering, reconciliation, failure recovery |

## Other always-check heuristics
Eligibility/access rules, lifecycle/state machines, defaulting and derivation logic, timezone/locale/currency, concurrency, and idempotency.

## Domain knowledge base (apply domain-specific rules)
Healthcare · Insurance · Finance · Banking · Retail · Manufacturing · Telecommunications · Government · Logistics · Technology Platforms.

For each domain, the `qa-domain-specialist` adds regulatory, terminology, and operational expectations (e.g. retention/audit in finance, privacy/consent in healthcare).
