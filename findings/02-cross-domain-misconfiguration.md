
<div align="center">

[← Back to summary](../README.md)

</div>
<br>

# ୨୧ Cross Domain Misconfiguration ୨୧

## ⑅ ‧₊˚ ↬ *Overview*
ʚɞ **Severity:** Medium<br>
ʚɞ **Endpoint:** API Endpoints<br>
ʚɞ **Vulnerability Category:** Security Misconfiguration<br>

<br>

## ⑅ ‧₊˚ ↬ *Description*
The application implements an overly permissive Cross-Origin Resource Sharing (CORS) policy. By allowing arbitrary origins to access application resources, attackers could potentially craft malicious pages that force authenticated users to execute unintended actions or leak sensitive data across domains.

<br>

## ⑅ ‧₊˚ ↬ *Steps to Reproduce*
⋈ 1. Intercept an API request using OWASP ZAP.<br>
⋈ 2. Modify the request by adding an arbitrary `Origin` header.<br>
⋈ 3. Forward the request to the server.<br>
⋈ 4. Observe that the server responds with `Access-Control-Allow-Origin: *` or reflects the malicious origin.<br>

<br>

## ⑅ ‧₊˚ ↬ *Remediation*
Restrict the `Access-Control-Allow-Origin` header to explicit, trusted domains. Avoid using the wildcard or dynamically reflecting the user provided `Origin` header in authenticated API routes.
