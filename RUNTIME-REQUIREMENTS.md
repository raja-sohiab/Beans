# JackHamr Runtime Requirements for Beans

This document is a capability contract, not an assumption that the current JackHamr UI already provides every capability.

## Required native execution mechanism

Before production implementation, identify and document the exact JackHamr mechanism that:

1. Receives one lead/item as stage input.
2. Spawns or invokes the configured stage skill.
3. Exposes the workflow-selected model, specifically the configured GPT-5.6 Luna model, to that invocation.
4. Returns structured JSON.
5. Persists the stage output.
6. Passes exact output to the next stage.
7. Retries one item without corrupting other items.
8. Resumes completed items without reprocessing them.
9. Allows an independent QA workflow to read the actual final CSV.

## Evidence required

The capability must be demonstrated in the authenticated JackHamr UI/runtime with a synthetic test. Documentation or a chat answer is not sufficient.

Record:

- Exact UI location and configuration name
- Workflow name
- Stage name
- Skill name
- Model setting and override behavior
- Input shape
- Output shape
- Persistence location/reference
- Retry behavior
- Resume behavior
- Artifact handoff reference
- QA read path
- Batch-size limit or observed throughput

## Model boundary

The fact that the main agent chat uses GPT-5.6 Luna does not prove that a shell script, external Python program, or arbitrary workflow stage can call it. Beans must use the native JackHamr model path once proven. Do not create a fake API bridge.

## Structured outputs

Each generation stage should return JSON validated against the repository schema. If the runtime cannot enforce JSON output or detect malformed output, generation must fail closed for that item.

## Bulk processing

A 1,000-lead run must be modeled as independent per-lead work with durable state, bounded concurrency, per-item retries, and resume. Do not rely on one giant prompt or one unbounded chat context.

The exact concurrency limit must be discovered from JackHamr, measured with a safe synthetic batch, and recorded before production use.

## File handling

The runtime must write the final CSV to a durable artifact location, then independent QA must open that exact artifact. A manifest saying a file exists is insufficient.

## Stop condition

If any required capability is missing or unproven, do not process live campaign files and do not claim Beans is production-ready.
