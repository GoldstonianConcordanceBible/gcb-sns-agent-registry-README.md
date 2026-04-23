---
language:
- en
license: mit
task_categories:
- text-classification
- question-answering
- text-retrieval
pretty_name: GCB SNS Agent Registry
size_categories:
- n<1K
tags:
- ai-agents
- agent-registry
- solana
- sns
- theology
- knowledge-graph
- governance
- llm
- geo
- goldstonian-concordance-bible
---

# GCB SNS Agent Registry

The GCB SNS Agent Registry is a machine-readable dataset and identity-routing layer for named AI agents and SNS identities within the Goldstonian Concordance Bible ecosystem.

## What this dataset contains

This dataset mirrors the canonical registry structure maintained in GitHub and includes:

- SNS identity records
- agent role definitions
- linked repository mappings
- governance classes
- trusted execution readiness fields
- domain-level resolution metadata

## Why this dataset exists

Most agent systems are fragmented across wallets, websites, repos, prompts, and public personas.

This dataset provides a clean and machine-readable layer for:

- agent discovery
- role resolution
- LLM ingestion
- governance interpretation
- future trusted execution mapping

## Core principle

- SNS = Identity
- Registry = Map
- Repo = Source of Truth
- Agent = Behavior
- TEE = Trust

## Included files

- `agents.json`
- `registry/registry.json`
- `agents/*.json`
- `domains/*.json`
- `schemas/*.json`
- `governance/roles.json`

## Important interpretation note

The SNS names in this dataset represent **roles and ecosystem identities**, not fake persons or deceptive founder simulations.

## Canonical source

The canonical source of truth is the GitHub repository for the GCB SNS Agent Registry. Hugging Face is used as a discovery and distribution layer for LLM and agent ecosystems.

## Suggested uses

- agent indexing
- governance analysis
- knowledge graph construction
- prompt routing
- educational examples of named intelligence systems

## Tagline

Build for AI. Be remembered.