# Stage 8: Output Assembly and Artifact Persistence

## Mission

Write the validated results into durable, auditable artifacts. This stage copies validated values and computes manifest data. It does not generate, rewrite, rotate, repair, or fill email copy.

## Required artifacts

### 1. `customized_leads.csv`

Include only rows whose Stage 7 status is `customized`. Preserve:

- Original row order among customized rows
- All original input columns and values
- Stable lead ID
- Approved generated fields
- Any required evidence or provenance references

The exact output fields and CSV quoting rules must be versioned in the production contract.

### 2. `failed_leads.csv`

Include every input row that did not become `customized`, including:

- Stage 1 homepage failures
- Stage 2/3 review outcomes, if policy routes them to failure/review
- Generation failures
- Validation failures
- `needs_review` outcomes
- Retry exhaustion
- Runtime or persistence errors

Preserve all original input fields and add:

- `failure_stage`
- `failure_status`
- `failure_reason`
- `failure_detail`
- `retry_count`
- `last_invocation_id`, when available

No failed lead may disappear.

### 3. `run_manifest.json`

The manifest must be derived after re-reading the written CSV files. It must include:

- Run ID
- Beans version
- Pinned knowledge-bundle commit
- Input file hash
- Customized output hash
- Failed output hash
- Input row count
- Customized row count
- Failed row count
- Complete lead partition map
- Stage status counts
- QA status
- Final release decision

## Partition invariant

Every input row must appear exactly once in either customized or failed output.

The two outputs must be disjoint by stable `lead_id`. Their combined count must equal the input count. No row may be omitted, duplicated, or silently replaced.

## Order invariant

Original input order must be retained in customized output and failed output unless an explicit, versioned contract says otherwise. The manifest must record the order map or enough information to verify it.

## Persistence rules

Write each artifact atomically where the runtime supports it. Store a completed artifact only after the write succeeds. Re-read it from storage before declaring it valid.

The runtime must support resumption without regenerating completed successful stages. A resumed run must use stable lead IDs, stage records, hashes, and invocation metadata.

## Prohibited behavior

- No email prose generation.
- No missing-field filler.
- No fallback copy.
- No sorting by company or email unless explicitly required and recorded.
- No manifest values copied from an in-memory claim without artifact reread.
- No deletion of failed rows.

## Acceptance checks

- Both CSVs are readable.
- Every input row is represented exactly once.
- Original fields are preserved exactly according to CSV serialization rules.
- Generated fields equal the validated text.
- Counts and hashes come from actual written files.
- Manifest schema validation passes.
