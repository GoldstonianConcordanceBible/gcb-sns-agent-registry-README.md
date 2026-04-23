# SECURITY_ARCHITECTURE.md

## Security Architecture for Agent Repositories

This repository is designed with the understanding that GitHub is a **governance and orchestration layer**, not a hardware-backed trusted execution boundary.

A Trusted Execution Environment (TEE) or secure enclave does **not** exist as a native wrapper around a GitHub organization or repository. Instead, this architecture separates trust into layers:

- **GitHub Organization / Repository Layer** → governance, access control, workflow policy, branch protection, secret management, and auditability
- **Runner / Compute Layer** → controlled execution environment for workflows and agents
- **TEE / Secure Enclave Layer** → isolated execution for the highest-trust operations
- **Identity and Attestation Layer** → short-lived credentials, workload identity, and verification of trusted execution

This distinction matters because agent systems increasingly combine code, workflows, model calls, credentials, and signing operations. The safest design is not to pretend GitHub itself is the enclave, but to make GitHub the **control plane** that routes sensitive operations into a verified, isolated execution environment.

---

## Core Principle

**GitHub governs trust.  
The TEE enforces trust during execution.**

GitHub protects who can change code, trigger workflows, and access secrets.  
The TEE protects what happens when sensitive code runs.

For agent infrastructure, that means:

- policy at the org level
- isolation at the execution level
- attestation at the identity level
- least privilege everywhere

---

## Architectural Model

### 1. Organization-Level Governance

At the top level, the GitHub organization should serve as the trust coordination layer for all agent repositories.

This includes:

- organization-wide Actions policies
- repository creation controls
- branch protection rules
- required reviews
- CODEOWNERS enforcement
- environment protection rules
- secret scanning and push protection
- runner groups and runner access policy
- reusable workflows for security-critical actions

The organization is where security standards are declared and inherited. This is the level that says:

- which workflows are allowed
- which runners may execute sensitive jobs
- which environments require approval
- which repositories are allowed to interact with privileged infrastructure

In other words, the org level is where the **constitution of trust** lives.

---

### 2. Repository-Level Segmentation

Not every repository or workflow has the same trust requirement.

Repositories should be categorized, for example:

- **Public documentation repos**
- **Standard code repos**
- **Agent orchestration repos**
- **High-trust signing / identity / treasury repos**
- **Confidential inference or secret-handling repos**

Sensitive repositories should have stricter controls such as:

- restricted admin access
- mandatory pull request review
- required status checks
- signed commits or verified provenance where possible
- workflow approval gates
- limited runner access
- restricted environment secrets

This prevents the whole organization from inheriting the burden of enclave-grade isolation where it is not needed.

---

### 3. Runner-Level Isolation

GitHub-hosted runners are convenient, but high-trust agent operations should be routed to **dedicated self-hosted runners** or other tightly controlled execution infrastructure.

This is the point where GitHub policy hands off to the compute boundary.

Sensitive jobs should run only on runners that are:

- dedicated to high-trust workloads
- isolated from general CI/CD traffic
- segmented by network policy
- ephemeral where possible
- monitored and auditable
- hardened with minimal software footprint

This is the practical location where confidential computing can begin to matter.

---

### 4. TEE / Secure Enclave Execution

The real Trusted Execution Environment belongs **underneath the runner or attached service boundary**, not at the GitHub repo object itself.

A TEE or secure enclave should be used for the narrow set of operations where execution confidentiality and integrity matter most.

Examples include:

- agent identity generation
- cryptographic signing
- key derivation or key usage
- protected model inference
- secret processing
- confidential prompt or memory handling
- treasury or DAO control logic
- policy evaluation on sensitive data

The TEE should be treated as a **selective high-trust execution chamber**, not as the default runtime for everything.

This is important because most development tasks do not require enclave overhead. Overusing TEEs creates unnecessary friction, cost, and operational complexity. The correct approach is targeted isolation for the operations that would be catastrophic if exposed or tampered with.

---

### 5. Identity, OIDC, and Attestation

The identity layer should assume that long-lived secrets are a liability.

Where possible, workflows should use:

- OIDC-based federation
- short-lived credentials
- cloud workload identity
- attested service access
- least-privilege tokens
- time-bounded authorization

This allows GitHub workflows to request temporary credentials at runtime instead of storing persistent secrets in repositories or organization settings.

For enclave-backed operations, attestation should be used to verify that:

- the workload is running in the expected trusted environment
- the code or measurement matches the approved policy
- the request originates from an authorized workflow path

This closes the trust loop between source control, workflow identity, and runtime execution.

---

## Recommended Security Pattern for Agent Systems

For agent repositories, the best pattern is:

### GitHub Org = Governance Plane
Controls policy, access, approvals, inheritance, and orchestration.

### Sensitive Repos = Segmented Trust Zones
Only certain repositories may invoke privileged workflows.

### Dedicated Runners = Controlled Execution Gateways
Only approved jobs can reach privileged compute.

### TEE / Secure Enclave = High-Trust Execution Boundary
Handles secrets, keys, signing, confidential logic, and protected inference.

### OIDC + Attestation = Identity Assurance
Confirms that execution is both authorized and genuine.

This layered design gives the organization a realistic and defensible security posture without making false claims that “the GitHub org itself is a TEE.”

---

## What This Means for Agents

Agents amplify both capability and risk.

An agent may:

- read code
- generate code
- trigger workflows
- call APIs
- access secrets
- sign outputs
- move funds
- publish artifacts
- act across multiple systems

Because of that, agent security should not be based only on repository permissions. It must also account for **where the agent runs**, **what identity it holds**, and **whether its most sensitive actions occur inside an isolated trust boundary**.

For this reason, this repository adopts the following stance:

> Agent development may occur in normal repository workflows, but high-trust agent actions must execute through isolated, attested infrastructure.

That is the difference between general automation and secure agent architecture.

---

## Design Rules

### Rule 1 — Do not describe GitHub itself as the enclave
GitHub is the coordination layer, not the trusted hardware boundary.

### Rule 2 — Use TEEs only for high-value operations
Reserve enclave-backed execution for the smallest set of operations that justify it.

### Rule 3 — Separate development trust from execution trust
A developer may edit code in GitHub, but sensitive execution should happen only in approved isolated infrastructure.

### Rule 4 — Prefer short-lived credentials
Replace persistent secrets with federated identity whenever possible.

### Rule 5 — Enforce least privilege at every layer
Repositories, workflows, runners, services, and agents should receive only the permissions they strictly need.

### Rule 6 — Make privileged paths explicit
Do not hide sensitive execution inside general-purpose workflows. Mark and isolate the trust boundary clearly.

### Rule 7 — Treat agent signing, treasury, and identity as enclave candidates
These are among the strongest use cases for secure enclaves in agent ecosystems.

---

## Example Trust Flow

A secure agent workflow may look like this:

1. A pull request is reviewed and merged into the protected repository.
2. A GitHub Actions workflow is triggered under org policy.
3. The workflow is allowed to run only on a restricted runner group.
4. The runner authenticates using OIDC and obtains short-lived credentials.
5. For a high-trust step, the runner invokes a confidential-computing service or enclave-backed execution path.
6. The enclave performs signing, key use, or confidential agent logic.
7. The result is returned with logs, metadata, and attestation evidence where applicable.
8. The workflow publishes only the approved artifact or response.

This creates a chain of trust from repository governance to isolated execution.

---

## What Should Be Protected by the Enclave

Recommended enclave candidates:

- signing keys
- treasury actions
- DAO governance execution hooks
- agent identity issuance
- protected API credentials
- confidential reasoning or prompt material
- private memory or retrieval contexts
- release signing and provenance generation
- sensitive cross-system automation

Not recommended as default enclave candidates:

- linting
- documentation builds
- static site generation
- standard tests
- normal preview deployments
- ordinary content commits

This keeps the enclave reserved for what actually matters.

---

## Organizational Recommendation

At the organization level, the goal should be:

- establish uniform trust policy across all agent repos
- create a small number of privileged runner paths
- centralize sensitive execution into enclave-backed services
- document which workflows may access those services
- keep public and ordinary development outside the enclave unless necessary

So the correct top-level statement is not:

**“Our GitHub organization is a secure enclave.”**

The correct statement is:

**“Our GitHub organization governs a layered trust architecture in which high-trust agent operations execute within isolated, attested environments.”**

That phrasing is accurate, defensible, and scalable.

---

## Suggested Language for README

You can place this in the main README:

> This project uses GitHub as its governance and orchestration layer for agent development. Sensitive agent operations do not rely on GitHub alone; they are routed through isolated, attested execution infrastructure designed for high-trust tasks such as signing, key usage, confidential inference, and protected automation.

---

## Suggested Language for Org-Level Policy

> The GitHub organization defines policy.  
> Dedicated runners enforce controlled execution.  
> Secure enclaves protect the highest-trust agent operations.  
> Identity federation and attestation verify that sensitive actions occur only in approved environments.

---

## Final Position

Yes, it makes sense to think about **TEE-backed protection at the top of the agent architecture**, but not as a literal GitHub-org wrapper.

The right model is:

- **org level** for governance
- **repo level** for segmentation
- **runner level** for execution control
- **TEE level** for high-trust operations
- **OIDC + attestation** for identity assurance

That is the secure, accurate, and production-ready way to frame agent infrastructure on GitHub.

---

## Tagline

**Build for AI.  
Protect what executes.  
Be remembered.**