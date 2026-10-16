<div align="center">

<!-- Official Calify logo: reserved for an approved brand asset. -->

# Calify

### Academic grade tracking powered by iOS automation and Google Workspace

**Record academic assessments, automate grade entry, and visualize course progress.**

[![Project Status](https://img.shields.io/badge/status-V1%20documented-10B981?style=for-the-badge)](docs/ROADMAP.md)
[![Platform](https://img.shields.io/badge/platform-iOS%20%7C%20Google%20Workspace-2563EB?style=for-the-badge&logo=apple&logoColor=white)](#-tech-stack)
[![Public Release](https://img.shields.io/badge/public%20release-not%20available-64748B?style=for-the-badge)](#-getting-started)
[![GPLv3](https://img.shields.io/badge/license-GPLv3-3DA639?style=for-the-badge&logo=gnu&logoColor=white)](LICENSE)

[**Architecture**](docs/ARCHITECTURE.md) · [**Roadmap**](docs/ROADMAP.md) · [**iOS V2 Design**](docs/design/IOS_SHORTCUT_V2.md) · [**Security**](docs/PRIVACY_AND_SECURITY.md) · [**License**](LICENSE) · [**Releases**](https://github.com/yeremyacuna/calify/releases)

</div>

---

## 📖 Overview

**Calify** is an independent software engineering project that connects **Apple Shortcuts**, a **Google Apps Script API**, and **Google Sheets** to simplify academic assessment tracking.

Calify V1 is currently used as a functional personal iOS-to-Google-Workspace workflow. This repository documents the existing architecture while preparing a secure, reusable public distribution. Future features are documented separately in the [engineering roadmap](docs/ROADMAP.md).

> [!IMPORTANT]
> **Project status:** this public repository currently contains documentation and a future-facing project scaffold—not an installable release. The functioning personal Shortcut, its credentials, personal trackers, and unreviewed production code are **not published** here.

## ✨ Calify V1 — Core Capabilities

<div align="center">
<table align="center">
<thead><tr><th align="center">Component</th><th align="center">Existing Functionality</th></tr></thead>
<tbody>
<tr><td align="center"><strong>Mobile Client</strong></td><td align="center">Apple Shortcuts workflow for personal grade recording</td></tr>
<tr><td align="center"><strong>Web API</strong></td><td align="center">Google Apps Script endpoint handling JSON requests</td></tr>
<tr><td align="center"><strong>Academic Data</strong></td><td align="center">Google Sheets trackers with course-specific grading rules</td></tr>
<tr><td align="center"><strong>Grade Entry</strong></td><td align="center">Score recording and completion-based assessments</td></tr>
<tr><td align="center"><strong>Analytics</strong></td><td align="center">Calculated academic results and Dashboard summaries</td></tr>
</tbody>
</table>
</div>


The current personal workflow exists; its source code and original Shortcut are not public distribution artifacts.

## 🏗️ Architecture

<div align="center">
  <img src="assets/diagrams/system-overview.svg" alt="Calify V1 vertical architecture: iOS mobile client, Apps Script web API, and Google Sheets grade tracking" width="760" />
</div>

**Diagram type:** High-level System Architecture / Component Diagram (top-down). **Mobile** refers to the Apple Shortcuts iOS client; **Web API** refers to the server-side Google Apps Script Web App—not a separate browser frontend.

Each tracker uses four worksheets: **Dashboard → Grade Entry → Control → Settings**. Course-specific formulas distinguish pending scores from legitimate zero scores and actual results from projections.

📄 [Explore the detailed architecture and Mermaid diagrams](docs/ARCHITECTURE.md)

## 🛠️ Tech Stack

<div align="center">

<div align="center">
<table align="center">
<thead><tr><th align="center"><strong>Current Integration</strong></th><th align="center"><strong>Development Tooling</strong></th></tr></thead>
<tbody>
<tr><td align="center"><img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&amp;logo=javascript&amp;logoColor=black" /></td><td align="center"><img alt="Git" src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&amp;logo=git&amp;logoColor=white" /></td></tr>
<tr><td align="center"><img alt="Google Apps Script" src="https://img.shields.io/badge/Google_Apps_Script-4285F4?style=for-the-badge&amp;logo=google&amp;logoColor=white" /></td><td align="center"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&amp;logo=github&amp;logoColor=white" /></td></tr>
<tr><td align="center"><img alt="Google Sheets" src="https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&amp;logo=googlesheets&amp;logoColor=white" /></td><td align="center"><img alt="Node.js" src="https://img.shields.io/badge/Node.js-5FA04E?style=for-the-badge&amp;logo=nodedotjs&amp;logoColor=white" /></td></tr>
<tr><td align="center"><img alt="Apple Shortcuts" src="https://img.shields.io/badge/Apple_Shortcuts-111827?style=for-the-badge&amp;logo=apple&amp;logoColor=white" /></td><td align="center"><img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&amp;logo=githubactions&amp;logoColor=white" /></td></tr>
<tr><td align="center"><img alt="HTTP / JSON" src="https://img.shields.io/badge/HTTP_%2B_JSON-475569?style=for-the-badge&amp;logo=json&amp;logoColor=white" /></td><td align="center"><img alt="clasp" src="https://img.shields.io/badge/clasp-source%20recovery-4285F4?style=for-the-badge&amp;logo=google&amp;logoColor=white" /></td></tr>
</tbody>
</table>
</div>


</div>

GitHub Actions and `clasp` remain tooling planned for recovery and CI/CD. Badges do not imply that those pipelines are deployed.

## 📂 Project Structure

```text
calify/
├── .github/
│   ├── workflows/              # Future CI/CD pipelines
│   └── ISSUE_TEMPLATE/         # Issue templates
├── apps/
│   ├── ios-shortcuts/
│   │   ├── templates/          # Sanitized Shortcut sources (future)
│   │   └── releases/           # Verified distributable Shortcuts (future)
│   └── web/
│       ├── public/             # Web static assets (future)
│       └── src/                # Web/PWA source code (future)
├── backend/
│   └── apps-script/
│       ├── src/                # Reviewed public .gs modules (future)
│       └── tests/              # Backend tests (future)
├── packages/
│   ├── api-contracts/          # Shared API contract (future)
│   └── grading-engine/        # Evaluated shared calculation logic
├── config/
│   └── examples/              # Safe configuration examples (future)
├── assets/
│   ├── branding/              # Official logo pending approval
│   ├── diagrams/              # Public architecture diagrams
│   └── screenshots/           # Demo-only screenshots (future)
├── docs/
│   ├── api/
│   ├── design/
│   ├── decisions/
│   ├── guides/
│   ├── sheets/
│   ├── ARCHITECTURE.md
│   ├── ROADMAP.md
│   ├── PRIVACY_AND_SECURITY.md
│   ├── BRANCHING_STRATEGY.md
│   └── LICENSING.md
├── infra/
│   └── apps-script/           # Deployment configuration (future)
├── scripts/                   # Maintenance tooling (future)
├── tests/                     # Integration tests (future)
├── .gitignore
└── README.md
```

**Scaffold rule:** folders containing `.gitkeep` are intentionally reserved. They are not evidence that a feature has already been built.

## 🚀 Getting Started

A public installation is **not yet available**. Once the audited release is ready, each student will configure their own Google account, tracker, Apps Script deployment, and iOS client. No student will need access to the maintainer's private spreadsheets or production token.

You can inspect the current documentation locally:

```bash
git clone https://github.com/yeremyacuna/calify.git
cd calify
```

No functional installation command is provided until the public setup flow has been tested with synthetic data.

## 🗺️ Engineering Roadmap

Future development and version-specific designs are maintained outside the V1 overview to avoid presenting unfinished capabilities as shipped.

📄 [Explore the complete versioned roadmap and acceptance criteria](docs/ROADMAP.md) · [Branching Strategy](docs/BRANCHING_STRATEGY.md)

## 🔐 Security & Privacy

Calify follows a privacy-first approach. The public repository must never include live credentials, personal API endpoints, private spreadsheet IDs, the signed original personal Shortcut, or real student grades. Public releases require security review and independent validation.

📄 [Security policy and safe reporting](docs/PRIVACY_AND_SECURITY.md)

## 📚 Documentation

<div align="center">
<table align="center">
<thead><tr><th align="center">Document</th><th align="center">Purpose</th></tr></thead>
<tbody>
<tr><td align="center"><a href="docs/ARCHITECTURE.md">Architecture</a></td><td align="center">V1 baseline, V2 target, diagrams, data rules</td></tr>
<tr><td align="center"><a href="docs/ROADMAP.md">Roadmap</a></td><td align="center">Milestones, release gates and required learning</td></tr>
<tr><td align="center"><a href="docs/design/IOS_SHORTCUT_V2.md">iOS Shortcut V2 Design</a></td><td align="center">Proposed UX and server integration</td></tr>
<tr><td align="center"><a href="docs/PRIVACY_AND_SECURITY.md">Privacy &amp; Security Guidelines</a></td><td align="center">Privacy, source publication and responsible reports</td></tr>
<tr><td align="center"><a href="docs/BRANCHING_STRATEGY.md">Branching Strategy</a></td><td align="center">Main branch, V2 branch, feature branches and releases</td></tr>
<tr><td align="center"><a href="docs/LICENSING.md">GPLv3 Licensing Guide</a></td><td align="center">Copyleft, source distribution, attribution, and warranty terms</td></tr>
</tbody>
</table>
</div>


**Internal-only material:** detailed private audits, personal Shortcut inventories, original production exports, and personal Learning Notes are maintained outside the public repository. They are not end-user documentation.

## 🤝 Contributions

Code contributions will open after a reviewed public source baseline and contribution rules are available. Until then, use [GitHub Issues](https://github.com/yeremyacuna/calify/issues) for feature suggestions without posting secrets or academic records.

## 📄 License

**Calify is licensed under the [GNU General Public License v3.0 (GPL-3.0-only)](LICENSE).** Publicly released covered works may be used, modified, and redistributed under GPLv3 terms, including the obligation to provide corresponding source for distributed derivative versions. There is **no warranty**, subject to applicable law. GPLv3 permits forks and commercial redistribution; it does **not** prohibit cloning. The working personal Shortcut, unpublished production backend, user data, and credentials are **not included in this release**. See the [Licensing Guide](docs/LICENSING.md) for scope and compliance.

---

<div align="center">

**Calify — Learn more. Track better.**

Copyright © 2026 Yeremy Acuña ([@yeremyacuna](https://github.com/yeremyacuna)) · Licensed under [GNU GPLv3](LICENSE)

</div>
