# Artifact Contract

Every run must persist these artifacts:

- input.csv
- customized_leads.csv
- failed_leads.csv
- run_manifest.json
- qa_report.json

Rules:

1. The exact input CSV is persisted before processing.
2. Every input row appears exactly once in customized_leads.csv or failed_leads.csv.
3. The two output files are disjoint by lead_id.
4. Original input fields and values are preserved.
5. The manifest is calculated from re-read artifacts.
6. Independent QA reads the actual files.
7. Missing, unreadable, or mismatched artifacts block release.
