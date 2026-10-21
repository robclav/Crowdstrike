# Agentic SOC Oversight Dashboard

<p align="center">
  <img src="docs/logo.png" alt="SOC Dashboard" width="120" />
</p>

<p align="center">
  <strong>Real-time videowall for SOC teams, built on CrowdStrike Falcon Foundry</strong>
</p>

<p align="center">
  <a href="https://www.crowdstrike.com/platform/falcon-foundry/"><img src="https://img.shields.io/badge/Falcon-Foundry-ff0000" alt="Falcon Foundry"></a>
  <img src="https://img.shields.io/badge/version-v0.7.137-blue" alt="Version">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License">
</p>

---

## 📖 Overview

**Agentic SOC Oversight Dashboard** is a [Falcon Foundry](https://www.crowdstrike.com/platform/falcon-foundry/) application designed as a *videowall* for SOC leads and managers. It consolidates key operational metrics for a modern SOC into a single view, with no console-hopping required.

Metrics are pulled live from the Falcon platform:

- 🚨 **Alerts REST API** — alert volume, severity, backlog, and age (primary source)
- 💻 **Devices API** — endpoint inventory, platform mix, sensor distribution
- 🔎 **NGSIEM / LogScale** — saved searches for ingestion rate, MITRE, and agent activity
- 🤖 **Charlotte AI** — credit usage and top consumers
- 🧰 **Fusion Workflows** — SOAR workflow executions

The dashboard auto-refreshes every ~1 minute. Each widget surfaces a status indicator:

- 🟢 **Green** — live data from the backend
- 🟡 **Yellow** — fallback / mock (API unavailable or empty tenant)

## 📸 Screenshots

<p align="center"><img src="docs/screenshots/01-dashboard-overview.png" alt="Dashboard Overview" width="900"></p>

## ✨ Widgets (15 total)

The dashboard is organized into 4 thematic rows:

| Row | Widgets |
|------|---------|
| **1. Threat Pulse** | Threat Timeline (24H) · Top Noisy Detections (7D) |
| **2. Threat Landscape** | SOC Capacity · Alert Backlog Trend (7D) · New Threats Pulse (1H) · Alert Age Distribution |
| **3. Operational** | Top AI Services (24H) · Dark Hours Monitoring · Agent Health · CrowdStrike Data Ingestion Rate · 3rd-Party Feed Silence |
| **4. Deep Analytics** | Sensor Hygiene · NIST 800-61 v3 IR Phases · MITRE ATT&CK Coverage (7D) · Top Impacted Hosts (24H) |

For a detailed description of each widget (what it shows, how to read it, which query feeds it) see **[docs/widget-guide.md](docs/widget-guide.md)**.

### Functional highlights

- **3rd-Party Feed Silence**: per-vendor color-coded list with 5 staleness tiers (<15m / ≥15m / ≥30m / ≥1h / ≥4h), built by combining `postAggregatesAlertsV2` over `source_vendors` with the latest `created_timestamp` per vendor.
- **MITRE ATT&CK Heatmap (7D)**: coverage of tactics and techniques detected from alerts.
- **NIST 800-61 v3 IR Phases**: tracking of analyst activity by response-cycle phase.
- **Dark Hours Monitoring**: off-hours activity heatmap (day-of-week × hour).
- **Mean Time Metrics**: MTTD / MTT / MTTR computed in LogScale.
- **Mock-data fallback** with a clearly visible banner and yellow dot when any source fails.

## 📦 Contents

```
soc-dashboard/
├── README.md                            ← this file
├── dist/
│   └── soc-dashboard-v0.7.137.tar.gz    ← app export, ready to import into Foundry
└── docs/
    ├── widget-guide.md                  ← detailed guide for the 15 widgets
    ├── logo.png
    └── screenshots/
```

> ℹ️ This repository ships **only the packaged bundle** (Foundry export). Development source code is not published here.

## 🚀 Installation

### Prerequisites

- A CrowdStrike Falcon tenant with **Falcon Foundry** enabled.
- Administrator permissions to install apps from the *App Manager*.
- Enabled API scopes (already declared in `manifest.yml`):
  - `alerts:read`
  - `incidents:read`
  - `detects:read`
  - `devices:read`
  - `host-group:read`
  - `workflow:read`
  - `message-center:read` *(for /xdr/cases)*
  - `cases:read`
  - `discover:read`
  - `zero-trust-assessment:read`
  - `foundry-pages:read` / `foundry-pages:write`
  - `app-logs:read` / `app-logs:write`
  - `ioc:read`
  - `cspm-registration:read`

### Steps

1. Download **[`dist/soc-dashboard-v0.7.137.tar.gz`](dist/soc-dashboard-v0.7.137.tar.gz)** from this repository.
2. In the Falcon console, open **Foundry → App Manager → Import app**.
3. Select the `.tar.gz` and confirm the import.
4. When finished, Foundry will launch the credential wizard. Provide an API Client with the scopes above.
5. **Deploy** and **Release** the app from App Manager.
6. The app will appear in the Falcon launcher (name: *SOC Dashboard*).

> 💡 When imported into a different tenant, Foundry **regenerates the internal IDs** (`app_id`, `page_id`, `function_id`, `saved_search_id`). The values present in `manifest.yml` inside the tar.gz are the original references and do not affect the new installation.

## 🧰 Tech stack

- **Frontend**: React 18 + Vite, [Shoelace Design System](https://shoelace.style/), Chart.js
- **SDK**: [Foundry-JS](https://developer.crowdstrike.com/foundry) (OAuth2 and Falcon API)
- **Cloud functions**: Python (FalconPy) — `charlotte-credits-fn`, `incidents-fn`, `devices-fn`, `workflow-executions-fn`
- **Saved searches**: 18 LQL queries in LogScale/NGSIEM

## 📝 Changelog highlights

Recent versions include:

- **v0.7.137** — New *3rd-Party Feed Silence* widget with 5 staleness tiers per vendor
- **v0.7.136** — *Data Ingestion* rewrite aggregating directly on `source_vendors`
- **v0.7.134** — Visual separation of CrowdStrike vs 3rd-party ingestion
- **v0.7.65** — Live Mean Time to Detect/Triage/Resolve from LogScale
- **v0.7.9** — Full migration to Alerts REST API (267k+ alerts on an empty-LogScale tenant)
- **v0.6.0** — First release with the 15 widgets and 4-row layout

## 🔐 Security

If you find a vulnerability in the application, please **do not open a public issue** — contact the author directly.

This application is a **community/personal** development and is not an official CrowdStrike product.

## 📄 License

Distributed under the [MIT](LICENSE) license.

CrowdStrike®, Falcon®, and related product names are registered trademarks of CrowdStrike, Inc. This project is independent and is not officially endorsed by CrowdStrike.

## 👤 Author

**Roberto Clavero**

---

<p align="center"><sub>Built with ❤️ for the Falcon Foundry community.</sub></p>
