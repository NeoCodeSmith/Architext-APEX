# Changelog

All notable changes to Architext APEX are documented here.

This project follows [Semantic Versioning](https://semver.org/):

- **MAJOR** — Breaking change to an existing constraint (meaning changes)
- **MINOR** — New constraint domain or risk signal added
- **PATCH** — Clarification, correction, or formatting improvement

Changes that soften an existing constraint are treated as **MAJOR** and require explicit rationale.

---

## [1.0.0] — 2026

### Added

- `SYSTEM_CONSTRAINTS.md` — 10 authoritative constraint domains covering:

  - Database design and p95 latency
  - API safety and idempotency
  - Error handling and failure modes
  - Observability and monitoring
  - Performance discipline
  - Configuration and secrets management
  - Resource management
  - Dependency discipline
  - Data and state management
  - Documentation and maintainability

- `ARCHITECTURE_RISK_SCAN.md` — Free self-assessment across 4 risk areas
- `REVIEW_OUTPUT_TEMPLATE.md` — Structured template for architecture verdict output
- `README.md` — Repository overview and quick-start guide
- `LICENSE.txt` — MIT license

---

## Upcoming

Items under consideration for v1.1:

- Constraint domain: **Deployment & Rollback** (zero-downtime deploys, canary gates, rollback SLA)
- Constraint domain: **Multi-Tenancy Isolation** (data leakage, noisy-neighbour, blast radius)
- Risk scan expansion: **Async / Queue Systems** (unbounded queues, poison messages, consumer lag)
- Public post-mortem references mapped to each constraint

To propose additions, open an issue with the `gap-report` label.
