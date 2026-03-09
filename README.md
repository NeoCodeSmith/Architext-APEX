<div align="center">

# Architext APEX

**Authoritative engineering standards for production software.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE.txt)
[![Standard Version](https://img.shields.io/badge/standard-v1.0-brightgreen.svg)](SYSTEM_CONSTRAINTS.md)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Markdown Lint](https://github.com/NeoCodeSmith/Architext-APEX/actions/workflows/markdown-lint.yml/badge.svg)](https://github.com/NeoCodeSmith/Architext-APEX/actions/workflows/markdown-lint.yml)

*Stop guessing. Start building systems that hold.*

</div>

---

## What Is Architext APEX?

Architext APEX is a **public engineering standard** — a set of non-negotiable constraints that define whether a system is truly production-ready.

It is not a tutorial. It is not blog content. It is a deterministic framework for identifying failure modes before they reach production.

Systems that violate these constraints will fail at scale. This standard tells you exactly where and why.

---

## Table of Contents

- [The Problem This Solves](#the-problem-this-solves)
- [Quick Start](#quick-start)
- [Documents](#documents)
- [The 10 Constraint Domains](#the-10-constraint-domains)
- [Architecture Risk Scan](#architecture-risk-scan)
- [Paid Offering](#paid-offering-1)
- [Contributing](#contributing)
- [License](#license)

---

## The Problem This Solves

Most systems fail in production for the same predictable reasons:

| Root Cause | Example Failure |
|---|---|
| Missing DB indexes on foreign keys | p95 query time: 2s → 40s under load |
| No connection pooling in serverless | Lambda cold-start cascades |
| `await` inside loops | Throughput collapses at 50 concurrent users |
| Writes before validation | Corrupt data under API retry storms |
| No structured logs or correlation IDs | Outage takes 6 hours to debug |
| Unbounded retries without backoff | Thundering herd brings down dependencies |

Architext APEX gives every engineer a **single checklist** that catches these failures at design time — not at 3am.

---

## Quick Start

### Self-Assessment

1. Read [`SYSTEM_CONSTRAINTS.md`](SYSTEM_CONSTRAINTS.md) — the 10 non-negotiable constraint domains
2. Run [`ARCHITECTURE_RISK_SCAN.md`](ARCHITECTURE_RISK_SCAN.md) against your system
3. Count how many risk signals apply

> **If 3 or more signals apply → your system is not production-ready.**

### In Code Review

Drop the relevant constraint section into any PR that touches infrastructure, APIs, or data models. Use it as a review checklist, not a suggestion list.

### In System Design

Use [`REVIEW_OUTPUT_TEMPLATE.md`](REVIEW_OUTPUT_TEMPLATE.md) to structure architecture decisions and communicate verdicts to stakeholders.

---

## Documents

| Document | Purpose |
|---|---|
| [`SYSTEM_CONSTRAINTS.md`](SYSTEM_CONSTRAINTS.md) | The 10 authoritative constraint domains — start here |
| [`ARCHITECTURE_RISK_SCAN.md`](ARCHITECTURE_RISK_SCAN.md) | Free self-assessment: identify production failure signals |
| [`REVIEW_OUTPUT_TEMPLATE.md`](REVIEW_OUTPUT_TEMPLATE.md) | Template for communicating architecture verdicts |
| [`docs/ADR-001-documentation-as-standard.md`](docs/ADR-001-documentation-as-standard.md) | Why this exists as a document standard, not a linter or tool |

---

## The 10 Constraint Domains

A summary of what [`SYSTEM_CONSTRAINTS.md`](SYSTEM_CONSTRAINTS.md) covers in full:

| # | Domain | Key Rule | Failure Mode |
|---|---|---|---|
| 1 | **Database Design** | All FK's indexed; connection pooling mandatory | Throughput collapse |
| 2 | **API Safety** | Schema-validate all inputs; POST/PUT must be idempotent | Data corruption under retries |
| 3 | **Error Handling** | Typed, classified errors; no silent failures | Undetected incidents |
| 4 | **Observability** | p50/p95/p99 metrics + correlation IDs across all boundaries | Un-debuggable outages |
| 5 | **Performance** | p95 target defined; no unbounded concurrency | Cascading collapse at scale |
| 6 | **Configuration & Secrets** | Env-driven config; invalid config must fail startup | Insecure runtime behaviour |
| 7 | **Resource Management** | Explicit timeouts, retries, and payload limits | Resource exhaustion |
| 8 | **Dependency Discipline** | Every external call has a timeout and explicit fallback | Total failure on partial outages |
| 9 | **Data & State** | Explicit source of truth; auditable state transitions | Irreproducible bugs |
| 10 | **Documentation** | Non-obvious decisions explain trade-offs | Systems operable only by their authors |

---

## Architecture Risk Scan

The [`ARCHITECTURE_RISK_SCAN.md`](ARCHITECTURE_RISK_SCAN.md) covers four risk areas:

```text
Database Risks      → indexes, pooling, unbounded growth
API Safety Risks    → idempotency, validation, write ordering
Performance Risks   → async discipline, latency targets, fan-out
Observability Risks → structured logs, error classification, correlation IDs
```text

**Score your system:**
- 0–2 signals → Proceed with awareness
- 3–5 signals → Not production-ready — remediate before launch
- 6+ signals → Stop. Redesign before continuing.

---

## Paid Offering

I provide **async, written architecture risk scans** — a deterministic engineering verdict on your system.

**You submit:**
- Repository link or system diagrams
- Load expectations (RPS, data volume, concurrency)
- Deployment model (serverless, containerised, bare metal)

**You receive:**
- Full bottleneck register mapped to the 10 constraint domains
- Scalability score (Low / Medium / High)
- Failure-mode analysis with exact reproduction conditions
- Prioritised remediation plan
- Clear **Go / No-Go verdict**

This is not consulting-by-the-hour.
This is a deterministic engineering verdict — delivered in writing, with receipts.

> To request a scan, open an issue with the label `scan-request` or contact directly via GitHub.

---

## Contributing

Corrections and additions to the standard are welcome. Please read [`CONTRIBUTING.md`](CONTRIBUTING.md) before opening a PR.

All contributions must:

- Be grounded in documented failure modes (not opinion)
- Follow the existing constraint format
- Include a rationale referencing real-world incidents or post-mortems where possible

---

## License

MIT — see [`LICENSE.txt`](LICENSE.txt).

The standard is free to use, adopt, and build on. Attribution appreciated but not required.

---

<div align="center">

*Built by engineers who have debugged enough 3am outages to know what actually breaks.*

</div>
