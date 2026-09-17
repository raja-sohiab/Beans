# Research Scope

For each lead, review:

1. The supplied homepage.
2. A bounded services/products/solutions lookup.

## Services lookup order

From the website root, try `/services`, `/service`, `/solutions`, and `/solution`, in that order. Also follow a clearly canonical homepage link labelled Services, Products, Solutions, What We Do, Capabilities, or equivalent. Stop after the first useful canonical page.

Do not browse blogs, news, careers, social profiles, pricing, case studies, or unrelated pages.

## Homepage fallback

If no services/solutions page is available, use homepage content to identify the core service/product, problem addressed, benefits, and likely beneficiaries. Mark the source as `homepage_inferred`.

## Failure

If the homepage cannot provide meaningful content after bounded URL attempts, mark the lead unprocessable and emit it in the failed-leads CSV. This must not stop other leads.

