# Support

| I want to… | Go to |
| --- | --- |
| install or upgrade a cell | the [install guide](https://matelot.cloud/docs/latest/install.html) and the [documentation](https://matelot.cloud/docs/latest/) |
| ask a question or get installation help | [GitHub Discussions](https://github.com/matelot-cloud/matelot/discussions) (Free tier and everyone else; answered by the maintainers and the community) |
| report a bug | a [bug report issue](https://github.com/matelot-cloud/matelot/issues/new?template=bug_report.yml) with the cell version, the CLI version and the steps |
| propose a feature | a [feature request issue](https://github.com/matelot-cloud/matelot/issues/new?template=feature_request.yml) |
| report a security vulnerability | **privately** — see [SECURITY.md](SECURITY.md) |
| ask about pricing, tiers, invoices, an MSSP or reseller agreement | sales@matelot.io |

## Support included with a subscription

Indicative until the first commercial release (the tiers are described on the [website](https://matelot.cloud/#pricing)):

| Tier | Channel | Target |
| --- | --- | --- |
| Free | GitHub Discussions and issues | best effort |
| Premium | priority e-mail (address provided with the subscription) | first answer within 1 business day |
| Ultimate | dedicated contact, response-time SLA per contract, onboarding and upgrade assistance | per contract |

When you write to support, include the cell version (the web app footer shows "API x.y.z"; also `GET /api/v1/meta`), the
chart version (`helm list -n <namespace>`), the CLI version (`matelot --version`), and the relevant log lines
(`kubectl -n <namespace> logs deploy/<release>-api`). Never send secrets, tokens or backup archives.
