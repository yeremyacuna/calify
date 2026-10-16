# Calify — Architecture Baseline

## Status and scope

This document distinguishes **confirmed V1 design**, **partially inspected source**, and **V2 proposal**. Private identifiers, endpoints and credentials are intentionally omitted.

## V1 — Confirmed high-level integration

```text
Apple Shortcuts (iOS)
    -> HTTP request / JSON
    -> Google Apps Script Web App
    -> Google Sheets Grade Entry
    -> Control calculations
    -> Dashboard presentation
```

Existing user-managed trackers have the four-tab organization:

1. `Dashboard`
2. `Grade Entry`
3. `Control`
4. `Settings`

The `Grade Entry` ledger uses fourteen columns (A–N). Its data and score rules are not interchangeable with generic examples. At least one course has a distinct score-column heading; backend assumptions must be tested rather than inferred from display labels.

## Legacy backup — Source-inspected

A historical single-file Apps Script implementation exposes:
- `doGet()` service metadata.
- `doPost(e)` with `listCourses`, `listPending`, `recordScore`, and `markCompleted`.
- Script-property token comparison.
- Script-wide locking for write operations.
- Spreadsheet reads/writes and JSON responses.

Historical risks to investigate in the active backend:
- Completed records being changed by a stale or repeated request.
- Descriptive assessment IDs colliding.
- Empty/missing scores being coerced to zero.
- Partial writes and rollback limitations.
- Ambiguous authorization and secrets handling.

**These risks are confirmed or inferred only for the historical backup, not automatically for active Production.**

## Active production — Inventory only

The current Apps Script project exposes source file names such as `api.gs`, `auth.gs`, `config.gs`, `courseService.gs`, `assessmentService.gs`, `sheetRepository.gs`, `tests.gs`, and parallel `*Notes.gs` modules.

The source contents and deployed version boundaries still need full verification before modifying or publishing any backend code.

## V2 — Target architecture

```text
           iOS Shortcut        Web / PWA
                  \             /
                   API contract
                        |
             Validation + authorization
                        |
               Assessment services
                        |
               Google Sheets adapter
                        |
               User-owned trackers
```

The initial public distribution target is **user-owned/self-hosted**, not shared use of the personal production account or token. A hosted multi-user design is optional and requires a separate identity and tenant-isolation architecture.

## Source of truth and deployment

- During recovery: live Apps Script and the original iOS Shortcut are read-only baselines.
- After code recovery: Git becomes the reviewed source of truth for changes.
- CI should test untrusted contributions without access to deployment credentials.
- Staging deployments must be isolated from personal production.
- Production releases require explicit approval, tests, and rollback documentation.

See [Roadmap](ROADMAP.md) and [Shortcut V1 audit](audits/SHORTCUT_V1.md).
