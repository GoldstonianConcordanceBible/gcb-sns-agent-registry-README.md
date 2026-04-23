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