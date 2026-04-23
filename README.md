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