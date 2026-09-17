# Functional Component Registry Guidance

## Principle

A component expresses a job the model must accomplish. It is not a phrase, synonym, sentence frame, or reusable email fragment.

The model chooses wording and sentence construction within the evidence and strategy boundaries.

## Required component fields

Each component record must define:

```yaml
id: unique_component_id
purpose: what the component accomplishes
when_to_use: evidence and situation requirements
required_evidence: evidence types or IDs required
incompatible_evidence: evidence that forbids use
compatible_strategies: strategy IDs
allowed_positions: permitted location in the email
quality_checks: checks applied after generation
```

## Initial component roles

### Service or benefit reference

Purpose: connect the email to what the prospect actually offers.

Required evidence: service, product, solution, benefit, or problem evidence.

Incompatible evidence: no usable offering evidence.

### Plain commercial observation

Purpose: show practical understanding without praise, flattery, or copied website wording.

Required evidence: a clear offering or benefit and a supported buyer-discovery challenge.

Incompatible evidence: homepage failure or unsupported specificity.

### Customer discovery challenge

Purpose: express that finding people who need the prospect's offering is a separate challenge.

Required evidence: prospect service/benefit and a reasonable beneficiary.

Incompatible evidence: a claim that current prospects are actively searching or that demand is known.

### PersistIQ outreach offer

Purpose: offer to identify and reach relevant potential customers through outbound prospecting.

Required evidence: service/benefit and beneficiary or broad beneficiary.

Incompatible evidence: no honest commercial connection.

### Interested-response handoff

Purpose: explain that interested respondents can be passed to the prospect.

Required evidence: PersistIQ outreach offer.

Incompatible evidence: guarantee language.

### Short CTA question

Purpose: invite a low-pressure next step.

Required evidence: a complete preceding commercial idea.

Incompatible evidence: aggressive or unsupported call to action.

### Soft P.S. intent

Purpose: give Email 1 a low-pressure relevance check or opt-out line.

Required evidence: Email 1 context.

Incompatible evidence: a second pitch or new unsupported claim.

### Email 2 continuation

Purpose: reinforce, clarify, qualify, or make the same offer easier to understand.

Required evidence: exact Email 1 and its commercial proposition.

Incompatible evidence: unrelated new pitch.

### Email 3 new angle

Purpose: introduce a distinct evidence-grounded commercial reason.

Required evidence: exact Email 1, exact Email 2, and a supported new angle.

Incompatible evidence: no distinct angle, contradiction, or generic fallback.

## Forbidden component design

Do not create components that are merely:

- Synonym sets
- Greeting rotations
- CTA phrase lists used mechanically
- Complete email paragraphs
- Category substitution slots
- Seven or more fixed email skeletons
- Shared fallbacks
