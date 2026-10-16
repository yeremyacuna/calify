<div align="center">

# Calify

**A privacy-first academic grade tracker built with Apple Shortcuts, Google Apps Script, and Google Sheets.**

**Status:** V1 recovery and V2 planning · **Public release:** not yet available

[Roadmap](docs/ROADMAP.md) · [Architecture](docs/ARCHITECTURE.md) · [Shortcut audit](docs/audits/SHORTCUT_V1.md) · [iOS V2 design](docs/SHORTCUT_V2_DESIGN.md) · [Learning path](docs/learning/README.md) · [Security](SECURITY.md)

</div>

---

## Overview

Calify is an independent software engineering project focused on making academic assessment tracking easier, clearer, and more reliable. Its existing personal workflow connects an iOS Shortcut to a Google Apps Script backend that reads and updates course-specific Google Sheets trackers.

Calify V2 aims to preserve the working personal V1 while preparing a reusable, safely configurable edition for other students.

> **Important:** The working personal Shortcut and production backend have **not** been published here. No active credentials, personal spreadsheet IDs, real grades, or production webhook URLs belong in this repository. The public project is currently in a documentation and recovery phase.

## Current architecture

```text
Apple Shortcuts (personal iOS client)
              |
         HTTPS / JSON
              |
Google Apps Script (personal API)
              |
Google Sheets (course-specific trackers)
    Dashboard | Grade Entry | Control | Settings
```

The established tracker layout contains exactly four sheets, with `Grade Entry` acting as the activity and score ledger. Detailed rules are course-specific and must not be copied blindly across trackers.

## Target architecture — Calify V2

```text
           iOS Shortcut        Web / PWA (planned)
                \               /
                 Versioned API contract
                          |
               Backend / services
                          |
                Google Sheets adapter
                          |
              User-owned grade trackers
```

**Delivery approach:** a self-hosted, individually configured public edition first; a centralized multi-user service only after authentication, isolation, and operational requirements are validated.

## Technology stack

- **Existing:** JavaScript, Google Apps Script, Google Sheets, HTTP, JSON, Apple Shortcuts.
- **Development and recovery:** Git, GitHub, Node.js tooling, `clasp`.
- **Planned:** automated tests, GitHub Actions, CI/CD, and a responsive PWA.

Only existing or expressly planned components are listed; a PWA or multi-user service is not yet implemented.

## Repository structure

```text
calify/
├── README.md
├── SECURITY.md
└── docs/
    ├── ARCHITECTURE.md
    ├── ROADMAP.md
    ├── audits/
    │   └── SHORTCUT_V1.md
    └── learning/
        └── README.md
```

The repository will evolve toward an organized monorepo with `apps/`, `backend/`, `packages/`, `tests/`, and `.github/workflows/` when verified code is ready. Empty placeholder directories and sensitive production exports will not be added merely for appearances.

## Project principles

1. **Privacy by default:** users configure their own Google account, trackers, and credentials.
2. **Backward compatibility:** never overwrite the working personal Shortcut or approved trackers as part of public development.
3. **Testable releases:** staging and regression testing before production changes.
4. **Learning by building:** each phase includes practical JavaScript/backend concepts and reusable learning notes.
5. **Transparent status:** distinguish current behavior, inspected evidence, planned functionality, and unverified assumptions.

## Getting started

Installation instructions will be published after the backend and Shortcut have been audited, sanitized, and tested on an isolated sample tracker.

**Do not reuse anyone else's API tokens, deployed endpoints, or spreadsheet IDs.**

## Documentation

- [V2 roadmap and acceptance criteria](docs/ROADMAP.md)
- [System architecture](docs/ARCHITECTURE.md)
- [V1 Shortcut audit](docs/audits/SHORTCUT_V1.md)
- [Proposed iOS Shortcut V2 design](docs/SHORTCUT_V2_DESIGN.md)
- [Learning notes and study workflow](docs/learning/README.md)
- [Security policy](SECURITY.md)

## Branding

The official icon and wordmark are **pending review**. Concept artwork is not a production asset and will be added only after approval.

## License

A public software license has not yet been selected. Do not assume permission to redistribute unpublished production code.

---

Created as a practical software engineering and learning project.
