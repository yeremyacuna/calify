# 🌿 Calify — Git Branching Strategy

**Status:** Adopted project workflow. No Git branch alone represents a production deployment.

## Branch Model

```mermaid
gitGraph
    commit id: "Documentation baseline"
    branch v2
    checkout v2
    commit id: "V2 planning"
    branch feature/v2-example
    checkout feature/v2-example
    commit id: "Small implementation"
    checkout v2
    merge feature/v2-example
    checkout main
    merge v2 id: "Approved release"
```

The Mermaid diagram is illustrative; it is **not** an exact record of GitHub history or existing releases.

<div align="center">
<table align="center">
<thead><tr><th align="center">Branch</th><th align="center">Purpose</th><th align="center">Merge Rule</th></tr></thead>
<tbody>
<tr><td align="center"><code>main</code></td><td align="center">Public stable project state and approved releases</td><td align="center">Only reviewed changes and accepted releases</td></tr>
<tr><td align="center"><code>v2</code></td><td align="center">Calify V2 integration branch</td><td align="center">Reviewed PRs from feature and fix branches</td></tr>
<tr><td align="center"><code>feature/v2-*</code></td><td align="center">One scoped V2 feature</td><td align="center">PR to <code>v2</code> after tests</td></tr>
<tr><td align="center"><code>fix/v2-*</code></td><td align="center">V2 defect correction</td><td align="center">PR to <code>v2</code> after regression tests</td></tr>
</tbody>
</table>
</div>


No dedicated `v1` branch is necessary for the current published documentation baseline. The personal V1 production Apps Script source is **not** represented as source code in this public repository yet.

## Workflow

1. Create a scoped branch from `v2`.
2. Implement one change with English code comments and safe example data.
3. Run static checks, tests, and privacy review.
4. Open a Pull Request targeting `v2`.
5. Review the diff and update docs/changelog.
6. Merge after checks pass.
7. Promote a release to `main` only after isolated staging tests and explicit approval.

## Commit Style

Use Conventional Commits:

```text
docs(calify): clarify architecture diagrams
feat(api): validate score submissions
fix(shortcut): handle missing assessments
test(backend): cover duplicate score writes
chore(ci): add staging checks
```

A project initialization commit traditionally uses `chore: initial commit` or `Initial commit`; existing history is kept intact rather than rewritten merely for cosmetic naming.

## Releases

Version labels and tags follow a deliberate release policy. A tag must point to tested, publishable source—not to unverified personal production code.
