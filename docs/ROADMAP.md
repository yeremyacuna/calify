# Calify V2 — Engineering Roadmap

**Status:** Proposed and versioned planning baseline. No V2 feature is considered implemented solely because it appears here.

## Goals

- Preserve the existing personal V1 and all user-owned academic records.
- Recover the actual production Apps Script source and audit the iOS Shortcut.
- Create a safe, professional GitHub workflow with no embedded secrets.
- Resolve verified security, integrity, and maintainability risks.
- Provide a reusable self-hosted edition for students.
- Develop an iOS V2 experience and, later, a mobile-friendly web/PWA client.
- Integrate a long-term JavaScript and backend learning track into development.

## Delivery phases

| Phase | Scope | Learning track | Exit criteria |
| --- | --- | --- | --- |
| **00 — Recovery & Audit** | Inventory current Shortcut and Apps Script; extract source read-only; document data boundaries. | JavaScript, Apps Script, HTTP, JSON, signed Shortcut format. | V1 behavior documented; all production source recovered or explicitly marked missing. |
| **01 — Repository Foundation** | Organize source, README, docs, changelog, templates, Git workflow and safe backup strategy. | Git, branches, conventional commits, Node.js, clasp. | Reproducible local setup, secret scan, reviewed baseline, no private data committed. |
| **02 — Backend Hardening** | Review validation, authorization, score state transitions, stable identifiers, duplicate requests, failures and consistency. | API design, error handling, state machines, idempotency. | Automated tests cover critical writes and reject invalid or stale requests. |
| **03 — CI/CD & Staging** | Introduce linting, testing, staging deployments, release gates and rollback. | GitHub Actions, CI/CD, test isolation, release management. | Production deployments require explicit approval; staging tests pass. |
| **04 — Public Configuration** | Separate personal and public settings, build user-owned setup and document permissions. | Configuration, secrets, OAuth fundamentals, least privilege. | A sample student can configure an isolated demo without production data. |
| **05 — iOS Shortcut V2** | Improve course/assessment selection, validation, previews, confirmations, feedback, and failure recovery. | Apple Shortcuts, mobile UX, HTTP client integration. | Real-device testing passes; personal V1 remains available and unchanged. |
| **06 — Web / PWA** | Implement mobile-first cross-platform interface against the versioned contract. | Web frontend, accessibility, API clients, responsive UX. | Functional, accessible demo using staging credentials only. |
| **07 — Public Release** | Publish clean sample assets, documentation, installation steps, verified releases and maintenance policy. | Open-source hygiene, semantic versioning, documentation. | Reproducible safe installation and acceptance checklist. |
| **08 — Multi-user Evaluation** | Assess hosted auth, tenant isolation, database, costs, monitoring, and scaling based on validated demand. | System design, scalability, operations, security. | Architecture decision recorded; implementation optional. |

## Non-negotiable safeguards

- Never upload original signed personal Shortcuts, access tokens, OAuth refresh credentials, production deployment URLs, real grade data, or personal course spreadsheet identifiers.
- Store configuration examples with placeholders such as `YOUR_SPREADSHEET_ID` and `YOUR_WEB_APP_URL`.
- Do not modify the canonical approved tracker books or deploy to production during recovery.
- A numeric score of **0** is valid; a blank score means pending. Preserve this distinction.
- Do not overwrite a completed assessment without an explicitly authorized correction workflow.
- Prevent duplicate score submissions and handle concurrent writes.
- Distinguish actual completed grades from projections.
- Do not generalize one course's grading weights or components to unrelated courses.
- Require staging, tests, and a rollback plan before production changes.

## Release acceptance checklist

- [ ] Production source and manifest recovered and reviewed.
- [ ] Shortcut workflow decoded and actions audited without exposing sensitive values.
- [ ] API contract and supported tracker schema documented.
- [ ] No credentials, production IDs, or academic records in public artifacts or Git history.
- [ ] Valid-zero, pending, duplicate, completed, validation and failure cases tested.
- [ ] Staging separated from personal production trackers.
- [ ] Legacy personal Shortcut preserved.
- [ ] Public install/setup tested with demo-only data.
- [ ] CI checks and controlled release process documented and passing.
- [ ] Rollback rehearsed.
- [ ] Learning notes and practical examples delivered for each relevant phase.

## Collaboration and learning workflow

For every development increment:
1. **Learn:** explain technology, terminology, and background.
2. **Inspect:** identify how the real Calify code uses the concept.
3. **Practice:** complete a focused example or exercise.
4. **Implement:** propose a small change with clear acceptance criteria.
5. **Test:** demonstrate valid cases and edge cases.
6. **Review:** inspect the diff and its security implications.
7. **Commit:** use meaningful Conventional Commit messages.
8. **Document:** update learning notes and changelog.

## Repository strategy

The existing public `yeremyacuna/calify` repository is the official public project. A separate private development/recovery repository may be created later after ownership and permission decisions. Secrets must not be included even in the private repository.

The preferred long-term **Source of Truth** is reviewed Git history. During initial recovery, Apps Script remains the live reference and only read-only extraction is permitted. Automatic pull/diff checks may be used as a temporary bridge. No automatic deployment of production changes is authorized.

## Change control

Reprioritization is allowed. Major architectural choices must be documented as Architecture Decision Records (ADRs) with context, trade-offs, and consequences. This roadmap is a living plan, not a claim that features have shipped.
