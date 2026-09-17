# Beans for PersistIQ

Beans is a PersistIQ-only lead research, email customization, validation, and release system.

This repository is the declarative source of truth for the system. It contains policy, stage contracts, schemas, QA rules, and test specifications. It does not contain live campaign files, secrets, or deterministic email-generation code.

## Pipeline

```text
Input CSV
→ 01 research homepage and services/solutions
→ 02 business understanding and commercial translation
→ 03 Email 1 strategy selection
→ 04 Email 1 generation
→ 05 Email 2 using exact Email 1
→ 06 Email 3 using exact Email 1 + Email 2
→ 07 per-lead validation
→ 08 output assembly
→ 09 independent final-artifact QA
→ 10 release or reject
```

## Hard boundaries

- PersistIQ only.
- ICP qualification is upstream.
- Research is bounded to the homepage and services/products/solutions lookup defined in Stage 1.
- The model writes all email prose. Infrastructure may not generate, rewrite, rotate, or fill email copy.
- Email 2 and Email 3 receive exact prior rendered email text.
- Failed leads never stop good leads.
- A failed lead is never silently dropped.
- Release is based on the actual final CSV, not agent claims or manifests alone.

## Runtime requirement

The JackHamr runtime must prove the configured model invocation, structured stage handoff, artifact persistence, and independent QA access before production use. If any of those capabilities cannot be demonstrated, the run is `NOT_RELEASED`.

