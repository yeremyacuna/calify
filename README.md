<div align="center">

<!-- Official Calify logo: reserved for an approved brand asset. -->

# Calify

### Privacy-first academic grade tracking & smart automation

**Record assessments, understand your progress, and keep control of your own academic data.**

[![Project Status](https://img.shields.io/badge/status-V2%20planning-F59E0B?style=for-the-badge)](docs/ROADMAP.md)
[![Platform](https://img.shields.io/badge/platform-iOS%20%7C%20Google%20Workspace-2563EB?style=for-the-badge&logo=apple&logoColor=white)](#-tech-stack)
[![Public Release](https://img.shields.io/badge/public%20release-not%20available-64748B?style=for-the-badge)](#-getting-started)

[**Architecture**](docs/ARCHITECTURE.md) · [**Roadmap**](docs/ROADMAP.md) · [**iOS V2 Design**](docs/design/IOS_SHORTCUT_V2.md) · [**Security**](docs/SECURITY.md) · [**Releases**](https://github.com/yeremyacuna/calify/releases)

</div>

---

## 📖 Overview

**Calify** is an independent software engineering project that connects **Apple Shortcuts**, a **Google Apps Script API**, and **Google Sheets** to simplify academic assessment tracking.

Its existing **personal V1** supports a real iOS-driven tracking workflow. The **V2 roadmap** focuses on reliability, secure configuration, an improved Shortcut experience, a self-hosted edition that other students can configure, and a possible cross-platform web/PWA client.

> [!IMPORTANT]
> **Project status:** this public repository currently contains documentation and a future-facing project scaffold—not an installable release. The functioning personal Shortcut, its credentials, personal trackers, and unreviewed production code are **not published** here.

## ✨ Project Capabilities

| Existing personal V1 | Planned Calify V2 |
|:---:|:---:|
| iOS Shortcut workflow | Guided Shortcut onboarding and improved UX |
| Google Apps Script backend | Audited, versioned API with stronger validation |
| Google Sheets grade tracking | Safe reusable tracker configuration |
| Course-specific grading calculations | Idempotent writes and staging tests |
| Grade entry and progress dashboards | Web/PWA client after backend stabilization |
| Personal production deployment | Reproducible public self-hosted installation |

**Existing** does not imply publicly downloadable. **Planned** means not shipped.

## 🏗️ Architecture

<div align="center">
  <img src="assets/diagrams/system-overview.svg" alt="Diagram showing Calify personal V1 architecture and the proposed V2 architecture" width="100%" />
</div>

The personal tracker schema uses four worksheets, in this order: **Dashboard → Grade Entry → Control → Settings**. The grading engine must respect each course's distinct evaluation rules, never substitute projections for actual results, and preserve a legitimate **zero** grade.

📄 [Explore the detailed architecture and Mermaid diagrams](docs/ARCHITECTURE.md)

## 🛠️ Tech Stack

<div align="center">

| **Current Integration** | **Development & Future Stack** |
|:-----------------------:|:------------------------------:|
| ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) | ![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white) |
| ![Google Apps Script](https://img.shields.io/badge/Google_Apps_Script-4285F4?style=for-the-badge&logo=google&logoColor=white) | ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white) |
| ![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white) | ![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=for-the-badge&logo=nodedotjs&logoColor=white) |
| ![Apple Shortcuts](https://img.shields.io/badge/Apple_Shortcuts-111827?style=for-the-badge&logo=apple&logoColor=white) | ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white) |
| ![HTTP / JSON](https://img.shields.io/badge/HTTP_%2B_JSON-475569?style=for-the-badge&logo=json&logoColor=white) | ![PWA](https://img.shields.io/badge/Web_%2F_PWA-planned-7C3AED?style=for-the-badge&logo=googlechrome&logoColor=white) |

</div>

GitHub Actions and the PWA are **planned**; badges indicate technologies in scope, not operational features. `clasp` is the planned source-recovery tool for Apps Script.

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
│   └── SECURITY.md
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

## 🗺️ Roadmap

<div align="center">

| Stage | Deliverable | Status |
|:-----:|:-----------:|:------:|
| 00 | Recover and audit V1 | In progress |
| 01 | Repository and source-control foundation | In progress |
| 02 | Harden backend and grading writes | Planned |
| 03 | CI/CD, staging and rollback | Planned |
| 04 | Public self-hosted configuration | Planned |
| 05 | iOS Shortcut V2 | Planned |
| 06 | Web/PWA client | Planned |
| 07 | Tested public release | Planned |
| 08 | Hosted multi-user evaluation | Future |

</div>

📄 [Detailed delivery roadmap, acceptance criteria, and learning objectives](docs/ROADMAP.md)

## 🔐 Security & Privacy

Calify follows a privacy-first approach. The public repository must never include live credentials, personal API endpoints, private spreadsheet IDs, the signed original personal Shortcut, or real student grades. Public releases require security review and independent validation.

📄 [Security policy and safe reporting](docs/SECURITY.md)

## 📚 Documentation

| Document | Purpose |
|:--------:|:-------:|
| [Architecture](docs/ARCHITECTURE.md) | V1 baseline, V2 target, diagrams, data rules |
| [Roadmap](docs/ROADMAP.md) | Milestones, release gates and required learning |
| [iOS Shortcut V2 Design](docs/design/IOS_SHORTCUT_V2.md) | Proposed UX and server integration |
| [Security Policy](docs/SECURITY.md) | Privacy, source publication and responsible reports |

**Internal-only material:** detailed private audits, personal Shortcut inventories, original production exports, and personal Learning Notes are maintained outside the public repository. They are not end-user documentation.

## 🤝 Contributions

Code contributions will open after a reviewed public source baseline and contribution rules are available. Until then, use [GitHub Issues](https://github.com/yeremyacuna/calify/issues) for feature suggestions without posting secrets or academic records.

## 📄 License

The open-source license has not yet been selected. **`SECURITY.md` is not a license.** No license is implied for unreleased production code.

---

<div align="center">

**Calify — Learn more. Track better.**

Built by [@yeremyacuna](https://github.com/yeremyacuna) · Software engineering & practical automation

</div>
