# Security Policy

## Reporting a vulnerability

If you find a vulnerability in the **Agentic SOC Oversight Dashboard**, please **do not open a public issue**.

Use [GitHub Security Advisories](https://github.com/robclav/Crowdstrike/security/advisories/new) to open a private report to the maintainer.

I aim to respond within **72 hours**.

## Scope

This repository ships only the packaged bundle (`.tar.gz`) of the Foundry application. Relevant reports include:

- Data leaks inside the bundle (credentials, tokens, internal IPs, real hostnames).
- Logic vulnerabilities in the app after installing it into a tenant.
- Issues with the OAuth2 scopes requested in `manifest.yml`.

Vulnerabilities in the **CrowdStrike Falcon** platform or **Foundry** itself should be reported directly to [CrowdStrike](https://www.crowdstrike.com/vulnerability-disclosure-policy/).
