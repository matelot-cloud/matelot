# Changelog

Release notes with image and chart digests are published at https://github.com/matelot-cloud/matelot/releases.
This file summarises each release line; the detailed per-change log is maintained internally.

## v0.1.0 — first self-hosted release

The first release a customer can install from the public chart: `oci://ghcr.io/matelot-cloud/charts/secops-cell`.

- **One cell per organization** from one Helm chart: API, worker, web app, managed runners, built-in container
  registry, Postgres, Redis, Keycloak; generated secrets that survive upgrades; upgrades roll only the application pods.
- **Inventory and SBOM**: repositories, builds, releases, images, deployments and Kubernetes/cloud discovery in one
  graph; an SBOM per release; continuous correlation with vulnerability intelligence.
- **Security pipeline** per service (checkout, SBOM, secrets, IaC, SAST, dependency scanning) with a policy gate;
  managed runners in the cell and self-hosted runner pools; signed, scoped CI tokens; CI examples for GitHub Actions,
  GitLab CI and Bitbucket Pipelines.
- **Vulnerabilities and risk**: findings correlated with images and deployments, risk scored by CVSS, exploitation,
  exposure and criticality; VEX; fix-first queue; SLAs; issues in GitHub, GitLab, Bitbucket and Jira with status sync.
- **Policies, gates and exceptions** inherited from organization to environment; deployment gates; policy templates;
  service coverage.
- **Keyless registry access** for ECR, ACR and Artifact Registry through workload identity federation; token-based
  access for Docker Hub, GHCR and any v2 registry.
- **CRA evidence**: signed evidence bundle per release, CRA readiness checks, audit trail on every change.
- **Notifications** to Slack, Microsoft Teams, e-mail and webhooks.
- **Identity and access**: Keycloak per cell (SSO/SAML/MFA), hierarchical RBAC, administration area, usage and
  rate limits.
- **CLI** `matelot` (npm `secops-platform-cli`) with every UI action; **MCP server** for AI assistants.
- **Operations**: scheduled backups to a volume and S3, restore and disaster-recovery procedures, usage per month.
