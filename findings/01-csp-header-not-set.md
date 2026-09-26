<div align="center">

[ 🏠 Home ](../README.md) ⋆ [ 🛡️ Findings ](README.md) ⋆ [ 🏆 Challenges ](../challenges-solved/README.md)

</div>
<br>

# ୨୧ Content Security Policy (CSP) Header Not Set ୨୧

## ⑅ ‧₊˚ ↬ *Overview*
ʚɞ **Severity:** Medium<br>
ʚɞ **Endpoint:** Global / Multiple Endpoints<br>
ʚɞ **Category:** Security Misconfiguration

<br>

## ⑅ ‧₊˚ ↬ *Description & Exploitation*
During the initial reconnaissance of the OWASP Juice Shop, we need to inspect the HTTP headers returned by the server to evaluate its baseline security posture. 

By proxying the traffic through OWASP ZAP and intercepting a standard `GET` request to the application's root endpoint, we capture the server's response:

```http
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: text/html; charset=utf-8
Content-Length: 1045
```

Looking at the returned headers, we can clearly see that the `Content-Security-Policy` (CSP) header is completely missing. 

Without a strict CSP, the browser has no instructions on which dynamic resources are safe to load. If we manage to find an injection point later in the assessment, the lack of this header guarantees that the browser will blindly execute our malicious scripts, leaving the application highly vulnerable to Cross-Site Scripting (XSS).

<br>

## ⑅ ‧₊˚ ↬ *Remediation*
To secure the application against unauthorized script execution, the backend server must be configured to return a strict CSP header on all HTTP responses. 

```http
Content-Security-Policy: default-src 'self'; script-src 'self' [https://trusted-cdn.com](https://trusted-cdn.com);
```
This configuration restricts the browser to only load scripts from the application's own origin (`'self'`) or explicitly whitelisted domains.
