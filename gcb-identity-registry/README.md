# GCB Identity Registry

The **GCB Identity Registry** is the canonical identity layer for the Goldstonian Concordance Bible (GCB) ecosystem.

It provides a structured, machine-readable registry for:

- organizations
- brands
- agents
- people
- projects
- future credentials and permissions

This repository is the **identity database layer**, not the final resolver protocol.

## Why this exists

Traditional naming systems such as wallet names or domain names are not sufficient to represent the semantic complexity of the GCB ecosystem.

The GCB ecosystem includes:

- multiple institutions
- multiple publishing and media entities
- multiple tokenized environments
- multiple AI agent types
- multiple identity and governance roles

This registry creates a canonical, versioned foundation that can later support:

- custom resolver APIs
- W3C DID integration
- credential layers
- agent routing and permissions
- GEO and LLM ingestion

## Current scope

This repository currently includes:

- canonical schemas
- entity records
- agent records
- organization records
- base validation tooling
- `llms.txt` for LLM discovery
- `AGENTS.md` for agent-facing interpretation

## Initial architecture

Identity records use a soft namespace format:

- `gcb:person:...`
- `gcb:org:...`
- `gcb:brand:...`
- `gcb:agent:...`
- `gcb:project:...`

This is intentionally lightweight for early iteration.

## Initial entities

The first scaffold includes:

- G. Rune Publishing
- G Films
- Justin Goldston
- GCB Orchestrator

## Long-term direction

This repository is designed to evolve toward:

- JSON-LD identity documents
- resolver endpoints
- DID-compatible formats
- institutional and on-chain identity linking
- agent accountability frameworks

## Core principle

SNS or wallet identity alone is not the full strategy.

The stack is:

1. wallet or on-chain identity anchor
2. canonical identity record
3. crawlable public repository
4. future resolver infrastructure

## Status

Scaffold v0.1.0

This version is intended to establish a clean foundation for future audits, extensions, and protocol development.