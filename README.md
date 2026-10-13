<p align="center"><img src="logo.png" width="96" alt="Matelot"></p>

<h1 align="center">Matelot</h1>

<p align="center"><strong>Product security, DevSecOps and CRA compliance — self-hosted in your Kubernetes cluster.</strong></p>

<p align="center">
  <a href="https://matelot.cloud/">Website</a> ·
  <a href="https://matelot.cloud/docs/latest/">Documentation</a> ·
  <a href="https://matelot.cloud/docs/latest/install.html">Install guide</a> ·
  <a href="https://github.com/matelot-cloud/helm-charts">Helm chart</a> ·
  <a href="https://github.com/matelot-cloud/matelot/releases">Releases</a> ·
  <a href="SECURITY.md">Security policy</a>
</p>

---

Matelot keeps a live picture of every product, service, release and deployment you ship: **what is in it** (SBOM per
release), **which vulnerabilities reach production** (findings correlated with images and deployments, risk-scored by
exposure), **which policies apply** (inherited policies evaluated as pipeline gates and deployment gates, explicit
time-limited exceptions), and **the evidence the Cyber Resilience Act expects** (a signed evidence bundle per release,
CRA readiness checks, a full audit trail).

It runs as **one cell per organization** in your own cluster, installed from one Helm chart: API, worker, web app,
managed runners, a container registry, Postgres, Redis and Keycloak. Nothing leaves the cell except the integrations
you connect.

## What is in the box

- **Security pipeline** — checkout, SBOM, secrets, IaC, SAST and dependency scanning per service, with a policy gate at the end; run from the UI, the CLI (`matelot`) or your CI with signed, scoped tokens.
- **Vulnerability and risk** — findings correlated against SBOMs and deployments; the same CVE is Medium in development and Critical when internet-facing in production.
- **Keyless registries** — ECR, ACR and Artifact Registry through workload identity federation, no stored registry secrets; Docker Hub, GHCR and any v2 registry with tokens.
- **Managed and self-hosted runners** — runners ship inside the cell; add pools for private networks and other clusters.
- **Remediation and SLAs** — fix-first queue, SLA clocks per severity, issues in GitHub, GitLab, Bitbucket or Jira kept in sync.
- **Hierarchical RBAC and audit** — organization → workspace → team → project → service → environment, SSO through the cell's own Keycloak.
- **CRA evidence** — signed evidence bundles per release, readiness checks mapped to requirements.
- **Operations** — scheduled backups to a volume and your S3 bucket, tested restore, upgrades that roll only the application pods, an MCP server for AI assistants.

## Screenshots

<!-- TODO: add screenshots of the Overview, a release's evidence bundle and the Security graph -->
_Screenshots will be added with the first public release._

## Install

**Docker Compose — five minutes on one host** (evaluation and small teams):

```bash
git clone --depth 1 https://github.com/matelot-cloud/matelot && cd matelot/docker
cp .env.example .env            # MATELOT_DOMAIN (keep localhost to try it), MATELOT_ADMIN_EMAIL
docker compose up -d
docker compose logs -f welcome  # prints the URL and the administrator login
```

Every secret is generated on first start; with a real domain Caddy obtains HTTPS certificates automatically.
`docker/` is written by the release pipeline (compose file, `.env.example` pinned to the release, backup/restore
scripts, smoke test).

**Kubernetes (Helm) — production:**

```bash
helm install acme oci://ghcr.io/matelot-cloud/charts/secops-cell --version <release> \
  --namespace tenant-acme --create-namespace -f values.yaml
```

The [install guide](https://matelot.cloud/docs/latest/install.html) compares the two, and covers
requirements, settings, the first administrator, backups, upgrades and removal. Images
(`ghcr.io/matelot-cloud/{api,web,worker,runner}`) and the chart are published on GitHub Packages, signed with cosign
(keyless, GitHub OIDC) and carry SBOM attestations; every [release](https://github.com/matelot-cloud/matelot/releases)
lists the digests.

## This repository

Matelot is closed source; this repository holds no application code. It is the public home for:

- **[Issues](https://github.com/matelot-cloud/matelot/issues)** — bug reports and feature requests (templates provided). Security vulnerabilities go through the [security policy](SECURITY.md), never through a public issue.
- **[Discussions](https://github.com/matelot-cloud/matelot/discussions)** — questions, installation help, ideas.
- **[Releases](https://github.com/matelot-cloud/matelot/releases)** — release notes with image and chart digests and SBOMs.
- **[docker/](docker/)** — the Docker Compose stack (kept in sync by the release pipeline).
- [CHANGELOG.md](CHANGELOG.md), [SUPPORT.md](SUPPORT.md), [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md), [LICENSE](LICENSE) (customer EULA).

Pull requests are not accepted here (there is nothing to change); see the [pull request template](.github/PULL_REQUEST_TEMPLATE.md).
