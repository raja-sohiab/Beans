# Immutable Lead Identity Contract

Every input row receives a stable lead_id before any stage runs.

Required fields:

- run_id
- lead_id
- input_row_position
- original_input

Rules:

1. lead_id is assigned once by the runtime.
2. Every stage must copy lead_id exactly.
3. Stages may not regenerate, normalize, shorten, or replace lead_id.
4. input_row_position is immutable.
5. Duplicate, missing, or changed IDs are blocking failures.
6. The model must never invent or assign lead IDs.
