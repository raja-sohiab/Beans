# Stage 6: Email 3 Generation

## Mission

Write the final follow-up using the exact Email 1 and Email 2 for the same lead. Email 3 must introduce a genuinely new, evidence-grounded commercial angle while remaining connected to the prospect's actual offering and the PersistIQ offer.

## Input and exact handoff

The runtime must pass:

- Original lead identity
- Stage 2 commercial profile and evidence
- Stage 3 strategy selection
- Exact Subject 1/2
- Exact rendered Email 1 and hash
- Exact rendered Email 2 and hash
- Pinned Email 3 rules

The agent must read the actual prior rendered text. Summaries are not a substitute.

## Subject

Subject 3 must equal Subject 1 and Subject 2 exactly. Do not change it, add `Re:`, or rotate it.

## New-angle requirement

Email 3 must have a genuinely new commercial reason, not merely different phrasing. A valid angle may come from:

- A supported customer situation
- A supported trigger or timing implication
- A different but adjacent use case
- A broader or secondary beneficiary
- A consequence or opportunity implication
- A practical next-step implication
- A supported channel, partner, lifecycle, renewal, or stakeholder angle

The angle must be grounded in Stage 1 evidence and Stage 2 interpretation. It must not contradict Email 1 or Email 2.

## Human construction

Avoid generic framing such as:

- `Another reason to consider this...`
- `One more angle...`
- `A final thought...`
- `Just wanted to reach out one last time...`

Do not use a breakup template or a category-only substitution. The new angle must change the commercial reason for contacting the prospect.

## P.S. rule

Email 3 must not contain a P.S. No P.S. marker, postscript, or second footer is permitted.

## No honest angle rule

If no distinct honest angle can be supported, do not invent one and do not use a generic fallback. Return:

```text
status: needs_review
reason: none_supported
```

That lead belongs in the review or failed artifact according to the release policy.

## Prohibited behavior

Do not:

- Generate a new unrelated pitch.
- Claim current demand or intent.
- Promise results.
- Use unsupported specificity.
- Use an em dash.
- Copy either earlier email.
- Change the subject.
- Add a P.S.
- Generate a replacement fallback.

## Output contract

Return:

- Exact subject equal to Subject 1 and Subject 2
- `email_3.greeting`
- `email_3.body`
- `email_3.signature`
- `email_3.ps_present: false`
- `new_angle_type`
- `new_angle_reason`
- Evidence IDs used
- `prior_email_1_hash`
- `prior_email_2_hash`
- Model and invocation metadata

Persist exact Email 3 and its hash before validation.

## Acceptance checks

- Exact prior emails were supplied.
- Subject equality is exact.
- The commercial angle differs materially from earlier emails.
- The angle is evidence-grounded and non-contradictory.
- No generic breakup or fallback construction is used.
- No P.S. appears.
- No em dash, guarantee, or unsupported specificity appears.
