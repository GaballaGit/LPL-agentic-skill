# Proposed engineering approach

Treat these as prototype defaults, not LPL internal standards. Follow the repository and event constraints. Verify current framework/provider documentation before selecting compatible supported versions, and pin them. Do not require the newest major version.

## Angular and TypeScript

- Organize by workflow/feature. Use strict TypeScript and typed API contracts. Follow repository conventions; use supported standalone components when suitable for new work.
- Implement loading, empty, error, success, and retry states. Provide labels, keyboard access, useful focus behavior, and readable hierarchy.
- Use framework escaping/sanitization. Do not bypass sanitization for documents or model output. Keep credentials out of browser code.
- Enforce authorization server-side; route guards and hidden controls only shape the interface.

Official references: [style guide](https://angular.dev/style-guide), [security](https://angular.dev/best-practices/security), [accessibility](https://angular.dev/best-practices/a11y).

## ASP.NET Core and persistence

- Prefer one deployable modular application, explicit DTOs, dependency injection, and clear feature boundaries. Avoid microservices created solely for presentation.
- Define OpenAPI and consistent errors with correlation IDs. Validate both shapes and business rules. Keep stack traces server-side.
- Enforce identity, policy, and resource ownership as needed. Derive tenant scope from trusted identity; check it on reads and mutations. Arbitrary caller-supplied tenant IDs do not prove access.
- Use existing OIDC when available. For a standalone demo, isolate seeded identities or a development-only auth handler, document it, and disable it outside development. Do not describe it as enterprise SSO.
- Use transactions for coupled state/audit updates, concurrency tokens for conflicting edits, and idempotency for retryable commands where relevant.
- Choose storage for actual constraints. SQLite suits a local single-instance demo with stated limitations. Kubernetes persistence requires suitable external storage or a documented volume strategy, not a disposable container filesystem.
- Separate audit events from diagnostic logs. Record actor, resource, action, timestamp, outcome, correlation ID, and relevant proposal/model version. Redact sensitive payloads. An audit table is not automatically tamper-proof.

Official reference: [ASP.NET Core resource-based authorization](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/resource-based).

## Containers and Kubernetes

- Use repeatable builds, pinned dependencies, a non-root runtime, external configuration, and a small local start path.
- For Kubernetes artifacts, supply Deployment/Service, requests/limits, readiness/liveness probes, and startup probes when initialization warrants them. Keep probe purposes separate; an unavailable dependency should not restart an otherwise healthy process.
- Apply appropriate least-privilege identity and pod security settings. Keep secrets out of manifests and explain environment-specific injection.
- Handle graceful termination, persistence, and rollback. Include network/ingress controls when supported and required.
- Distinguish schema checks, dry runs, local cluster runs, and cloud deployment. Manifests alone do not prove availability or recovery.

Official references: [probes](https://kubernetes.io/docs/concepts/workloads/pods/probes/), [security checklist](https://kubernetes.io/docs/concepts/security/security-checklist/).

## AWS and Terraform

- Justify each service. Keep a cloud target optional unless required. A future EKS design must remain labeled future; do not fabricate operational evidence.
- Define only infrastructure in scope. Reuse provided cluster/VPC resources when practical.
- Specify region/environment inputs, outputs, tags, and narrow IAM. Prefer short-lived credentials. Keep sensitive storage private with appropriate encryption.
- Protect Terraform state. The sensitive flag redacts some displays; it does not ensure secrets are absent or encrypted in state. Exclude state, plans, credentials, and secret variable files from source control. For shared/cloud work, use an encrypted access-controlled backend and appropriate locking.
- Run formatting/validation. Plan against an authorized environment only; report missing credentials honestly. Explain costs and teardown for resources provisioned. Budget alerts are not hard spending caps.

Official references: [AWS least privilege](https://docs.aws.amazon.com/wellarchitected/latest/framework/sec_permissions_least_privileges.html), [Terraform sensitive data](https://developer.hashicorp.com/terraform/language/manage-sensitive-data).

## CI and evidence

Reuse existing CI. For new work, include relevant frontend build/type checks, backend build/tests, and conditional image/IaC checks. Do not prescribe a CI vendor as an LPL standard. Keep credentials out of definitions and logs.

Test state rules, authorization, mutations, retries, and the principal integration path. For AI, cover grounding, malformed output, prompt injection, changed approvals, and provider failure with a small evaluation set and actual results.

Describe a realistic production path: identity integration, threat review, domain validation, migrations, retention, telemetry, scaling tests, backup/recovery, and operational ownership. Label unfinished work. Do not claim FINRA/SEC compliance from this checklist; regulatory assertions need applicable authoritative evidence and qualified review.
