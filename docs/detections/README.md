# Detection Engineering Docs

One write-up per detection: objective, logic, SPL, test data, expected
result, false-positive considerations. Also home to the project's risk
scoring model, since it's used across detections rather than tied to one.

- [`detection-1-reply-to-mismatch.md`](./detection-1-reply-to-mismatch.md),
  Reply-To Domain Mismatch. Complete, alert confirmed firing.
- [`detection-2-urgency-language.md`](./detection-2-urgency-language.md),
  External Sender + Urgency Language. Complete, alert confirmed firing.
- [`risk-scoring-model.md`](./risk-scoring-model.md), the CVSS-aligned
  (0.0-10.0) point model used to score investigated cases.

Screenshots referenced by these docs live in `screenshots/`.
