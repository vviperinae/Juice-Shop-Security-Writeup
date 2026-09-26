

<div align="center">

[← Back to summary](../README.md)

</div>
<br>

# ୨୧ Timestamp Disclosure ୨୧

## ⑅ ‧₊˚ ↬ *Overview*
ʚɞ **Severity:** Low<br>
ʚɞ **Endpoint:** Various API Responses<br>
ʚɞ **Vulnerability Category:** Information Exposure<br>

<br>

## ⑅ ‧₊˚ ↬ *Description*
The application discloses internal system timestamps within its HTTP responses. While not a direct vulnerability, this information can assist an attacker in fingerprinting the backend system, mapping server uptime, or synchronizing time-based attacks against cryptographic tokens.

<br>

## ⑅ ‧₊˚ ↬ *Steps to Reproduce*
⋈ 1. Browse the application while proxying traffic through OWASP ZAP.<br>
⋈ 2. Run a passive scan on the captured traffic.<br>
⋈ 3. Review the ZAP alerts for "Timestamp Disclosure".<br>
⋈ 4. Observe that raw Unix timestamps are exposed in plain text within the JSON response bodies.<br>

<br>

## ⑅ ‧₊˚ ↬ *Remediation*
Strip internal timestamps from API responses unless they are strictly required for front-end functionality. If time data is necessary, format it in a standard, generalized way.
