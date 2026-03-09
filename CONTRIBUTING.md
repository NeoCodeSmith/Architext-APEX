# Contributing to Architext APEX

Thank you for your interest in improving this standard.

Architext APEX is a living engineering document. Contributions are welcome when they improve the accuracy, completeness, or clarity of the constraints — not when they soften them.

---

## Principles for Contribution

Before submitting anything, understand what this standard is:

- **It is authoritative, not opinionated.** Every constraint must be grounded in documented failure modes.
- **It is a floor, not a ceiling.** Constraints define the minimum for production-readiness. They do not define the best possible system.
- **Vagueness is a defect.** Contributions that introduce ambiguity will be rejected.

---

## What Contributions Are Welcome

| Type | Description |
|---|---|
| **Corrections** | Factual errors in the constraints or risk scan |
| **Gap reports** | Production failure modes not covered by the current standard |
| **Clarity improvements** | Rewrites that sharpen precision without changing meaning |
| **New constraint domains** | Well-evidenced additions backed by real-world failure data |
| **Post-mortem references** | Links to public post-mortems that validate existing constraints |

## What Will Not Be Accepted

- Constraints based on personal preference rather than failure evidence
- Softening of existing constraints without documented justification
- Content that promotes specific vendors, tools, or paid services (other than the maintainer's own offering, which is clearly labelled)
- Tutorials, how-to guides, or opinionated "best practices"

---

## How to Contribute

### 1. Open an Issue First

For anything beyond a typo fix, open an issue before writing a PR.

Use the appropriate template:

- **Standard Gap** — for failure modes not covered
- **Correction** — for factual errors

This prevents wasted effort and allows discussion before implementation.

### 2. Fork and Branch

```bash
git clone https://github.com/NeoCodeSmith/Architext-APEX.git
cd Architext-APEX
git checkout -b fix/your-change-description
```

### 3. Write the Change

Follow the existing document structure exactly. For new constraints:

```markdown

## N. [Domain Name]

- [Constraint statement in imperative form — MUST / MUST NOT]
- [Second constraint]

Failure mode: [one sentence describing what breaks and how].
```

Every constraint must:

- Use `MUST` or `MUST NOT` (RFC 2119 language)
- State a clear failure mode
- Be falsifiable (you can verify compliance or non-compliance)

### 4. Test Locally

Install [markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli) and verify your changes pass:

```bash
npm install -g markdownlint-cli
markdownlint "**/*.md" --ignore node_modules
```

### 5. Submit a Pull Request

Use the PR template. The description must answer:

- What failure mode does this address?
- What evidence supports this constraint (incident report, post-mortem, benchmark)?
- Does this change existing behaviour or add new coverage?

---

## Style Guide

- Use present tense and imperative mood: *"Systems MUST emit..."* not *"Systems should emit..."*
- Keep failure modes to one sentence. If it takes more, split the constraint.
- No bullet point nesting beyond one level.
- Line length: 120 characters maximum.
- Headings: Title Case for H2, sentence case for H3 and below.

---

## Code of Conduct

All contributors are expected to follow the [Code of Conduct](CODE_OF_CONDUCT.md).

---

## Questions

Open a GitHub Discussion or an issue labelled `question`.
