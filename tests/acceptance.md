# Acceptance Tests

## Runtime

- The configured GPT-5.6 Luna invocation is proven with a synthetic item.
- Stage output is persisted and passed structurally to the next stage.
- Exact Email 1 reaches Stage 5.
- Exact Email 1 and Email 2 reach Stage 6.
- The actual final CSV is readable by independent QA.

## Failure regressions

- No Python/template email generation.
- No row-index or phrase rotation.
- No fallback writer.
- No hand-authored fixture used as an end-to-end substitute.
- No missing model provenance.
- No missing evidence accepted.
- No handoff mismatch accepted.
- No manifest/CSV mismatch accepted.
- No em dash accepted.
- No P.S. in Email 2 or Email 3.
- No final release when independent QA fails.

## Scale

Run the same production path at 1, 5, 25, 100, and 1,000+ leads. Verify partition completeness, idempotent retries, resume behavior, ordering, and artifact integrity at every size.

