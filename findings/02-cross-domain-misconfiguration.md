<div align="left">
  <a href="./">↤ Back to Findings</a>
</div>
<br>

# ୨୧ Cross Domain Misconfiguration ୨୧

## ⑅ ‧₊˚ ↬ *Overview*
ʚɞ **Severity:** Medium<br>
ʚɞ **Endpoint:** API Endpoints<br>
ʚɞ **Category:** Security Misconfiguration
<br>

## ⑅ ‧₊˚ ↬ *Description & Exploitation*
The application implements an overly permissive Cross-Origin Resource Sharing (CORS) policy. To test this, we intercept an API request using OWASP ZAP and manually inject an arbitrary `Origin` header to see how the server responds.

We modify the intercepted `GET` request like so:

```http
GET /api/Users HTTP/1.1
Host: localhost:3000
Origin: [http://evil-attacker-site.com](http://evil-attacker-site.com)
```

Forwarding this to the server yields the following response:

```http
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Content-Type: application/json
```

By responding with the wildcard `*`, the server is explicitly telling the browser to allow any domain to read the responses from this API. This misconfiguration could allow an attacker to craft a malicious webpage that forces an authenticated user's browser to execute cross-domain requests and leak sensitive JSON data.
<br>

## ⑅ ‧₊˚ ↬ *Remediation*
Restrict the `Access-Control-Allow-Origin` header to explicit, trusted domains. Avoid using the wildcard `*` or dynamically reflecting the user provided `Origin` header in authenticated API routes.

```http
Access-Control-Allow-Origin: [https://trusted-frontend.com](https://trusted-frontend.com)
```
