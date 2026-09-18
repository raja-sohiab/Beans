Customer Type Derivation Contract
Purpose
Customer type is a derived field. It is not expected in the input CSV.

Source priority
Use evidence in this order:

Supplied business_type, services, and industry fields when present.
The supplied homepage.
One bounded first-party services, products, solutions, or capabilities page only when the homepage is insufficient.
Supplied non-empty fields remain preserved as original input values. Website evidence may enrich or contradict them, but must not silently overwrite them.

Homepage evidence
Use the combined evidence from:

Page title
Meta description
Homepage headings
Subheadings and supporting copy
Named services, products, or solutions
Benefits
Features
Industries or sectors
Explicit audience or customer references
Calls to action
Case studies or client references visible on the permitted page
Do not infer customer type from the company name alone.

Derivation rule
Infer the narrowest defensible customer type that would plausibly need the offering.

The derived customer type must be traceable to evidence IDs.

If the evidence supports only a broad category, return the broad category with low or medium confidence.

If evidence is insufficient, return:


unknown
with low confidence and a limitation.

Prohibited inference
Do not infer:

Named companies
Specific decision-makers
Active buying intent
Budget
Urgency
Current demand
Guaranteed need
unless explicitly supported by permitted source evidence.

Required output
Return:

customer_type.value
customer_type.confidence
customer_type.evidence_ids
customer_type.reasoning_summary
customer_type.limitations
Do not write email copy during customer-type derivation.
