# Stage 7: Per-Lead Validation

## Mission

Validate the actual rendered lead record before it enters the output CSV. This stage checks facts, strings, handoffs, policy, and construction quality. It does not rewrite emails, generate replacements, or silently repair failures.

## Input

Read the actual persisted record for one lead, including:

- Original input row
- Stage 1 evidence
- Stage 2 profile
- Stage 3 strategy selection
- Exact subject
- Exact Email 1, Email 2, and Email 3
- Model invocation metadata
- Exact handoff hashes

## Identity and evidence checks

- Original lead identity is unchanged.
- Original row position is present.
- Original fields are preserved.
- Website evidence exists for material personalization claims.
- Inferred customer types are labelled as inference.
- The PersistIQ offer is consistent with the approved positioning.
- No claim says the prospect currently has demand or intent unless supported.

## Email 1 checks

- Subject is 2–4 words.
- Main body is 15–29 words, counted from the actual rendered field.
- Greeting follows the first-name availability rule.
- One primary CTA is present.
- P.S. is present.
- Any observation is approximately 4–9 words when used and is commercial, plain, and evidence-grounded.
- The body connects the prospect's benefit to finding and reaching relevant potential customers.
- Interested respondents are described as a possible handoff, not a guarantee.

## Email 2 checks

- The exact Email 1 text was handed off and its hash matches.
- Subject 2 equals Subject 1 exactly.
- Email 2 continues the same core commercial proposition.
- Email 2 is not a duplicate or synonym rewrite.
- Email 2 has no P.S.
- Greeting and signature are valid.

## Email 3 checks

- The exact Email 1 and Email 2 texts were handed off and hashes match.
- Subject 3 equals Subject 1 exactly.
- Email 3 contains a genuinely new commercial angle.
- The new angle is evidence-grounded and non-contradictory.
- Email 3 is not a category-only substitution or generic breakup message.
- Email 3 has no P.S.
- Greeting and signature are valid.

## Global prohibited-language checks

Reject the row for:

- Em dash
- Guarantees of leads, meetings, customers, revenue, conversions, or outcomes
- Fake website personalization
- Unsupported specificity
- Calendar links or pressure
- Aggressive CTA
- Generic fallback copy
- Complete template reuse
- Row-index, random, phrase, synonym, or category rotation evidence
- Missing model invocation metadata

## Construction-quality checks

The validator should compare the row against the batch for suspicious determinism:

- Identical sentence skeletons across many leads
- Only category words changing
- Repeated phrase clusters inconsistent with natural variation
- Reused complete email bodies
- Identical Email 2 or Email 3 structures across unrelated businesses

A repeated short phrase is not automatically a failure. The check must identify meaningful deterministic construction, not penalize normal language.

## Retry policy

A failed row may receive a bounded retry only when the failure is plausibly a generation error and the runtime invokes the configured model again. Every retry must produce a new invocation ID and be fully revalidated.

There is no deterministic repair writer and no shared fallback. If the retry fails, send the row to the failed or review artifact with the exact failure reason.

## Output

Return a validation record:

- `lead_id`
- `status`: `customized`, `failed`, or `needs_review`
- Check results
- Blocking failures
- Warnings
- Retry count
- Final text hashes
- Evidence IDs checked
- Validator version

A row may enter `customized` only when all blocking checks pass.
