# Calify Engineering Learning Notes

The Calify project is both a real software product and a practical learning program. Notes must remain useful beyond the project itself.

## Structure for every learning topic

Create one Markdown note per topic using the following template:

1. **Concept:** precise definition and terminology.
2. **Why it matters:** general engineering uses, not just Calify.
3. **Prerequisites:** concepts to review first.
4. **How Calify uses it:** reference to relevant reviewed code.
5. **Minimal example:** clear, runnable code with English comments.
6. **Edge cases:** failure modes, validation and security.
7. **Practice exercises:** beginner, intermediate and applied.
8. **Self-check:** short questions with testable answers.
9. **Further reading:** authoritative references.
10. **What I learned:** concise reflection and linked commit or PR.

## Learning tracks by phase

| Phase | Main subjects | Practical exercises |
| --- | --- | --- |
| 00–01 | JavaScript fundamentals, Apps Script, HTTP/JSON, Git, clasp | Parse JSON; validate a score; explain an HTTP request; create a branch. |
| 02 | State transitions, error handling, idempotency, test doubles | Reject a completed write; prove zero is valid; prevent duplicate submissions. |
| 03 | GitHub Actions, CI/CD, staging, rollback | Run an automated test suite on a pull request. |
| 04 | Configuration, secrets, user authorization | Replace hardcoded IDs with placeholders and user-owned settings. |
| 05 | Apple Shortcuts, accessible user flows, API clients | Design and verify a score confirmation flow. |
| 06 | Web frontend, PWA, responsive accessibility | Build a small mobile-first course picker against mock data. |
| 07–08 | Release engineering, system design, multi-user security | Write an ADR comparing self-hosted and multi-user approaches. |

## Conventions

- All repository documentation, examples, identifiers, and code comments use **English**.
- Use straightforward explanations and define new technical terms precisely.
- Preserve practical examples that can be understood independently of Calify.
- Never use real production tokens, endpoints, spreadsheet IDs, or actual student records in examples.
- Prefer small, testable commits and link them from the learning notes.

## Available lessons

- [Lesson 01 — JavaScript, JSON, and Input Validation](phase-00/01-javascript-json-and-validation.md)

## Initial study queue

- [ ] JavaScript objects, arrays, functions and scope.
- [ ] JSON serialization and HTTP request anatomy.
- [ ] Apps Script services and `.gs` files.
- [ ] Git branches, pull requests, Conventional Commits.
- [ ] Error handling, validation and trust boundaries.
- [ ] Idempotency and concurrency in score recording.
- [ ] Testing strategy and CI/CD fundamentals.
