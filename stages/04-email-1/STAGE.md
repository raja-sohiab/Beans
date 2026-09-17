# Stage 4: Email 1 Generation

## Mission

Write the first customized outreach email from the approved Stage 3 brief. This stage generates the subject, Email 1 body, signature, and P.S. It does not research the website, choose a strategy, or generate Email 2 or Email 3.

## Input

Consume:

- Original lead fields
- Stage 1 evidence record
- Stage 2 commercial profile
- Stage 3 strategy selection and generation brief
- Pinned PersistIQ positioning and Email 1 rules

The model must receive structured data and return structured JSON. The runtime must record model name, invocation ID, knowledge-bundle commit, and timestamp for the invocation.

## Greeting rule

If a valid first name is present in the input CSV, use it naturally.

If the first name is missing, blank, malformed, or unavailable, do not guess it. Use a name-free greeting such as:

- `Hi,`
- `Hello,`
- `Hi there,`
- `Hey,`

The last name must not be used as a substitute for a missing first name unless an explicit project rule later approves that behavior.

## Subject rule

The subject must be:

- 2–4 words
- Natural and understated
- Relevant to the selected strategy
- Consistent across Email 1, Email 2, and Email 3
- Free of hype, guarantees, pressure, and fabricated specificity

## Main body rule

Email 1's main body must contain 15–29 words, excluding the greeting, signature, and P.S. The runtime must calculate and validate the count from the actual rendered text.

The body should weave this commercial logic:

```text
prospect service or benefit
→ finding people who need it is a separate challenge
→ Beans/PersistIQ can help find and reach them
→ interested respondents can be passed to the prospect
→ short natural CTA
```

The message should be commercial but understated, direct, and human. It must not read as a polished marketing slogan.

## Website observation rule

Do not use a decorative website-observation strategy. If an observation is useful, express the whole observation in one short sentence or clause of approximately 4–9 words, then immediately connect it to the offer.

The observation should make the prospect feel the sender understood the business without copying website wording into the email.

Avoid:

- `Your focus on device imaging stood out.`
- `Custom apps for growing teams caught my eye.`
- `The workflow automation angle is clear.`
- `Helping manufacturers reduce downtime is compelling.`

Prefer the commercial contrast represented by examples such as:

- `Finding manufacturers looking to cut downtime can be tough.`
- `Building custom mobile apps and finding who needs them are different baskets.`
- `Banks needing document workflow might not find you.`
- `The way you focus on scientific software, I focus on finding who might need it.`
- `You seem focused on commercial roofing; I focus on finding companies that may need it.`
- `Plenty of users may be looking for Windows device management.`

These are directional examples of meaning, not templates to copy.

## PersistIQ offer

The offer is to help identify and reach relevant potential customers who may need what the prospect offers, then pass interested respondents to the prospect.

Use non-guaranteed language such as `can help`, `could help`, `find`, `reach`, `identify`, or `pass interested respondents`. Do not promise leads, meetings, customers, revenue, or conversions.

## CTA rule

Use one primary CTA. It should normally be 1–5 words or a short contextual question, for example:

- `Worth a chat?`
- `Open to discussing?`
- `Would that be useful?`
- `Worth exploring?`

Do not use a calendar link, multiple questions, pressure, or a generic `let me know` as the only commercial close.

## P.S. rule

Email 1 includes a P.S. The P.S. is a soft opt-out, relevance check, or low-pressure permission line. It is not a second pitch and must not introduce unsupported facts.

## Signature

Use the configured sender signature supplied by the production runtime. Do not invent sender identity or company claims inside the stage.

## Prohibited construction

Do not:

- Use em dashes.
- Copy a complete reusable template.
- Rotate phrases or synonyms.
- Select wording by row index.
- Substitute only a category name inside a fixed sentence.
- Use a shared fallback when generation is difficult.
- Add unsupported specificity.
- Claim to have personally observed something not supported by the evidence record.
- Mention research mechanics or internal strategy IDs.

## Output contract

Return structured fields:

- `subject`
- `email_1.greeting`
- `email_1.body`
- `email_1.signature`
- `email_1.ps`
- `body_word_count`
- `observation_used`
- `evidence_ids_used`
- `strategy_id`
- `model`
- `invocation_id`

The rendered email text must also be persisted exactly, with a hash, before Stage 5 runs.

## Acceptance checks

- Subject is 2–4 words.
- Main body is 15–29 words.
- Greeting follows the name rule.
- The offer is connected to the prospect's actual service or benefit.
- Any observation is short, plain, and commercial rather than decorative praise.
- One primary CTA is present.
- Email 1 has a P.S.
- No prohibited language or em dash appears.
- Every material claim maps to evidence.
- Text was generated by the configured model, not infrastructure.
