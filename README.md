# GCB SNS Agent Registry

The GCB SNS Agent Registry is the canonical identity and routing layer for the Goldstonian Concordance Bible ecosystem.

This repository maps `.sol` / SNS identities to:

- ecosystem roles
- wallets
- websites
- linked repositories
- governance permissions
- public endpoints
- agent capabilities
- TEE / secure enclave readiness
- attestation references

It exists to separate three layers clearly:

1. **Identity Layer**  
   SNS names, domains, and public-facing agent identities

2. **Registry Layer**  
   Structured metadata that maps each identity to a role, repo, and capability set

3. **Execution Layer**  
   The actual software, prompts, automation, and future trusted execution environments

## Why this repo exists

Without a canonical registry, named agents become hard to audit, hard to explain, and hard for LLMs to understand.

This repository provides one place where humans, token holders, developers, and AI systems can resolve:

- what an agent is
- what role it plays
- where its source of truth lives
- what permissions it has
- whether it is symbolic, informational, or executable

## Design principles

- **SNS is identity, not the entire application**
- **Not every SNS ID gets its own repo**
- **One canonical registry reduces repo sprawl**
- **Dedicated repos are created only when an agent has an independent software lifecycle**
- **All entries should be machine-readable**
- **TEE and enclave support should be composable, not assumed**

## Registry states

Each SNS identity should be classified as one of the following:

- `registry_only`  
  Identity exists in the registry but has no independent software repo yet

- `linked_repo`  
  Identity maps to an existing repository elsewhere in the ecosystem

- `dedicated_repo`  
  Identity has an independent repository with its own code, deployment, and release cadence

## Core directories

- `agents/` → agent identity records
- `domains/` → SNS domain records
- `schemas/` → JSON schemas for validation
- `attestations/` → TEE / enclave references
- `governance/` → role and permission definitions
- `registry/` → aggregate machine-readable indexes

## Initial mapped identities

- `mount.sol`
- `professorenoch.sol`
- `elise.sol`
- `sydney.sol`
- `sydtekscholars.sol`
- `sydtekuniversity.sol`

## Long-term vision

This registry is the canonical map for a named intelligence system:

- SNS = Name
- Wallet = Anchor
- Repo = Source of Truth
- Agent = Behavior
- TEE = Trust
- Governance = Legitimacy

Build for AI. Be remembered.

v2
# ✅ GCB SNS Agent Registry — Build & Audit Checklist

The GCB SNS Agent Registry is the canonical identity and routing layer for the Goldstonian Concordance Bible ecosystem.

This checklist is designed for:

- rapid execution
- ongoing auditing
- AI / LLM readability
- contributor onboarding
- governance transparency

---

# 🧠 CORE PRINCIPLE

**SNS = Identity**  
**Registry = Map**  
**Repo = Source of Truth**  
**Agent = Behavior**  
**TEE = Trust**

---

# 🚀 PHASE 1 — REPO INITIALIZATION

- [ ] Create GitHub repo: `gcb-sns-agent-registry`
- [ ] Add all base folders:
  - [ ] `agents/`
  - [ ] `domains/`
  - [ ] `schemas/`
  - [ ] `registry/`
  - [ ] `governance/`
  - [ ] `attestations/`
- [ ] Add base files:
  - [ ] `registry/registry.json`
  - [ ] `schemas/agent-entry.schema.json`
  - [ ] `schemas/domain-entry.schema.json`
  - [ ] `governance/roles.json`
  - [ ] `.gitignore`
  - [ ] `LICENSE`

---

# 🧩 PHASE 2 — SNS IDENTITY MAPPING

## Required SNS IDs

- [ ] `mount.sol`
- [ ] `professorenoch.sol`
- [ ] `elise.sol`
- [ ] `sydney.sol`
- [ ] `sydtekscholars.sol`
- [ ] `sydtekuniversity.sol`

## For EACH SNS ID:

- [ ] Create `agents/{name}.json`
- [ ] Create `domains/{name}.json`
- [ ] Add entry to `registry/registry.json`

---

# 🏷️ PHASE 3 — CLASSIFY EACH SNS

For each identity, assign ONE state:

- [ ] `registry_only`
- [ ] `linked_repo`
- [ ] `dedicated_repo`

## Decision Rule (must meet ≥3 to be dedicated repo):

- [ ] Has independent codebase
- [ ] Has its own deployment pipeline
- [ ] Has its own prompt stack
- [ ] Has its own permissions model
- [ ] Has its own release cadence
- [ ] Has its own contributors

---

# 🔐 PHASE 4 — WALLET & OWNERSHIP

For EACH SNS:

- [ ] Add wallet address
- [ ] Define custody model:
  - [ ] `operator_controlled`
  - [ ] `family_controlled`
  - [ ] `organizational_controlled`
  - [ ] `multisig`
- [ ] Confirm wallet matches SNS ownership
- [ ] (Optional) Add multisig configuration

---

# 🏛️ PHASE 5 — ROLE & GOVERNANCE

Assign role class:

- [ ] `origin_node`
- [ ] `interpreter_agent`
- [ ] `legacy_node`
- [ ] `education_node`
- [ ] `institutional_node`

For EACH agent:

- [ ] Set `voting_weight`
- [ ] Define permissions list
- [ ] Validate against `governance/roles.json`

---

# 🤖 PHASE 6 — AGENT DEFINITION

For EACH SNS:

- [ ] Set agent type:
  - [ ] `guardian_node`
  - [ ] `publishing_agent`
  - [ ] `education_agent`
  - [ ] `institutional_agent`
  - [ ] `legacy_identity`
- [ ] Define capabilities list
- [ ] Set status:
  - [ ] `registry_only`
  - [ ] `planned`
  - [ ] `active_design`
  - [ ] `active`
- [ ] Add endpoint (if exists)

---

# 🔗 PHASE 7 — REPO LINKING

For EACH SNS:

- [ ] Link to existing repo OR
- [ ] Leave empty (registry only) OR
- [ ] Define new dedicated repo

## Common links:

- [ ] `canonical-index`
- [ ] `gcb-knowledge-infrastructure`
- [ ] future agent-specific repos

---

# 🌐 PHASE 8 — DOMAIN RECORDS (SNS)

For EACH SNS:

- [ ] Add website
- [ ] Add GitHub link
- [ ] Add registry reference
- [ ] Add optional:
  - [ ] Twitter
  - [ ] Discord
  - [ ] Prompt registry
- [ ] Set visibility:
  - [ ] `public`
  - [ ] `private_or_limited`

---

# 🔐 PHASE 9 — TEE / SECURE ENCLAVE READINESS

For EACH SNS:

- [ ] Set `tee.enabled` = true/false
- [ ] Set attestation status:
  - [ ] `not_applicable`
  - [ ] `not_configured`
  - [ ] `planned`
  - [ ] `active`
- [ ] Add attestation file (if applicable)

## Only REQUIRED for:

- [ ] treasury agents
- [ ] signing agents
- [ ] governance execution agents

---

# 📊 PHASE 10 — REGISTRY VALIDATION

- [ ] Confirm all SNS IDs appear in `registry.json`
- [ ] Confirm all agent files exist
- [ ] Confirm all domain files exist
- [ ] Validate against schemas
- [ ] Ensure no broken paths
- [ ] Ensure consistent naming (`.sol`)

---

# 🧠 PHASE 11 — LLM / GEO OPTIMIZATION

- [ ] Ensure all descriptions are clear + structured
- [ ] Avoid vague language (be explicit)
- [ ] Use consistent role naming
- [ ] Ensure JSON is machine-readable
- [ ] Keep fields stable across updates

---

# ⚠️ PHASE 12 — RISK CHECK

- [ ] DO NOT present SNS IDs as fake “people”
- [ ] DO define them as roles
- [ ] DO ensure wallet ownership is truthful
- [ ] DO ensure governance mapping is accurate
- [ ] DO keep symbolic vs executable clearly separated

---

# 🏁 PHASE 13 — INITIAL COMPLETION TARGET

Minimum viable registry:

- [ ] All 6 SNS IDs mapped
- [ ] All agent files created
- [ ] All domain files created
- [ ] Wallets filled in
- [ ] Roles assigned
- [ ] States assigned
- [ ] Registry.json complete

---

# 🔮 PHASE 14 — NEXT EVOLUTION

- [ ] Add `prompts/` directory
- [ ] Add agent prompt manifests
- [ ] Add GitHub Actions validator
- [ ] Add TEE attestation files
- [ ] Expand agent capabilities
- [ ] Introduce DAO governance layer

---

# 🧬 FINAL FRAME

This is not a list of names.

This is a **Named Intelligence System**:

- SNS → Identity
- Registry → Structure
- Agents → Behavior
- Tokens → Alignment
- TEEs → Trust

---

# 🏛️ TAGLINE

**Build for AI. Be remembered.**
