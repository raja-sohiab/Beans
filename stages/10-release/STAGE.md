# Stage 10: Release or Reject

## Mission

Compute the final release decision from the independent QA report and actual artifact checks. This stage is a gate, not a copywriting stage.

## Possible decisions

### `RELEASED`

Use only when every blocking release gate passes and the actual output artifacts are available and readable.

### `NOT_RELEASED`

Use for any blocking failure, missing artifact, unverifiable handoff, manifest mismatch, failed independent QA, or unproven runtime requirement.

Preserve all artifacts and the blocker report so the run can be diagnosed or resumed.

## Required release gates

1. Beans knowledge bundle is pinned to a verified commit.
2. Actual input CSV was read successfully.
3. Input partition is complete and disjoint.
4. Original fields are preserved.
5. Customized output is readable.
6. Failed-leads output is readable.
7. Required generated columns are present.
8. Subject is 2–4 words.
9. Email 1 body is 15–29 words.
10. Email 1 includes a valid P.S.
11. Email 2 subject exactly equals Email 1 subject.
12. Email 3 subject exactly equals Email 1 subject.
13. Exact Email 1 is handed to Email 2.
14. Exact Email 1 and Email 2 are handed to Email 3.
15. Email 2 and Email 3 contain no P.S.
16. Evidence grounding passes.
17. Prohibited language is absent.
18. Deterministic behavior checks pass.
19. Manifest matches the actual written artifacts.
20. Independent final CSV QA passes.

## Partial delivery

A partial customized output may be delivered alongside the failed-leads CSV only when:

- The customized artifact itself passes all applicable QA gates.
- Every non-customized lead is present in failed-leads.csv.
- The release policy explicitly allows partial delivery.
- The decision and counts clearly state that the output is partial.

A partially successful generation is not permission to hide failures.

## Release record

The final release record must contain:

- Decision
- Run ID
- Beans version
- Knowledge-bundle commit
- Input hash
- Customized output hash
- Failed output hash
- QA report hash
- Counts
- Gate results
- Blockers
- Timestamp

No human-readable statement such as `looks good` can override a failed gate.
