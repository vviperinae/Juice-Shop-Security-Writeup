[← Back to summary](../README.md)

# Finding 2: Cross-Domain Misconfiguration

| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Type** | DAST (black-box, found via OWASP ZAP passive scan) |
| **OWASP Category** | A05:2021 - Security Misconfiguration |
| **CWE** | CWE-942: Overly Permissive Cross-domain Whitelist |

## Description

The application's Cross-Origin Resource Sharing (CORS) configuration appears overly permissive, potentially allowing other domains to make authenticated requests to this application on a victim's behalf.

## Steps to Reproduce

1. [Fill in: which endpoint(s) ZAP flagged]
2. [Fill in: check the `Access-Control-Allow-Origin` response header value — is it `*` or does it reflect any requesting origin?]

## Evidence

*(Insert screenshot showing the relevant response header)*

## Impact

If the CORS policy allows arbitrary origins to read authenticated responses (especially combined with `Access-Control-Allow-Credentials: true`), a malicious website could make requests to this app using a logged-in victim's session and read the response — a form of cross-site data theft.

## Remediation

Restrict `Access-Control-Allow-Origin` to a specific, trusted allowlist of domains rather than a wildcard, and avoid combining wildcard origins with credentialed requests.

## References
- https://cheatsheetseries.owasp.org/cheatsheets/CORS_Requirements_Cheat_Sheet.html
