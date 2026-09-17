# QA and Release Contract

## Why independent QA exists

Generation stages can claim success while the final CSV contains missing rows, stale values, broken handoffs, unsupported specificity, or deterministic copy. Independent QA must inspect the actual artifacts and make the release decision from evidence.

## QA inputs

Independent QA must read:

- Original input CSV
- Actual customized output CSV
- Actual failed-leads CSV
- Actual run manifest
- Pinned knowledge bundle
- Stage provenance and hashes

## Blocking failures

Any of these blocks release:

- Missing or unreadable artifact
- Input/output partition mismatch
- Duplicate or missing lead
- Original field changed unexpectedly
- Missing generated field
- Subject outside 2–4 words
- Email 1 body outside 15–29 words
- Subject handoff mismatch
- Prior email handoff mismatch
- P.S. in Email 2 or Email 3
- Missing Email 1 P.S.
- Evidence grounding failure
- Em dash
- Guaranteed outcome
- Fake personalization
- Unsupported specificity
- Calendar link or aggressive CTA
- Generic fallback
- Deterministic template behavior
- Manifest mismatch
- Missing model provenance
- Failed runtime contract proof

## Batch-level deterministic check

Use the actual output batch. Inspect repeated n-grams, repeated sentence structures, and category substitutions. Compare unrelated businesses and strategies. The check should identify the affected rows and repeated pattern.

Do not fail merely because normal phrases recur. The concern is meaningful fixed construction, not ordinary language.

## Release decision

`RELEASED` requires every blocking gate to pass.

`NOT_RELEASED` is the default when a gate cannot be verified. Lack of evidence is not evidence of a pass.

## Artifact partition

A lead that fails any required stage must appear in failed-leads.csv with the original input fields and the failure details. It must not prevent successful leads from being customized.

A partial release is permitted only if the customized artifact independently passes QA and the failed artifact contains every other input row.
