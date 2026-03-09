---
name: Standard Gap
about: Report a production failure mode not covered by the current standard
title: "[GAP] "
labels: gap-report
assignees: NeoCodeSmith
---

## Failure Mode

*Describe the production failure mode that is not currently covered by the standard.*

**What breaks:**

**Under what conditions:**

**At what scale / load:**

---

## Evidence

*Provide evidence that this is a real, documented failure pattern. Links to post-mortems, incident reports, or benchmark data are strongly preferred over anecdotal accounts.*

- [ ] Public post-mortem link:
- [ ] Benchmark / load test data:
- [ ] Internal incident (describe without sensitive detail):

---

## Proposed Constraint

*Write the constraint as it should appear in `SYSTEM_CONSTRAINTS.md`. Use RFC 2119 language (MUST / MUST NOT).*

```markdown
- [System / component] MUST [constraint].

Failure mode: [one sentence].
```

---

## Which Domain Does This Belong To?

- [ ] 1. Database Design & p95 Latency
- [ ] 2. API Safety & Idempotency
- [ ] 3. Error Handling & Failure Modes
- [ ] 4. Observability & Monitoring
- [ ] 5. Performance Discipline
- [ ] 6. Configuration & Secrets
- [ ] 7. Resource Management
- [ ] 8. Dependency Discipline
- [ ] 9. Data & State Management
- [ ] 10. Documentation & Maintainability
- [ ] New domain (describe below)

---

## Additional Context

*Anything else relevant to evaluating this gap.*
