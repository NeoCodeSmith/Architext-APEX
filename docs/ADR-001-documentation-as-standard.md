# ADR-001: Documentation as Engineering Standard (Not a Tool or Linter)

- **Date**: 2026
- **Status**: Accepted
- **Deciders**: NeoCodeSmith (maintainer)

---

## Context

Engineering standards can be enforced in two ways:

1. **Tooling** — linters, static analysers, CI gates, framework guardrails
2. **Documentation** — written constraints that engineers read, understand, and apply

Most existing standards projects take approach (1). They produce tools that check surface-level properties: naming conventions, import order, type annotations. These tools are useful but incomplete.

The failure modes that actually destroy production systems — missing indexes, absent idempotency keys,
synchronous fan-out, no fallback on external calls — cannot be detected by a linter.
They require **engineering judgment applied at design time**.

Additionally, tooling:

- Is language and framework-specific (cannot cover polyglot systems)
- Can be bypassed with suppressions (`# noqa`, `// eslint-disable`)
- Creates a false sense of compliance (green CI ≠ production-ready)
- Requires maintenance as ecosystems change

---

## Decision

Architext APEX is a **documentation standard**, not a tool.

The constraints are written in natural language, structured by domain, and designed to be read by engineers — not executed by machines.

The standard is applied through:

- Self-assessment checklists (Architecture Risk Scan)
- Code review integration (reference relevant sections in PR reviews)
- Architecture decision templates (Review Output Template)
- Paid async scans (human expert applies the standard to your specific system)

---

## Rationale

A written standard:

- Works across all languages, frameworks, and deployment models
- Cannot be silenced by a suppression comment
- Forces engineers to understand the failure mode, not just satisfy a checker
- Remains accurate longer than tool-specific implementations
- Can be applied at design time — before any code exists

The goal is not a green CI badge. The goal is a system that does not fail in production.

---

## Consequences

- ✅ The standard is universally applicable regardless of tech stack
- ✅ Constraints are human-readable and explainable to non-engineers
- ✅ No tooling maintenance burden
- ⚠️ Compliance cannot be automatically verified — it requires human review
- ⚠️ Adoption depends on engineers reading and applying the standard deliberately
- ❌ No automated enforcement in CI pipelines (by design)

---

## Alternatives Considered

| Option | Reason Rejected |
|---|---|
| Build a linter/CLI tool | Language-specific, bypassable, requires ongoing maintenance, misses design-time failures |
| GitHub Action that checks for constraint violations | Same limitations as a linter; cannot evaluate design intent |
| Interactive web tool / SaaS | Adds infrastructure, cost, and maintenance overhead; the standard's value is in clarity, not interactivity |

---

## Review

This ADR should be revisited if:

- A reliable, language-agnostic method of automated constraint checking emerges
- Adoption data shows that documentation alone is insufficient for the target audience
