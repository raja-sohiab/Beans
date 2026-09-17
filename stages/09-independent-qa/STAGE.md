# Stage 9: Independent Final-Artifact QA

## Mission

Independently inspect the actual final CSV artifacts and determine whether they satisfy the Beans contract. QA is independent from generation and must not trust an agent statement, stage status, manifest claim, or hand-authored fixture without comparing it to the files.

## Independence requirement

The QA invocation must receive paths or durable artifact references to:

- Actual input CSV
- Actual `customized_leads.csv`
- Actual `failed_leads.csv`
- Actual `run_manifest.json`
- Pinned Beans knowledge-bundle commit
- Validator version and rules

QA must open and parse the files itself. It must not validate only JSON emitted by the generation stages.

## Required checks

### Input and row integrity

- Input row count matches the partition count.
- Every input row appears exactly once in customized or failed output.
- No duplicate stable lead IDs.
- Original fields and values are preserved.
- Row order is correct according to the contract.

### Generated field integrity

- Required subject and email columns exist.
- No required generated value is missing.
- Actual CSV values match validated stage records.
- No unexpected extra output column undermines downstream use.

### Email 1

- Subject contains 2–4 words.
- Body contains 15–29 words according to the actual rendered CSV field.
- Greeting follows the available-name rule.
- P.S. is present.
- One primary CTA exists.
- Claims are grounded in the evidence record.

### Email 2

- Subject equals Email 1 exactly.
- Exact Email 1 handoff hash matches persisted provenance.
- Email 2 continues the same proposition.
- Email 2 is not a duplicate or synonym-only rewrite.
- No P.S. exists.

### Email 3

- Subject equals Email 1 and Email 2 exactly.
- Exact Email 1 and Email 2 handoff hashes match.
- Email 3 contains a distinct evidence-grounded commercial angle.
- No generic breakup fallback or category-only substitution exists.
- No P.S. exists.

### Policy and language

Reject blocking violations for:

- Em dash
- Guaranteed outcomes
- Unsupported specificity
- Fake personalization
- Aggressive CTA or calendar link
- Generic fallback
- Template construction
- Prohibited PersistIQ positioning

### Deterministic behavior

Analyze the actual batch, not a separate fixture. Look for:

- Seven-template or any fixed-template rotation
- Modulo or row-index effects
- Same sentence skeleton with only categories substituted
- Reused complete email bodies
- Shared fallbacks
- Identical later emails across unrelated leads

A natural phrase appearing more than once is not enough to fail the batch. The report must identify the repeated construction and affected rows.

### Manifest consistency

Recalculate counts, hashes, partition, order, and decision from the actual files. Any mismatch is a blocking failure.

## QA output

Produce a QA report containing:

- Run ID and artifact hashes
- Knowledge-bundle commit
- Files actually read
- Checks performed
- Pass/fail result for every gate
- Affected row IDs
- Evidence for every blocker
- Warnings and non-blocking observations
- Recommendation: `RELEASED` or `NOT_RELEASED`

QA must not edit the final CSV. If correction is required, send the run back through generation/assembly and repeat independent QA.
