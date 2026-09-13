# Risk Scoring Model

## Objective
Translate detection findings and enrichment results into a single
prioritization score, so an analyst working a queue of alerts knows which
ones to look at first. This is deliberately a simple additive point model,
not a statistical or machine-learning approach. The goal is a score an
analyst can fully explain in one sentence per case, not a black box.

## Model

```text
Reply-To domain mismatch                    +20
Urgency language present                    +20
Suspicious/unverifiable URL                 +15
Financial/payment change request in body    +25
Two independent detections agreeing         +10
```

**Severity bands:**
```text
0-29    Low
30-59   Medium
60-89   High
90+     Critical
```

Each signal maps directly to something already built in this project:
the first two come straight from Detection 1 and Detection 2 firing, the
URL signal comes from the enrichment step (an embedded link that no
reputation tool could verify one way or the other), the financial-request
signal comes from reading the email body during the Validate stage, and
the "two detections agreeing" bonus rewards corroboration, the same logic
an analyst uses when multiple unrelated alerts point at the same event.

## Applied to all 4 cases

| Signal | CASE-01 | CASE-02 | CASE-03 | CASE-04 |
|---|---|---|---|---|
| Reply-To mismatch | +20 | +20 | +20 | +20 |
| Urgency language | 0 | 0 | 0 | +20 |
| Unverifiable URL | +15 | +15 | +15 | +15 |
| Financial/payment request | 0 | 0 | +25 | +25 |
| Two detections agreeing | 0 | 0 | 0 | +10 |
| **Total** | **35** | **35** | **60** | **90** |
| **Model's band** | Medium | Medium | High | Critical |
| **Dataset's own label** | High | High | High | Critical |

## Comparison to the dataset's own labels

CASE-03 and CASE-04 line up cleanly with the pre-labeled severities in
`manifest.csv`. CASE-01 and CASE-02 don't: the model scores them Medium,
the dataset calls them High.

The reason is structural, not a scoring mistake. CASE-01 (Okta MFA reset)
and CASE-02 (SharePoint document review) are credential-harvesting
attempts, not financial fraud, so neither ever earns the "financial
request" or "two detections agreeing" points, the two highest-value
signals in this model. As built, the model is implicitly tuned toward
*financial* BEC-style harm and under-weights *credential theft*, even
though a stolen credential can lead to consequences well beyond one
fraudulent payment (lateral movement, mailbox takeover, further phishing
sent from a trusted internal account).

## What I'd Improve Next

The obvious next signal is something like **"Authentication check failure
(SPF/DKIM/DMARC): +15,"** since every case in this dataset fails at least
one of those checks, and it would raise CASE-01 and CASE-02 toward
agreement with their labeled severity.

It's worth noting this isn't a free fix, though. CASE-04, the one case we
most want to keep ranked highest, is the *only* case where DMARC actually
passes. Adding an auth-failure signal naively would narrow the gap between
CASE-04 and the others rather than sharpen it. Before adding it, I'd want
to weight it lower than the other signals, or split it into per-mechanism
signals (SPF fail, DKIM fail, DMARC fail counted separately) so a full
triple-failure counts for more than a single soft-fail. Documenting this
tension honestly, rather than quietly tweaking numbers until the model
agrees with the answer key, is the more useful exercise.

## Why not a more advanced approach
No machine learning or statistical scoring here on purpose. A hand-built,
fully explainable point model matches this project's goal: something I can
walk a hiring manager through line by line, not a model I'd have to defend
as a black box. The trade-off, less nuance, imperfect agreement with the
dataset's own labels on 2 of 4 cases, is the honest cost of that choice,
not a hidden flaw.
