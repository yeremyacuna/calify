# Security Policy

Calify is currently in an early public documentation phase. No personal production deployment or executable public release is advertised or supported here.

## Reporting security concerns

Please avoid posting live credentials, authentication headers, deployment URLs, academic records, or personally identifying information in public issues. Use a private reporting channel provided by repository maintainers if one becomes available.

## Sensitive information policy

Never commit or distribute:
- API tokens, Google OAuth refresh tokens, private keys, `~/.clasprc.json`, or local environment files.
- Private production endpoint URLs or user spreadsheet IDs.
- Raw personal Shortcuts or exported configurations containing secrets.
- Actual academic grades, student information, or private spreadsheet snapshots.
- Production logs that may include request bodies or credentials.

Use explicit placeholders and synthetic example data instead.

## Production safeguards

- Keep the working personal V1 unchanged during recovery.
- Use a separate staging API and synthetic tracker for testing.
- Protect successful score submissions against accidental duplicate or stale writes.
- Require explicit deployment approval and a tested rollback strategy.
- Apply least-privilege permissions and review sharing settings.

## Public release gate

A Shortcut or backend source must not be labeled public-ready until independently checked for sensitive values, validated with tests, and documented for self-hosted use.
