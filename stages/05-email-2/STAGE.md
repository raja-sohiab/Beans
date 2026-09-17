# Stage 5: Email 2 Generation

## Mission

Write a natural follow-up that continues the exact Email 1 for the same lead. Email 2 is not a new cold pitch and is not a mechanical follow-up formula.

## Input and exact handoff

The runtime must pass:

- Original lead identity
- Stage 2 commercial profile
- Stage 3 strategy selection
- Exact rendered Subject 1
- Exact rendered Email 1, including greeting, body, signature, and P.S.
- Email 1 hash
- Pinned Email 2 rules

The exact Email 1 text must be persisted before this invocation. The agent must not reconstruct Email 1 from fragments or a summary.

## Subject

Subject 2 must equal Subject 1 exactly. Do not create a new subject, add `Re:`, change capitalization, or rotate wording.

## Greeting and signature

Use the same greeting policy as Email 1. If a valid first name was absent, do not invent one in Email 2. Use the configured sender signature.

## Body purpose

Email 2 may:

- Reinforce the same value proposition.
- Clarify what finding and reaching potential customers means.
- Make the practical next step easier to understand.
- Qualify whether the prospect handles the relevant customer segment.
- Add a reasonable timing or operating implication supported by the evidence.

It must continue the same core value. It must not introduce an unrelated pitch or a new unsupported service.

## Human construction

The follow-up should sound like a person continuing a conversation, not like a scheduled sequence token. It may be shorter than Email 1. It must contain meaningful new construction rather than copying Email 1 with synonyms.

Do not use generic filler such as:

- `Just following up.`
- `Bumping this up.`
- `Wanted to circle back.`
- `Another quick thought.`

unless the surrounding sentence adds real, evidence-grounded meaning. Avoid a rigid follow-up formula across rows.

## P.S. rule

Email 2 must not contain a P.S. No P.S. field, P.S. marker, postscript, or second footer may appear.

## Prohibited behavior

Do not:

- Restart the entire pitch.
- Introduce a different service or unrelated customer category.
- Add unsupported claims.
- Use an em dash.
- Use a template or fallback.
- Rewrite Email 1 in disguised form.
- Change the subject.
- Generate Email 3 in the same invocation.

## Output contract

Return:

- Exact `subject` equal to Subject 1
- `email_2.greeting`
- `email_2.body`
- `email_2.signature`
- `email_2.ps_present: false`
- Evidence IDs used
- `prior_email_1_hash`
- Model and invocation metadata

Persist the exact rendered Email 2 and its hash before Stage 6 runs.

## Acceptance checks

- Exact Email 1 was available to the model.
- Subject 2 equals Subject 1 byte-for-byte after the defined CSV serialization rules.
- Email 2 continues the same core proposition.
- Email 2 is not a copy or synonym substitution.
- Email 2 contains no P.S.
- Greeting and signature are valid.
- No em dash or unsupported specificity appears.
