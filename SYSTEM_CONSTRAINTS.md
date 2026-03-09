# ARCHITEXT APEX — SYSTEM CONSTRAINTS v1.0

Authoritative Engineering Standards

These constraints define non-negotiable defaults for production systems.
Any deviation requires explicit justification.

---

## 1. Database Design & p95 Latency

- All foreign keys MUST be explicitly indexed
- Composite indexes MUST exist for common query paths
- Serverless systems MUST use connection pooling
- `await` inside loops is prohibited

Failure mode: throughput collapse and latency amplification.

---

## 2. API Safety & Idempotency

- All external inputs MUST be schema-validated
- POST and PUT operations MUST be retry-safe
- Side effects before validation are prohibited

Failure mode: data corruption under retries.

---

## 3. Error Handling & Failure Modes

- Errors MUST be typed and classified
- Client (4xx) and system (5xx) errors MUST be distinguished
- Silent failures are prohibited

Failure mode: undetected production incidents.

---

## 4. Observability & Monitoring

Systems MUST emit:

- p50 / p95 / p99 latency metrics
- Traffic and error metrics
- Correlation IDs across boundaries

Failure mode: un-debuggable outages.

---

## 5. Performance Discipline

- A p95 latency target MUST be defined
- Unbounded concurrency is prohibited
- Systems MUST apply backpressure under load

Failure mode: cascading collapse at scale.

---

## 6. Configuration & Secrets

- Secrets MUST NOT appear in code or logs
- Configuration MUST be environment-driven
- Invalid configuration MUST fail startup

Failure mode: insecure or undefined runtime behavior.

---

## 7. Resource Management

- Timeouts, retries, and payload limits MUST be explicit
- Retries MUST be bounded and idempotent
- Unbounded growth is prohibited

Failure mode: resource exhaustion.

---

## 8. Dependency Discipline

- External systems are unreliable by default
- Every external call MUST define a timeout
- Fallback behavior MUST be explicit

Failure mode: total failure on partial outages.

---

## 9. Data & State Management

- The source of truth MUST be explicit
- State transitions MUST be traceable and auditable
- Hidden state mutations are prohibited

Failure mode: irreproducible bugs.

---

## 10. Documentation & Maintainability

- Non-obvious decisions MUST explain trade-offs
- Systems MUST be operable by on-call engineers
- Critical assumptions MUST be documented

---

## Final Statement

Any system violating these constraints is **not production-ready**.
