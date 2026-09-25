[← Back to summary](../README.md)

# Finding 3: Timestamp Disclosure — Unix

| Field | Detail |
|---|---|
| **Severity** | Low / Informational |
| **Type** | DAST (black-box, found via OWASP ZAP passive scan) |
| **OWASP Category** | A01:2021 - Broken Access Control (information exposure) |
| **CWE** | CWE-200: Exposure of Sensitive Information |

## Description

A Unix timestamp was identified in an application response. While a single timestamp is low-risk on its own, exposed timestamps can help an attacker infer server behavior, caching logic, or be chained with other information disclosures to build a fuller picture of the backend.

## Steps to Reproduce

1. [Fill in: which request/response ZAP flagged this in]
2. [Fill in: locate the raw timestamp value in the response body/header]

## Evidence

*(Insert screenshot of the flagged response with the timestamp highlighted)*

## Impact

Low in isolation. Contributes to attacker reconnaissance when combined with other disclosures (server errors, verbose headers, etc.).

## Remediation

Avoid exposing raw internal timestamps in user-facing responses where not functionally necessary; use relative or formatted dates instead where display is required.

## References
- https://cwe.mitre.org/data/definitions/200.html
