# Calify Shortcut V1 — Initial File Audit

**Status:** Partial static inspection; action-by-action audit remains blocked until the signed Apple Archive payload can be extracted and parsed.

## Artifact details

- **Source:** privately provided personal `.shortcut` file.
- **Observed file size:** 34,783 bytes.
- **Magic bytes:** `AEA1` (Apple Encrypted Archive).
- **Profile:** 0 (signed, no content encryption).
- **Metadata:** signed archive authentication plist is readable.
- **Workflow actions:** not yet extracted or inspected.
- **Publication status:** **NOT APPROVED**.

No raw binary, signing identity data, token, script ID, spreadsheet ID, or private endpoint is retained in the public repository.

## Why a signed Shortcut is not inherently private

AEA profile 0 authenticates the archive; it does not encrypt the workflow. A compatible decoder can reveal embedded actions and constants. The personal export must not be assumed safe for public sharing.

## Required inspection before public release

- [ ] Decode the embedded workflow plist and preserve a private read-only baseline.
- [ ] Inventory all actions and control flow in execution order.
- [ ] Identify every HTTP method, URL, request body, header, authentication parameter and response field.
- [ ] Map course selection, assessment selection and grade entry paths.
- [ ] Audit errors, cancellation, network failures, retries and duplicate submissions.
- [ ] Search for hardcoded tokens, IDs, email addresses, personal URLs, sample grades and identifiable metadata.
- [ ] Design a user-configured onboarding flow with non-sensitive placeholders.
- [ ] Verify client/server authorization instead of merely deleting needed credentials.
- [ ] Generate a sanitized distribution artifact and compare action behavior.
- [ ] Test import, execution, failure modes, zero-score submissions, and real-device compatibility.
- [ ] Confirm the public artifact contains no personal data through an independent second scan.

## Acceptance criteria

Only a verified sanitized and properly signed/importable Shortcut may be distributed. The original active personal Shortcut and its existing backup remain unchanged.

## Limitations of this snapshot

The file envelope was inspected successfully, but this environment did not extract the compressed signed Apple Archive and underlying `WFWorkflowActions` data. Therefore this document does **not** claim to know the number of actions, request URLs, hardcoded credentials, or exact UX screens of the original.

## Next steps

1. Decode the original using a compatible Apple Archive decoder or macOS `aea` and `aa` tools.
2. Produce a **private** action inventory with sensitive values redacted before sharing details.
3. Audit the active Apps Script version against the observed Shortcut payload contract.
4. Build and test a sanitized template in staging.
