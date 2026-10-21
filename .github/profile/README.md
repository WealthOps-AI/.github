# WealthOps

WealthOps is a fictional wealth-management operations platform and containerized learning project. This organization groups independently versioned repositories for the application, local platform, contracts, and specifications.

## Get started

Use the platform's [Linux/macOS setup guide](https://github.com/WealthOps-AI/wealthops-ai-platform/blob/master/local/GETTING-STARTED-LINUX-MACOS.md) to run the Docker Compose stack. A [Windows setup guide](https://github.com/WealthOps-AI/wealthops-ai-platform/blob/master/local/GETTING-STARTED-WINDOWS.md) is also available. Docker or Docker Desktop with Docker Compose v2 must be running; host-installed .NET, Node.js, PostgreSQL, Kafka, or Airflow are not required.

## Repositories

| Repository | Contents |
|---|---|
| [`wealthops-ai-web`](https://github.com/WealthOps-AI/wealthops-ai-web) | React/TypeScript workstation |
| [`wealthops-ai-be`](https://github.com/WealthOps-AI/wealthops-ai-be) | .NET API, EF Core migrator/seeder, migrations, and tests |
| [`wealthops-ai-platform`](https://github.com/WealthOps-AI/wealthops-ai-platform) | Docker Compose, local Nginx/TLS configuration, Kong production gateway configuration, and deployment infrastructure |
| [`wealthops-ai-pipelines`](https://github.com/WealthOps-AI/wealthops-ai-pipelines) | Airflow repository skeleton and optional local infrastructure |
| [`wealthops-ai-legacy-adapter`](https://github.com/WealthOps-AI/wealthops-ai-legacy-adapter) | Deferred Windows .NET Framework adapter |
| [`wealthops-ai-contracts`](https://github.com/WealthOps-AI/wealthops-ai-contracts) | Shared HTTP and event contract skeleton |
| [`wealthops-ai-specifications`](https://github.com/WealthOps-AI/wealthops-ai-specifications) | Business, architecture, security, testing, and development specifications |

Each repository README describes its own scope. The platform's local guides cover setup by operating system.

## Implemented foundation

- .NET 10 ASP.NET Core API with EF Core/Npgsql, PostgreSQL migrations, a separate migrator, and Development-only synthetic seed data.
- JWT authentication, role-based authorization, request correlation, security headers, problem-details errors, CORS, rate limiting, health checks, and Development OpenAPI.
- React, TypeScript, and Vite workstation with dashboard/accounts views and light/dark/system themes.
- Docker Compose topology for PostgreSQL, migrator/seeder, API, Nginx HTTPS edge, and web. Optional profiles add standalone Kafka and Airflow containers.
- Initial advisor, household, client, account, dashboard, and audit API surface, with account lifecycle authorization and audit events.

## Current limits

Kafka and Airflow are infrastructure skeletons, not integrated pipelines or event processing. Production AWS EKS/Kubernetes manifests, Terraform, CI/CD, and AWS service integrations are not implemented. Production OIDC is configured as a backend validation boundary, but the web app currently offers only Development sign-in. Portfolio/trading, transfers, billing, ledger posting, reconciliation, workers, and legacy-adapter behavior remain future milestones.

See the [repository topology](https://github.com/WealthOps-AI/wealthops-ai-specifications/blob/master/20-repository-topology.md) and [local development guide](https://github.com/WealthOps-AI/wealthops-ai-specifications/blob/master/21-local-development-guide.md) for ownership and deployment details.

## Recommended next milestones

1. Wire production OIDC sign-in in the web app and add API authorization/integration tests.
2. Add securities, positions, simulated trades, and portfolio views with validated domain rules.
3. Add transfers, fee calculations, and a balanced double-entry journal with idempotency and approval controls.
4. Define versioned event contracts; implement the transactional outbox, Kafka consumers, retries, and replay tests.
5. Add custodian/reconciliation workflows and containerized Airflow ingestion and analytics DAGs.
6. Build the production EKS path: Terraform, Helm/Kubernetes, AWS identity/secrets, CI/CD, telemetry, and operational runbooks.

Keep each milestone independently testable; do not treat the Kafka/Airflow containers or target AWS architecture as completed integrations.

## Contributing and local development

The runnable application and Docker Compose configuration are maintained in `wealthops-ai-platform`. Follow the platform's [Linux/macOS setup guide](https://github.com/WealthOps-AI/wealthops-ai-platform/blob/master/local/GETTING-STARTED-LINUX-MACOS.md), or use the [Windows setup guide](https://github.com/WealthOps-AI/wealthops-ai-platform/blob/master/local/GETTING-STARTED-WINDOWS.md) if needed. These guides cover prerequisites, starting the stack, smoke testing, sample data, and stopping services without deleting local data.

Keep local `.env` values and credentials out of commits. Use only synthetic Development data and never reuse local credentials in deployed environments.
