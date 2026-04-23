# ✅ GCB SNS Agent Registry — Build & Audit Checklist

The GCB SNS Agent Registry is the canonical identity and routing layer for the Goldstonian Concordance Bible ecosystem.

This checklist is designed for:

- rapid execution
- ongoing auditing
- AI / LLM readability
- contributor onboarding
- governance transparency
- long-horizon citability

---

# 🧠 CORE PRINCIPLE

**SNS = Identity**  
**Registry = Map**  
**Repo = Source of Truth**  
**Agent = Behavior**  
**TEE = Trust**

---

# 🪞 PHASE 1 — REPO INITIALIZATION

- [ ] Create GitHub repo: `gcb-sns-agent-registry`
- [ ] Add all base folders:
  - [ ] `agents/`
  - [ ] `domains/`
  - [ ] `schemas/`
  - [ ] `registry/`
  - [ ] `governance/`
  - [ ] `attestations/`
  - [ ] `.github/workflows/`
  - [ ] `hf/`
- [ ] Add base files:
  - [ ] `registry/registry.json`
  - [ ] `agents.json`
  - [ ] `schemas/agent-entry.schema.json`
  - [ ] `schemas/domain-entry.schema.json`
  - [ ] `governance/roles.json`
  - [ ] `GOVERNANCE.md`
  - [ ] `ROUTING.md`
  - [ ] `STATUS.md`
  - [ ] `CITATION.cff`
  - [ ] `llms.txt`
  - [ ] `.gitignore`
  - [ ] `LICENSE`

---

# 💧 PHASE 2 — SNS IDENTITY MAPPING

## Required SNS IDs

- [ ] `themount.sol`
- [ ] `professorenoch.sol`
- [ ] `elisegoldston.sol`
- [ ] `sydneyleona.sol`
- [ ] `sydtekscholars.sol`
- [ ] `sydtekuniversity.sol`

## For EACH SNS ID

- [ ] Create `agents/{name}.json`
- [ ] Create `domains/{name}.json`
- [ ] Add entry to `registry/registry.json`
- [ ] Add entry to top-level `agents.json`

## Required purpose documentation

- [ ] `themount.sol` documented as origin / guardian / treasury-anchor node
- [ ] `professorenoch.sol` documented as interpreter / publishing node
- [ ] `elisegoldston.sol` documented as legacy family node with custody rationale
- [ ] `sydneyleona.sol` documented as future stewardship / legacy node with custody rationale
- [ ] `sydtekscholars.sol` documented as education node
- [ ] `sydtekuniversity.sol` documented as institutional authority node

---

# 🔥 PHASE 3 — CLASSIFY EACH SNS

For each identity, assign ONE state:

- [ ] `registry_only`
- [ ] `linked_repo`
- [ ] `dedicated_repo`

## Decision Rule

Use `dedicated_repo` only if the identity meets **3 or more** of the following:

- [ ] Has independent codebase
- [ ] Has its own deployment pipeline
- [ ] Has its own prompt stack
- [ ] Has its own permissions model
- [ ] Has its own release cadence
- [ ] Has its own contributors

## Tie-breaker Rule

- [ ] In case of tie or uncertainty, default to `linked_repo` until an independent codebase exists

## Schema discipline

- [ ] Add `schema_version` to every JSON record
- [ ] Pin current schema convention to `1.0.0`
- [ ] Prevent schema drift across releases

---

# 🔐 PHASE 4 — WALLET & OWNERSHIP

For EACH SNS:

- [ ] Add wallet address
- [ ] Define custody model:
  - [ ] `operator_controlled`
  - [ ] `family_controlled`
  - [ ] `organizational_controlled`
  - [ ] `multisig_or_guarded_wallet`
- [ ] Confirm wallet matches SNS ownership
- [ ] Add custody rationale where relevant
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
- [ ] Ensure human-readable explanation exists in `GOVERNANCE.md`

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
- [ ] Leave empty (`registry_only`) OR
- [ ] Define new dedicated repo

## Common links

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

## Only REQUIRED for

- [ ] treasury agents
- [ ] signing agents
- [ ] governance execution agents

---

# ✅ PHASE 10 — REGISTRY VALIDATION

- [ ] Confirm all SNS IDs appear in `registry.json`
- [ ] Confirm all agent files exist
- [ ] Confirm all domain files exist
- [ ] Validate against schemas
- [ ] Ensure no broken paths
- [ ] Ensure consistent naming (`.sol`)
- [ ] Run GitHub Actions validation successfully
- [ ] Update `STATUS.md`

---

# 🧠 PHASE 11 — LLM / GEO OPTIMIZATION

- [ ] Ensure all descriptions are clear and structured
- [ ] Avoid vague language
- [ ] Use consistent role naming
- [ ] Ensure JSON is machine-readable
- [ ] Keep fields stable across updates
- [ ] Add top-level `llms.txt`
- [ ] Add flat `agents.json`
- [ ] Add Hugging Face dataset mirror for discovery

---

# ⚠️ PHASE 12 — RISK CHECK

- [ ] DO NOT present SNS IDs as fake people
- [ ] DO define them as roles
- [ ] DO ensure wallet ownership is truthful
- [ ] DO ensure governance mapping is accurate
- [ ] DO keep symbolic vs executable clearly separated
- [ ] DO preserve custody clarity for family-linked nodes

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
- [ ] `agents.json` complete
- [ ] `llms.txt` present
- [ ] `CITATION.cff` present
- [ ] GitHub validator active

---

# 🔮 PHASE 14 — NEXT EVOLUTION

## Trigger conditions

- [ ] Add `prompts/` directory when 2 or more agents require formal prompt manifests
- [ ] Add agent prompt manifests when any agent reaches `active_design`
- [ ] Add TEE attestation files when any agent handles signing, custody, or treasury actions
- [ ] Add DAO governance layer when 4 or more agents reach `active` status
- [ ] Expand agent capabilities when independent endpoints are deployed

## Ownership

- [ ] Registry owner: Justin Goldston, PhD
- [ ] Institutional alignment: SydTek University
- [ ] Publishing alignment: G. Rune Publishing

---

# 📊 REPO STATUS SIGNALS

- [ ] Maintain `STATUS.md`
- [ ] Track registry completeness %
- [ ] Track active SNS count
- [ ] Track last validated date
- [ ] Track schema version

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