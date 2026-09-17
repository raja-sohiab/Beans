# Retry and Resume Contract

Retries are bounded and stage-specific.

Rules:

1. Every retry creates a new invocation_id.
2. A retry must use the approved model path.
3. A completed stage is not regenerated during resume.
4. Resume must verify run_id, input hash, knowledge-bundle commit, stage version, and output hash.
5. Failed leads continue independently.
6. No deterministic fallback writer is permitted.
7. No retry may overwrite prior evidence; each attempt remains auditable.
8. Retry exhaustion routes the lead to failed_leads.csv or review output.
