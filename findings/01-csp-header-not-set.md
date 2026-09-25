[← Back to summary](../README.md)

# Finding 1: Content Security Policy (CSP) Header Not Set

| Field | Detail |
|---|---|
| **Severity** | Low / Informational |
| **Type** | DAST (black-box, found via OWASP ZAP passive scan) |
| **OWASP Category** | A05:2021 - Security Misconfiguration |
| **CWE** | CWE-693: Protection Mechanism Failure |

## Description

The application does not set a `Content-Security-Policy` HTTP response header. CSP is a browser-enforced allowlist that restricts which sources scripts, styles, and other resources can be loaded from. Without it, the browser has no additional server-defined safety net against injected malicious scripts — meaning if an XSS vulnerability exists elsewhere in the app, its impact is not mitigated by this defense-in-depth layer.

## Steps to Reproduce

1. [Fill in: open ZAP, browse to localhost:3000, confirm alert in Alerts tab]
2. [Fill in: inspect a response header in ZAP's History/Response tab to show CSP is absent]

## Evidence

*(Insert screenshot of the ZAP alert detail + a response header view showing no `Content-Security-Policy` line)*

## Impact

On its own, this is not directly exploitable. Its impact is amplified only if paired with another vulnerability like stored/reflected XSS, where CSP would otherwise have blocked the malicious script from executing.

## Remediation

Configure the web/application server to send a `Content-Security-Policy` header, e.g.:
```
Content-Security-Policy: default-src 'self'; script-src 'self'
```
Start restrictive and loosen only as needed, testing thoroughly since overly strict policies can break legitimate app functionality.

## References
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CSP
- https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html
