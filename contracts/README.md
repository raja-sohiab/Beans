# Beans Contract Index

These contracts define cross-stage invariants. They do not, by themselves, provide runtime enforcement.

## Authority

When documents conflict, precedence is:

1. Runtime-enforced validation and persisted artifact checks
2. Versioned schemas in `schemas/`
3. Cross-stage contracts in the repository root
4. Contract documents in `contracts/`
5. Stage-specific `QA.md`
6. Stage-specific `STAGE.md` and `RULES.md`
7. Prompt-level instructions

No prompt may weaken a schema, identity rule, handoff rule, QA gate, or release gate.

## Contracts

- `identity-contract.md` — immutable run, lead, and row identity
- `sender-contract.md` — runtime-owned sender signature
- `handoff-contract.md` — exact persisted Email 1 and Email 2 handoffs
- `stage-record.schema.json` — stage provenance record
- `generation-output.schema.json` — generation payload baseline
- `retry-resume-contract.md` — bounded retries and safe resume
- `artifact-contract.md` — input/output artifact and partition rules
- `integrity-regressions.md` — mandatory regression cases

## Runtime boundary

The runtime must own:

- lead identity assignment
- sender signature configuration
- schema validation
- canonical serialization
- SHA-256 computation
- durable persistence
- exact handoffs
- retry and resume
- CSV assembly
- independent QA
- release gating

Models may generate evidence interpretations and email prose, but may not claim runtime enforcement or invent provenance.
