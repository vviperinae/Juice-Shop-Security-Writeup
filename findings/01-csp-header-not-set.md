

<div align="center">
  
[← Back to summary](../README.md)

</div>
<br>

# ୨୧ Content Security Policy (CSP) Header Not Set ୨୧

## ⑅ ‧₊˚ ↬ *Overview*
ʚɞ **Severity:** Medium<br>
ʚɞ **Endpoint:** Global / Multiple Endpoints<br>
ʚɞ **Vulnerability Category:** Security Misconfiguration<br>

<br>

## ⑅ ‧₊˚ ↬ *Description*
The web application does not set the `Content-Security-Policy` HTTP response header. Without a strict CSP, the application is at a higher risk of Cross-Site Scripting (XSS) and data injection attacks, as the browser cannot restrict the sources from which executable scripts and content can be loaded.

<br>

## ⑅ ‧₊˚ ↬ *Steps to Reproduce*
⋈ 1. Open OWASP ZAP and proxy the browser traffic.<br>
⋈ 2. Navigate to the main application endpoint.<br>
⋈ 3. Inspect the HTTP Response headers in the ZAP history.<br>
⋈ 4. Observe that the `Content-Security-Policy` header is entirely absent from the server response.<br>

<br>

## ⑅ ‧₊˚ ↬ *Remediation*
Implement a strict Content Security Policy by adding the `Content-Security-Policy` header to all server responses. Ensure the policy explicitly defines trusted sources for scripts, styles, and other resources.
