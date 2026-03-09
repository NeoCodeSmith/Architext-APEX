# Architecture Risk Scan (Free)

This document identifies common production failure signals.

If three or more items apply, the system is not production-ready.

---

## 1. Database Risks

- Missing foreign key indexes
- No connection pooling in serverless
- Unbounded table growth

---

## 2. API Safety Risks

- No idempotency keys
- Missing request validation
- Writes before validation

---

## 3. Performance Risks

- `await` inside loops
- No p95 latency target
- Synchronous fan-out

---

## 4. Observability Risks

- No structured logs
- No error classification
- No correlation IDs

---

If you want a written verdict on your system:
Paid Architecture Risk Scans are available.
