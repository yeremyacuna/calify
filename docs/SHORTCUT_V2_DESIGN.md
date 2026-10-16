# Calify iOS Shortcut V2 — Proposed Design

**Status:** Design proposal only. The original signed personal Shortcut's actions have not yet been extracted, so this is not a verified description of V1 behavior.

## Target user flow

```text
Launch Calify
    |
Check local configuration
    |-- Missing -> Setup assistant -> Connection test
    |
Choose course (from user-configured API)
    |
List pending assessments
    |
Choose assessment
    |-- Score activity -> Enter grade -> Validate 0 <= score <= maximum
    |-- Completion activity -> Ask for completion confirmation
    |
Preview intended operation
    |
User confirms
    |
POST validated request (unique request ID)
    |
Server authorizes and checks current assessment state
    |-- Conflict/duplicate -> Explain without overwriting
    |-- Failure -> Explain and allow safe retry
    |-- Success -> Show receipt and optionally dashboard link
```

## User experience goals

- Minimal steps for returning users, clear first-time setup.
- Readable menus, full course names, assessment dates, and maximum scores.
- Proper treatment of a valid numeric zero and a missing score.
- Explicit confirmation before any write operation.
- Consistent result messages, with course and assessment context.
- Accessible text, feedback, and cancellation without side effects.
- Safe recovery from a network failure without blind repeated writes.

## Configuration principles

- Remove all personal values from the shareable template.
- Require the user to supply their own authorized API endpoint (or setup flow).
- Never embed the developer's production token, spreadsheets, grades, personal endpoints or user-identifying metadata.
- Do not turn an active secret into a simple public placeholder without designing a replacement authentication process.
- Validate the server independently; client-side checks are for user experience, not authorization.
- For a self-hosted edition, the student's own Apps Script project and Google Sheet are isolated from the maintainer's personal production account.
- Consider Apple Shortcuts import questions for initial setup, with explicit warnings that a locally entered secret may still be visible to someone who can inspect the installed Shortcut.

## API needs to confirm against active Production

- Course catalog and activity discovery.
- Activity IDs that remain stable and unambiguous.
- Data contract for scored versus completion-only tasks.
- Freshness/state checks on submitted grade updates.
- Idempotency for retries and duplicate taps.
- Consistent structured error categories.
- Authentication and permission model for user-owned installations.

Do not assume that historical Legacy API requests exactly match active Production.

## Test matrix

| Case | Expected behavior |
| --- | --- |
| Empty configuration | Guide user to setup, no API write |
| Network unavailable | Friendly failure, no misleading success |
| No pending assessments | Explicit empty state |
| Valid score = 0 | Record legitimate zero |
| Empty score | Reject or cancel without treating it as zero |
| Score greater than maximum | Reject |
| Already completed assessment | Do not silently overwrite |
| Duplicate request | Avoid duplicate side effect |
| Activity without a score | Completion-specific confirmation |
| Wrong or expired authentication | No write and actionable message |
| Cancelled confirmation | No write |
| Backend response mismatch | Report error and keep audit context |

## Publication requirements

The public file must:
1. Be reconstructed from reviewed action definitions, not distributed as a renamed private file.
2. Contain no hardcoded personal token, grade data, spreadsheet ID, or production webhook.
3. Be validly signed and importable by Apple Shortcuts.
4. Pass a second privacy scan after signing.
5. Pass real-device tests with a synthetic demo course.
6. Be released with a version, changelog, and installation documentation.

The original personal Shortcut and backups must remain unchanged until V2 has been validated.
