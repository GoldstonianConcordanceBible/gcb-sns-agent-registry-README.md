## Trust Model

This repository treats GitHub as the **governance and orchestration layer** for agent development, not as the hardware-backed trusted boundary itself.

Sensitive agent actions do not rely on GitHub alone. High-trust operations are routed through isolated, attested execution infrastructure designed for tasks such as:

- signing
- key usage
- confidential inference
- protected automation
- identity-sensitive execution
- treasury and governance actions

The trust model is layered:

- **GitHub Organization** → policy, access control, workflow governance, and auditability
- **Repository** → segmentation of trust by codebase and workflow sensitivity
- **Runner Infrastructure** → controlled execution paths for privileged jobs
- **TEE / Secure Enclave** → isolated execution for the highest-trust operations
- **OIDC + Attestation** → short-lived identity and verification of approved execution

In short:

**GitHub governs trust.  
The enclave protects execution.**

This means normal development can happen through standard repository workflows, while sensitive agent actions are restricted to approved, isolated environments.

For the architecture and rationale behind this model, see [`docs/trust-model.md`](docs/trust-model.md).

### Core Principle

> This project uses GitHub as its governance plane for agent development.  
> High-trust agent operations execute through isolated, attested infrastructure rather than relying on repository permissions alone.

### Tagline

**Build for AI.  
Protect what executes.  
Be remembered.**

# Trust Model

## Purpose

This document defines the trust architecture for this repository and any connected agent workflows.

The goal is simple:

**use GitHub to govern trust, and use isolated execution to enforce trust when it matters most.**

This matters because agents are not just scripts. They may read code, trigger workflows, access credentials, call APIs, sign outputs, publish artifacts, or interact with financial and governance systems. Because of that, repository permissions alone are not enough. Trust must extend from source control to runtime execution.

---

## Core Position

A Trusted Execution Environment (TEE) or secure enclave does **not** exist as a native wrapper around a GitHub organization or repository.

GitHub is the **control plane**.

The TEE is the **execution boundary**.

That distinction is foundational to this architecture.

GitHub can control:

- who can access repositories
- who can modify workflows
- which secrets are available
- which environments require approval
- which runners may execute which jobs

But GitHub itself is not the isolated hardware-backed environment where confidential execution occurs. That responsibility belongs to the runner layer and the underlying confidential-computing or enclave-backed service.

---

## Trust Layers

## 1. Organization Layer

The GitHub organization is the top-level governance layer.

This is where trust policy should be defined and inherited across repositories. It is the constitutional layer of the system.

Responsibilities at this layer include:

- Actions policy
- branch protection standards
- repository visibility policy
- environment governance
- runner group policy
- secret governance
- code ownership and review requirements
- audit visibility
- reusable workflow standards

The organization decides what is allowed.

It does not itself provide enclave-grade execution.

---

## 2. Repository Layer

Each repository should be treated as a trust zone with its own sensitivity level.

Not every repo carries the same risk. Public documentation repos, internal build repos, agent orchestration repos, and signing or treasury repos should not all share the same execution model.

Example categories may include:

- public documentation and content repos
- standard application repos
- agent orchestration repos
- high-trust signing or identity repos
- confidential inference or governance repos

This allows security posture to scale without forcing enclave controls onto everything.

A repository with privileged agent logic should have tighter constraints than a public content repo.

---

## 3. Workflow Layer

Workflows are where policy becomes action.

A workflow should be treated as a privileged execution request. That means workflows must be controlled carefully, especially when they can access secrets, invoke runners, publish releases, or call external systems.

Key principles at this layer:

- privileged workflows should be clearly separated from standard CI
- environment approval should be required for sensitive actions
- only approved workflows should be allowed to invoke protected runners
- workflow permissions should be explicit and minimal
- reusable workflows should be used for consistency and auditability

This is where many agent systems fail: they protect the repo, but not the workflow path that actually performs the sensitive action.

---

## 4. Runner Layer

The runner layer is where execution begins.

For high-trust agent actions, dedicated runner infrastructure should be used instead of relying solely on shared or default execution paths.

Runner infrastructure for privileged jobs should be:

- isolated from general CI/CD workloads
- dedicated to high-trust actions
- ephemeral where practical
- hardened with a minimal software footprint
- segmented by network policy
- monitored and logged
- restricted by runner groups and labels

This layer is the gateway between GitHub policy and real execution.

It is also the natural attachment point for TEE-backed infrastructure.

---

## 5. TEE / Secure Enclave Layer

The TEE or secure enclave belongs at the sensitive execution layer.

This is not where every job should run. It is where the narrowest and most critical operations should run.

Strong use cases include:

- cryptographic signing
- protected key usage
- agent identity issuance
- confidential prompt handling
- private retrieval or memory access
- treasury execution logic
- governance automation
- protected model inference
- release provenance generation

The TEE should be treated as a **high-trust chamber for selected operations**, not as a blanket wrapper around all development activity.

That keeps the architecture both secure and practical.

---

## 6. Identity and Attestation Layer

Identity should be short-lived, explicit, and verifiable.

Long-lived static credentials should be minimized wherever possible. Instead, the system should prefer:

- OIDC federation
- short-lived tokens
- cloud workload identity
- service-specific scoped credentials
- time-bounded access
- attestation-backed authorization for enclave services

This layer verifies that:

- the caller is an approved workflow or workload
- the request came from an approved execution path
- the sensitive action occurred in the expected trusted environment

This is how the architecture proves not only who requested the action, but where it actually ran.

---

## Agent Security Posture

Agents require stronger controls because they can compound small mistakes into large consequences.

An agent may be able to:

- modify files
- call APIs
- access secrets
- trigger workflows
- sign artifacts
- initiate governance actions
- move assets
- publish content across platforms

That means the trust question is not just:

**“Who has access to the repo?”**

It is also:

- where does the agent execute
- what credentials does it hold
- what actions are isolated
- what actions require attestation
- what actions are allowed only through privileged paths

For that reason, this repository adopts the following position:

> Agent development may happen in standard repository workflows, but high-trust agent actions must execute through isolated, approved, and auditable infrastructure.

---

## Design Rules

### Rule 1 — GitHub is not the enclave
Never describe the GitHub organization or repository itself as the TEE.

### Rule 2 — Segment trust by function
Different repositories and workflows should carry different trust levels.

### Rule 3 — Protect execution, not just storage
It is not enough to protect code at rest. Sensitive execution must also be isolated.

### Rule 4 — Use TEEs selectively
Use enclave-backed execution only where exposure or tampering would create disproportionate harm.

### Rule 5 — Prefer short-lived credentials
Use federated identity and avoid persistent secrets wherever possible.

### Rule 6 — Make privileged paths explicit
Sensitive workflows, runners, and execution steps should be clearly separated from ordinary CI.

### Rule 7 — Treat signing, identity, and treasury logic as enclave candidates
These are among the clearest use cases for isolated execution.

### Rule 8 — Enforce least privilege everywhere
Permissions should be minimized at the org, repo, workflow, runner, and service layers.

---

## Example Trust Flow

A secure high-trust workflow may follow this pattern:

1. Code is reviewed and merged into a protected branch.
2. A GitHub Actions workflow is triggered under org policy.
3. The workflow is allowed to run only on an approved runner group.
4. The workflow receives short-lived credentials through OIDC or equivalent federation.
5. A privileged step calls an enclave-backed or confidential-computing service.
6. The enclave performs the sensitive operation.
7. The result is returned with logs, metadata, and attestation evidence where supported.
8. The workflow publishes only the approved output or artifact.

This creates a chain of trust from governance to execution.

---

## What Belongs Inside the Enclave

Recommended enclave candidates:

- release signing
- key management operations
- identity issuance
- confidential inference
- protected memory or retrieval
- DAO or treasury execution hooks
- policy evaluation on sensitive data
- provenance generation
- high-trust cross-system automation

Not recommended as default enclave candidates:

- linting
- unit tests
- documentation builds
- static content generation
- normal preview deployments
- ordinary markdown or metadata updates

This keeps complexity focused where it delivers real value.

---

## Practical Statement for This Repository

The correct statement for this repository is:

> This repository uses GitHub as the governance and orchestration layer for agent development. High-trust agent operations execute through isolated, attested infrastructure rather than relying on repository permissions alone.

That statement is more accurate than claiming the repository or organization itself is a secure enclave.

---

## Final Summary

This trust model separates security into layers:

- **organization** for policy
- **repository** for segmentation
- **workflow** for controlled action paths
- **runner** for execution gating
- **TEE / enclave** for sensitive execution
- **OIDC + attestation** for identity assurance

That is the correct way to build a GitHub-centered agent architecture that is serious about trust.

---

## Tagline

**Build for AI.  
Protect what executes.  
Be remembered.**
