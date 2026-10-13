# Security policy

We take vulnerability reports seriously and appreciate the time it takes to prepare one.

## Reporting a vulnerability

**Please do not open a public issue for a security vulnerability.**

Report it through one of these private channels:

1. **GitHub private vulnerability reporting** — [Report a vulnerability](https://github.com/matelot-cloud/matelot/security/advisories/new)
   on this repository (preferred: it keeps the whole exchange in one place and lets us credit you in the advisory).
2. **E-mail** — security@matelot.io. If you want to encrypt, ask for our PGP key in a first plain message.

Please include the affected component and version (cell version from the web app's footer ("API x.y.z") or `GET /api/v1/meta`,
CLI version, chart version), steps to reproduce, and the impact as you understand it.

## What to expect

- Acknowledgement within **2 business days**.
- An assessment and a plan within **7 days**; we keep you informed while we work on a fix.
- A fix in a release, with a GitHub security advisory and a CVE where appropriate. Advisories name the fixed
  version; the [release notes](https://github.com/matelot-cloud/matelot/releases) carry the image digests.
- Credit in the advisory, if you want it.

## Scope

Matelot's images (`ghcr.io/matelot-cloud/*`), the Helm chart, the `matelot` CLI, the runner agent and the public
website. Vulnerabilities in third-party components are in scope when Matelot's use of them is exploitable; we track
our own dependencies with the SBOMs we publish for every release.

## Supported versions

Security fixes go into the latest release line. Keep your cell on the latest release (`helm upgrade`, see the
[install guide](https://matelot.cloud/docs/latest/install.html#a5-upgrades-and-rollback)).

## Verifying what you run

Images and the chart are signed with cosign (keyless, GitHub OIDC) and the images carry SPDX SBOM attestations;
the verification commands are in every release's notes.
