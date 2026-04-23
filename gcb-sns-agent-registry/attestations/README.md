# Attestations

This directory stores references and documents related to:

- secure enclaves
- trusted execution environments
- signing policies
- remote attestation evidence
- hardware-backed execution references

## Purpose

Not every agent requires TEE-backed execution.

This directory should only be used when an agent moves from:

- symbolic identity
- informational agent
- content agent

into:

- signing agent
- treasury agent
- custody-sensitive agent
- autonomous governance agent

## Suggested future files

- `mount.sol.attestation.json`
- `treasury-guardian.policy.json`
- `tee-provider-notes.md`

## Current status

TEE support is planned but not yet configured.