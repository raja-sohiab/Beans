# Stage 2: Business Understanding and Commercial Translation

## Mission

Turn Stage 1 website evidence into a conservative commercial profile that can support outreach. This stage does not write email copy and does not choose the Email 1 strategy.

The commercial chain is:

```text
what the prospect offers
→ core benefit or problem addressed
→ who may benefit
→ what those potential customers may need
→ how PersistIQ can help find and reach relevant prospects
```

## Important behavior: fail-soft

Stage 2 must not fail a lead merely because it cannot produce a highly specific commercial profile.

This stage remains valid when:

- No service can be identified with certainty.
- No narrowly defined beneficiary can be identified.
- Website evidence is contradictory.
- Commercial translation would otherwise require fabrication.

In these cases, return a broad, low-confidence profile with explicit limitations. Only Stage 1's inability to obtain usable homepage content makes the lead unprocessable at this point.

## Input

Consume only the structured Stage 1 research record and the pinned Beans knowledge bundle. Do not perform new website research in this stage.

## Required interpretation

Identify, separately:

1. `observed_offering`: what the website directly says it provides.
2. `core_benefits`: the outcomes or benefits directly stated or conservatively implied.
3. `problem_addressed`: the problem the offering appears designed to solve.
4. `explicit_customer_types`: customer types directly named by the website.
5. `inferred_beneficiaries`: broad groups that could reasonably benefit when explicit customer types are absent.
6. `likely_customer_need`: the need those beneficiaries may have, written as a possibility rather than a fact.
7. `persistiq_relevance`: how finding and reaching relevant potential customers could relate to the prospect's offering.
8. `commercial_confidence`: high, medium, or low.
9. `limitations`: ambiguity, contradictions, missing pages, or evidence gaps.

## Commercial translation rule

The PersistIQ offer must be connected to the prospect's actual service or benefit:

> Find and reach relevant potential customers who may need what the prospect offers, then pass interested respondents to the prospect.

Use this as a capability, not a guarantee. Do not claim that prospects are currently searching, that leads already exist, or that PersistIQ will produce a specific outcome.

## Evidence discipline

Every statement in the commercial profile must point to one or more Stage 1 evidence IDs. Distinguish:

- What is observed.
- What is inferred.
- What remains unknown.

When evidence conflicts, preserve the conflict, select the least specific interpretation that remains accurate, and reduce confidence. Never resolve contradictions by inventing a story.

## Customer inference

If customer types are explicitly named, use them with the same level of specificity.

If they are not named, infer only a broad beneficiary from the service, product, problem, or benefit. Do not turn a broad beneficiary into a fabricated role such as CTO, VP, procurement manager, or founder.

## Output contract

Return a structured commercial profile with:

- Stable lead identity and original position
- Stage 1 status
- Observed offering
- Core benefits
- Problem addressed
- Explicit customer types
- Inferred beneficiaries
- Possible customer need
- PersistIQ relevance
- Evidence IDs for each claim
- Confidence per major claim
- Limitations and contradictions
- `status`: `complete` or `partial`

Never include a subject line, email body, P.S., strategy ID, component ID, or finished CTA.

## Acceptance checks

- The profile is supported by Stage 1 evidence.
- Observed and inferred information are separated.
- Beneficiary inference is broad and honest where needed.
- No current intent or demand is invented.
- PersistIQ relevance is phrased as an offer to find and reach relevant prospects.
- Uncertainty is recorded rather than treated as a hard failure.
- No email prose was generated.
