# 🔐 Calify — Security & Privacy Policy

> **Current scope:** documentation-only public repository. There is no publicly supported executable release yet.

## Security Policy vs. License

This file defines how to handle sensitive information and report potential security problems. It is **not** an open-source license. The repository license will be defined separately once distribution decisions are finalized.

## What Must Never Be Published

- API tokens, private keys, OAuth credentials, password material or authentication headers.
- Maintainer-owned production deployment URLs, webhook endpoints and spreadsheet identifiers.
- The original personal `.shortcut` or unreviewed signed exports.
- Real student grade records or private workbook backups.
- Configuration files containing private deployment IDs (including `.clasp.json` when tied to the personal project).
- Raw production logs, debugging exports or metadata that could expose access details.

Use synthetic data and placeholders only.

## User Data Boundaries

The first public target is a **self-hosted/user-owned** setup: students configure their own deployment and academic trackers. Calify must never provide external users access to the maintainer's personal token, production API or private academic records.

## Vulnerability Reporting

Do **not** post sensitive evidence in a public GitHub Issue. Use GitHub's private vulnerability reporting feature if the repository maintainer has enabled it. Otherwise, request an appropriate confidential reporting channel without including secrets in the initial message.

## Safe Development Requirements

- Isolate staging from production and use dummy data.
- Validate all write requests on the server.
- Protect completed assessments against accidental overwrite.
- Handle duplicate requests and ambiguous timeout outcomes.
- Keep credentials out of source control, including private repositories.
- Require security review and testing before enabling deploy credentials in workflows.
- Verify every Shortcut release by scanning the actual final signed file.

## Public Release Gate

No production source, iOS shortcut, or runnable release is public-ready until reviewed and independently checked for privacy, correctness, and safe installation.

See [Architecture](ARCHITECTURE.md) and [Roadmap](ROADMAP.md).
