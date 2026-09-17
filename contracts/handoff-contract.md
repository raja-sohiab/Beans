# Sender Signature Contract

The sender signature is a runtime configuration value, not model-generated content.

Rules:

1. The runtime supplies the approved sender signature.
2. Email stages may place it in the signature field.
3. The model may not invent, replace, or alter it.
4. Validation compares the rendered signature with the approved value.
5. Missing or mismatched signatures are blocking failures.
