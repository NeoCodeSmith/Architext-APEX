# Security Policy

## Scope

Architext APEX is a documentation repository. It contains no executable code, services, or APIs.

This security policy applies to:

- The content of the standards documents themselves (accuracy of security-related constraints)
- The GitHub repository configuration

---

## Reporting a Security Issue in the Standard

If you identify a constraint in [`SYSTEM_CONSTRAINTS.md`](SYSTEM_CONSTRAINTS.md) or [`ARCHITECTURE_RISK_SCAN.md`](ARCHITECTURE_RISK_SCAN.md) that:

- Contains incorrect security guidance
- Omits a well-documented security failure mode
- Could mislead engineers into an insecure design

Please report it via a **private GitHub Security Advisory** rather than a public issue, especially if the gap could be exploited before a correction is published.

To file a private advisory:

1. Go to the [Security tab](https://github.com/NeoCodeSmith/Architext-APEX/security) of this repository
2. Click **"Report a vulnerability"**
3. Describe the affected section, the current wording, the risk, and the proposed correction

---

## Response Timeline

| Stage | Target |
|---|---|
| Acknowledgement | Within 48 hours |
| Assessment | Within 7 days |
| Correction published | Within 14 days for confirmed issues |

---

## Security Constraints in the Standard

The standard covers security-relevant engineering constraints across:

- **Section 2** — API Safety & Idempotency (input validation, write safety)
- **Section 3** — Error Handling (information leakage through error messages)
- **Section 6** — Configuration & Secrets (secrets management, startup validation)
- **Section 8** — Dependency Discipline (supply chain failure modes)

If you believe any of these sections are incomplete or incorrect, use the process above.

---

## Out of Scope

The following are out of scope for this security policy:

- Vulnerabilities in GitHub's own platform
- Issues with third-party tools referenced (but not distributed) in this repository
- General security questions about systems you are building (use the paid scan offering for that)
