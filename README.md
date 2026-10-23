# Crowdstrike — Falcon Foundry apps

Public repository containing packaged bundles (`.tar.gz` / `.zip`) of [Falcon Foundry](https://www.crowdstrike.com/platform/falcon-foundry/) applications ready to import into a CrowdStrike Falcon tenant.

> ℹ️ This repository ships **only the packaged bundles** (Foundry export). Development source code is not published here.

## Apps

| App | Description | Documentation |
| --- | --- | --- |
| **[NVA](NVA/)** — Network Vulnerability Assesment Dashboard | Unified monthly vulnerability-management dashboard (FEM + NVA + Spotlight + Discover + Alerts v2 + NG-SIEM) | [NVA/README.md](NVA/README.md) |
| **[unified-vulnerability-explorer](unified-vulnerability-explorer/)** — Unified Vulnerability Explorer | Toggle between ALL datalake vulnerabilities and findings discovered only by the Falcon Network Scanner, across the same integrated views | [unified-vulnerability-explorer/README.md](unified-vulnerability-explorer/README.md) |
| **[soc-dashboard](soc-dashboard/)** — Agentic SOC Oversight Dashboard | Real-time SOC videowall with 15 widgets (threat volume, MITRE ATT&CK, agent health, backlog, feed silence, Charlotte AI credits…) | [soc-dashboard/README.md](soc-dashboard/README.md) |

## Policies

Each app ships its own license and security policy:

- NVA: [LICENSE](NVA/LICENSE) · [SECURITY.md](NVA/SECURITY.md)
- unified-vulnerability-explorer: [LICENSE](unified-vulnerability-explorer/LICENSE) · [SECURITY.md](unified-vulnerability-explorer/SECURITY.md)
- soc-dashboard: [LICENSE](soc-dashboard/LICENSE) · [SECURITY.md](soc-dashboard/SECURITY.md)

## Author

**Roberto Clavero**
