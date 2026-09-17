# Cross-Stage Contract for Beans

## Purpose

This document defines the rules that apply to every Beans stage. It supplements the individual stage documents.

## Stable lead identity

Every input row receives a stable `lead_id`. The lead ID must not be derived only from row position. Preserve enough original identifying fields to detect duplicate or changed inputs.

Original row position is also recorded so order can be checked and preserved.

## Structured handoff

Each stage must return a structured object that validates against the relevant schema. The next stage receives that object, not a conversational summary.

The runtime must persist:

- Input object
- Output object
- Stage name and version
- Invocation ID
- Model name
- Knowledge-bundle commit
- Timestamp
- Content hash
- Status and error information

## Model generation boundary

The configured model must generate Email 1, Email 2, and Email 3. Python, CSV infrastructure, deterministic formatters, templates, and fallback writers may validate and persist text but may not generate or rewrite email prose.

If the native runtime cannot expose the configured model to the stage, the run must stop as `NOT_RELEASED`. A shell script or assumed API bridge is not an acceptable substitute.

## Failure isolation

A lead-level failure must not stop other leads. Each lead has its own stage status and retry state.

Failures must be explicit and durable. A lead may be:

- `customized`
- `failed`
- `needs_review`
- `in_progress`

No lead may be silently dropped.

## Retry and resume

Retries are bounded and stage-specific. A retry must create a new invocation ID and be revalidated. Completed stages with valid persisted output are not regenerated on resume.

A resumed run must verify input hash, knowledge-bundle commit, stage versions, and prior output hashes before reusing a completed result.

## Evidence lineage

Every material commercial claim in generated email must be traceable to evidence IDs from Stage 1 and the Stage 2 profile. Evidence IDs must survive through strategy selection, generation, validation, and final provenance.

## Email handoff lineage

Before Stage 5:

```text
email_1_rendered_text → email_1_hash
```

Before Stage 6:

```text
email_1_rendered_text → email_1_hash
email_2_rendered_text → email_2_hash
```

Validation compares actual persisted strings and hashes. A declaration that a handoff occurred is insufficient.

## CSV authority

The final CSV files are authoritative for release QA. In-memory objects, manifests, stage claims, and test fixtures are supporting evidence only.

## No deterministic behavior

The system must not use:

- Row-index rotation
- Modulo selection
- Phrase rotation
- Synonym rotation
- Static sentence frames
- Category substitution
- Shared fallbacks
- Previous-output reuse
- Large collections of complete email templates

Functional strategies and components may constrain meaning and structure. They may not become a disguised template library.

## Runtime proof before production

Before live processing, prove with a synthetic lead that:

1. The selected JackHamr workflow invokes the configured GPT-5.6 Luna model.
2. One lead can be passed to a stage.
3. Structured JSON can be returned and validated.
4. Exact Email 1 can be handed to Email 2.
5. Exact Email 1 and Email 2 can be handed to Email 3.
6. Stage outputs persist durably.
7. Per-lead retries and resume work.
8. The independent QA workflow can read the actual final CSV.
9. The runtime can safely process the intended batch size.

Do not create a production workflow until these capabilities are demonstrated in the authenticated JackHamr environment.
