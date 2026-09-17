# Integrity Regression Tests

The following failures must remain blocked:

1. lead-001 must never become 1.
2. Supplied first names must not become generic greetings.
3. The approved sender signature must not become "Best, Beans".
4. Null handoff hashes must fail validation.
5. Missing persisted prior-email text must fail validation.
6. A failed lead must appear in failed_leads.csv.
7. Other leads must continue processing.
8. Subject lines must remain identical across the three emails.
9. Email 2 and Email 3 must not contain a P.S.
10. Email 1 must contain a P.S.
11. Email 1 body must remain within the configured word limit.
12. No release is permitted when independent QA fails.
