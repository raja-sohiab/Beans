# Stage 3: Email 1 Strategy Selection

## Mission

Select the single best approved Email 1 approach for the lead using the Stage 2 commercial profile. This stage chooses a reasoning path and functional components. It does not write email prose.

## Approved approaches

### 1. `direct_offer`

Use when the service or benefit and a reasonable beneficiary are clear enough to make a direct, understated offer.

Commercial logic:

```text
People who may need what you offer can be difficult to find.
Beans can help identify and reach relevant prospects, then pass interested respondents to you.
```

Required evidence:

- Service or benefit
- Beneficiary or broad beneficiary

### 2. `referral_hypothesis`

Use when the available evidence supports a careful hypothesis that the prospect may rely on referrals, word of mouth, existing networks, or similar acquisition channels.

The hypothesis must remain a hypothesis. Do not state that referrals are definitely the prospect's current acquisition method.

Required evidence:

- Acquisition, referral, network, or word-of-mouth evidence
- Service or benefit

### 3. `pain_problem`

Use when the website evidence supports a category-level customer problem that the prospect helps solve.

The pain must describe a plausible situation at the category level, not a fabricated problem at the individual company.

Required evidence:

- Service or benefit
- Supported customer situation or problem

### 4. `qualification_uncertainty`

Use when the service is broadly understandable but the beneficiary, use case, or commercial translation remains partial or low confidence.

The message should invite a natural correction or qualification rather than pretending certainty.

Required evidence:

- Service, benefit, or benefit language

## Selection procedure

1. Read the entire Stage 2 profile.
2. List strategies whose required evidence exists.
3. Remove strategies incompatible with the evidence or confidence.
4. Select exactly one strategy.
5. Prefer the simplest honest strategy that supports a relevant offer.
6. Use `qualification_uncertainty` when specificity would otherwise be fabricated.
7. Record the reason, confidence, evidence IDs, and compatible functional components.

Do not assign strategies by row number, random choice, round-robin, modulo, phrase availability, or category rotation.

## Observation treatment

A website observation is not a fifth strategy. Where supported, a short observation can be a component inside a selected strategy. It must sound like a practical commercial observation, not a compliment or proof-of-research slogan.

Avoid artificial constructions such as:

- `Your focus on device imaging stood out.`
- `Custom apps for growing teams caught my eye.`
- `The workflow automation angle is clear.`
- `Helping manufacturers reduce downtime is compelling.`

Prefer a direct connection between the prospect's offering and the challenge of finding the people who may need it.

## Functional components

Choose component IDs by purpose, not by reusable wording. Possible component roles include:

- `service_or_benefit_reference`
- `plain_commercial_observation`
- `customer_discovery_challenge`
- `persistiq_outreach_offer`
- `interested_response_handoff`
- `short_cta_question`
- `soft_ps_intent`

Each component must declare purpose, required evidence, incompatible evidence, compatible strategies, and allowed position.

## Output contract

Return:

- Stable lead identity
- Exactly one strategy ID
- Selection reason
- Strategy confidence
- Supporting evidence IDs
- Component IDs
- A concise generation brief
- Prohibited claims or limitations to avoid

The generation brief describes meaning and constraints. It must not contain a complete email, sentence template, synonym list, or fallback copy.

## Acceptance checks

- Exactly one registered strategy is selected.
- The strategy is evidence-compatible.
- Referral and pain strategies have their required evidence.
- Low confidence is handled with conservative selection, not lead rejection.
- No prose email was generated.
- No rotation or deterministic assignment rule was used.
