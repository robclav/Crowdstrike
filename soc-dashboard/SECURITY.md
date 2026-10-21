# Política de seguridad

## Reporte de vulnerabilidades

Si descubres una vulnerabilidad en **Agentic SOC Oversight Dashboard**, por favor **no la reportes en un issue público**.

Usa [GitHub Security Advisories](https://github.com/robclav/Crowdstrike/security/advisories/new) para abrir un reporte privado al mantenedor.

Intentaré responder en un plazo de **72 horas**.

## Alcance

Este repositorio distribuye únicamente el bundle empaquetado (`.tar.gz`) de la aplicación Foundry. Los reportes relevantes incluyen:

- Fugas de datos en el bundle (credenciales, tokens, IPs internas, hostnames reales).
- Vulnerabilidades de lógica en la aplicación tras instalarla en un tenant.
- Problemas con los scopes OAuth2 solicitados en `manifest.yml`.

Las vulnerabilidades en la plataforma **CrowdStrike Falcon** o **Foundry** deben reportarse directamente a [CrowdStrike](https://www.crowdstrike.com/vulnerability-disclosure-policy/).
