<div align="center">

[ 🏠 Home ](#) ⋆ [ 🛡️ Findings ](#findings) ⋆ [ 🏆 Challenges ](#findings)

<br>

# ୨୧ OWASP Juice Shop Security Assessment ୨୧

![OWASP ZAP](https://img.shields.io/badge/OWASP_ZAP-00549A?style=for-the-badge&logo=owasp&logoColor=white&color=DDA0DD)
![Security](https://img.shields.io/badge/DAST_Assessment-FF3E00?style=for-the-badge&logo=shield&logoColor=white&color=FFB6C1)
![Documentation](https://img.shields.io/badge/Vulnerability_Reports-000000?style=for-the-badge&logo=markdown&logoColor=white&color=DDA0DD)

*A structured dynamic application security assessment and remediation report.* ₊˚.༄

</div>

<br>

## ⑅ ‧₊˚ ↬ *Objective* 
A comprehensive black-box Dynamic Application Security Testing (DAST) assessment of the OWASP Juice Shop web application. This project demonstrates practical vulnerability identification, verification, and developer-ready reporting aligned with industry standards.

<br>

## ⑅ ‧₊˚ ↬ *Assessment Scope*
ʚɞ **Target Application:** OWASP Juice Shop (a deliberately vulnerable modern web application).<br>
ʚɞ **Methodology:** Black-box DAST methodology focusing on the OWASP Top 10 vulnerability categories.<br>
ʚɞ **Primary Tool:** OWASP ZAP (Zed Attack Proxy) for active and passive vulnerability scanning.<br>
ʚɞ **Deliverables:** Structured markdown reports detailing reproduction steps, impact analysis, and remediation guidance.<br>

<br>

<a id="findings"></a>
## ⑅ ‧₊˚ ↬ *Documented Findings*
⋈ **Vulnerability 01:** [Content Security Policy (CSP) Header Not Set](findings/01-csp-header-not-set.md)<br>
⋈ **Vulnerability 02:** [Cross Domain Misconfiguration](findings/02-cross-domain-misconfiguration.md)<br>
⋈ **Vulnerability 03:** [Timestamp Disclosure](findings/03-timestamp-disclosure.md)<br>
⋈ **Exploitation:** [Score Board Access Control Bypass](challenges-solved/score-board.md)<br>
