# 🔒 OWASP Juice Shop — Security Assessment & Write-ups

![Status](https://img.shields.io/badge/status-in%20progress-yellow)
![Target](https://img.shields.io/badge/target-OWASP%20Juice%20Shop-orange)
![Tools](https://img.shields.io/badge/tools-OWASP%20ZAP-blue)
![License](https://img.shields.io/badge/license-MIT-green)

A hands-on Application Security project: finding, verifying, and documenting vulnerabilities in [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/) — the intentionally vulnerable web app used to practice real AppSec workflows.

**Why this repo exists:** Juice Shop's vulnerabilities are well documented online, so the point here isn't discovering anything novel — it's demonstrating the actual job: independently finding an issue, verifying it, and writing it up clearly enough that a developer could act on it without re-doing your work.

---

## 👩‍💻 About me

Safa Sarfraz — Computer Engineering student, focused on penetration testing, cloud security, and AI/LLM security. [LinkedIn](https://www.linkedin.com/in/safa-sarfraz-1823b8333/) · [GitHub](https://github.com/vviperinae)

---

## 🧰 Methodology

Two separate tracks, kept clearly labeled since they demonstrate different skills:

| Track | What it is | Folder |
|---|---|---|
| **DAST (black-box)** | Found using OWASP ZAP — automated scanning + manual browsing through ZAP's proxy, with no source code access | [`/findings`](./findings) |
| **Code Review (source-assisted)** | Solved via Juice Shop's built-in coding challenges — reading actual source code to identify and fix the flawed line | [`/challenges-solved`](./challenges-solved) |

---

## 📋 Findings summary

| # | Finding | Severity | Type | OWASP Category | Write-up |
|---|---|---|---|---|---|
| 1 | Content Security Policy (CSP) Header Not Set | Low/Informational | DAST | A05: Security Misconfiguration | [link](./findings/01-csp-header-not-set.md) |
| 2 | Cross-Domain Misconfiguration | Medium | DAST | A05: Security Misconfiguration | [link](./findings/02-cross-domain-misconfiguration.md) |
| 3 | Timestamp Disclosure - Unix | Low/Informational | DAST | A01: Broken Access Control | [link](./findings/03-timestamp-disclosure.md) |
| 4 | Score Board — Hidden Admin Page Discovery | Medium | Code Review | A05: Security Misconfiguration | [link](./challenges-solved/score-board.md) |

*(More findings being added as testing continues — see [Issues](../../issues) for what's in progress.)*

---

## 🛠️ Tools used

- **OWASP ZAP** — automated + manual DAST scanning
- **Docker** — running the Juice Shop target locally
- **Firefox** (proxied through ZAP) — manual exploration

## 📚 What I learned

*(Fill this in as you go — this section is what recruiters actually read closely. Be honest: what surprised you, what took longer than expected, what you'd do differently next time.)*

---

## ⚠️ Disclaimer

This testing was performed exclusively against a locally-run instance of OWASP Juice Shop, an application explicitly designed and provided for security training. No production systems or third-party assets were tested.
