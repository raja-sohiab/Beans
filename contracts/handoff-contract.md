# Exact Handoff Contract

Contract ID: BEANS-HANDOFF-001

Email 2 must consume the exact persisted Email 1 output.

Email 3 must consume the exact persisted Email 1 and Email 2 outputs.

The runtime, not the model, computes SHA-256 over canonical persisted bytes.

Each handoff record must contain:

- run_id
- lead_id
- stage
- predecessor_stage
- exact persisted rendered text
- subject
- predecessor_sha256
- current_sha256
- serialization_version
- artifact_reference
- persistence_acknowledgement
- status

A downstream stage may run only when:

1. The predecessor record exists.
2. The predecessor status is complete.
3. The predecessor lead_id and run_id match.
4. The exact persisted text is readable.
5. The stored hash is present.
6. An independent recomputation matches the stored hash.
7. The handoff references the correct predecessor stage.

Null hashes, missing text, reconstructed text, conversational summaries, and model-reported hashes are invalid and must block the downstream stage.

The sender signature is governed separately by `sender-contract.md`.
