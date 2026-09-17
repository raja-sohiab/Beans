# Stage 1: Website Research and Evidence Capture

## Mission

Research each qualified PersistIQ lead's website narrowly and factually. The stage establishes what the prospect appears to sell, what problem or benefit it addresses, and who may benefit. It does not write emails, select an email strategy, or infer unsupported business facts.

## Input

The complete original CSV row, including at minimum:

- Email
- FirstName, if present
- LastName, if present
- Company
- Website
- Any other source fields supplied by the user

The input row must receive a stable `lead_id` and original row position. Both must be preserved through the entire pipeline.

## Bounded research scope

Review only:

1. The supplied homepage.
2. One useful canonical services, products, solutions, capabilities, or equivalent page.

Do not browse broadly. Do not use blogs, news, careers, social profiles, pricing, case studies, unrelated pages, search-result snippets, or third-party descriptions as substitutes for the prospect's own website.

## Homepage access procedure

1. Use the supplied website URL.
2. If the URL lacks a scheme, try HTTPS first and HTTP only as a bounded fallback.
3. Normalize the URL to the reachable homepage.
4. Record URL, HTTP/navigation status, page title, and whether meaningful readable content was obtained.
5. Meaningful content must contain more than a generic error page, empty shell, cookie wall, parked-domain page, or inaccessible JavaScript-only shell.

## Services/products/solutions procedure

From the reachable website root, try these path candidates in order:

1. `/services`
2. `/service`
3. `/solutions`
4. `/solution`

If those do not produce a useful page, inspect the homepage navigation for one clearly canonical link labelled Services, Products, Solutions, What We Do, Capabilities, or an equivalent label. Follow at most one such canonical page.

Stop after the first useful canonical page. Do not crawl additional pages merely to improve personalization.

## Evidence extraction

Capture source-backed evidence for:

- Service, product, or solution offered
- Problem addressed
- Core customer benefit or outcome
- Explicit customer types, industries, or use cases
- Homepage positioning language
- Services-page language, when available
- Important limitations, contradictions, or ambiguity

Every evidence item must include:

- `evidence_id`
- `source_url`
- `source_type`: `homepage`, `services_page`, `canonical_services_link`, or `homepage_inferred`
- `source_quote`: short verbatim supporting text
- `claim`: conservative interpretation of the quote
- `evidence_type`
- `confidence`: `high`, `medium`, or `low`

Do not copy large page sections. Store only the minimum quote needed to support the claim.

## Customer-type rule

If the website explicitly names customer types, record them as explicit evidence.

If it does not, understand the service or product and infer who it could reasonably help. Use a broad beneficiary when necessary. Label the source as `service_inference` or `broad_service_inference`. Do not invent a job title, decision-maker, company size, buying stage, urgency, budget, current demand, or current intent.

## Homepage fallback rule

If no services or solutions page is available, use homepage evidence to understand:

- What the business offers
- What problem it solves
- What benefits it promises
- Who could reasonably benefit

Mark the relevant claims as `homepage_inferred`. Do not claim that a services page was reviewed.

## Lead failure rule

If the homepage cannot provide meaningful content after bounded attempts, mark the lead:

- `processable: false`
- `research_status: failed`
- `failure_stage: 01-research`
- `failure_reason: homepage_unavailable_or_unusable`

Preserve the complete original row and place it in the failed-leads artifact. Do not stop other leads.

A failed services lookup alone is not a lead failure if the homepage is usable. Mark the research `partial` and continue with homepage evidence.

## Output contract

Return one structured research record per input row. The record must include:

- Agent and project identifiers
- Stable lead identity and original row position
- Original input reference
- Homepage page record
- Services research page record
- Evidence list
- Explicit customer types, if any
- Inferred beneficiary, if needed
- Research status
- Processable flag
- Limitations
- Failure information, only when applicable

No subject line, email body, P.S., strategy ID, CTA, or email wording may appear in this output.

## Stage acceptance checks

The stage passes only when:

- Original lead identity and order are preserved.
- Homepage status is recorded.
- Services lookup attempts and result are recorded.
- Each business claim has a source URL and quote.
- Explicit and inferred customer types are distinguished.
- Uncertainty and contradictions are recorded.
- Research scope was respected.
- No email copy or strategy was generated.

## Examples of valid evidence interpretation

- Explicit: the homepage says it serves manufacturers. Record manufacturers as an explicitly named customer type.
- Inferred: the homepage describes PC provisioning and imaging without naming buyers. Record a broad beneficiary such as organizations managing employee devices, marked as service inference.
- Uncertain: the homepage lists several unrelated services. Record the conflict and use the least specific honest description. Do not choose a favorite service silently.
