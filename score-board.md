[← Back to summary](../README.md)

# Score Board — Hidden Admin/Debug Page Discovery

| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Type** | Code Review (source-assisted — solved via Juice Shop's built-in coding challenge, not black-box) |
| **OWASP Category** | A05:2021 - Security Misconfiguration |
| **CWE** | CWE-538: Insertion of Sensitive Information into Externally-Accessible File or Directory |

## ⚠️ Methodology note

Unlike the findings in [`/findings`](../findings), this one was identified with **source code access** through Juice Shop's built-in "Find It / Fix It" coding challenge — not through black-box scanning. It's included here to show code-review skills separately from DAST work, and is labeled as such rather than presented as an independent discovery.

## Description

The application ships a `/score-board` route — a developer/QA debug page intended to track challenge completion — that is discoverable in the client-side Angular route configuration. In a real production app, an equivalent debug/admin route left in the routing table would be an unintentional exposure of internal tooling to any user who inspects the client bundle.

## Find It — the vulnerable line

In the Angular route configuration, the `score-board` route is defined identically to any other public-facing route, with no guard, authentication check, or environment flag restricting it to non-production builds:

```typescript
{
  path: 'score-board',
  component: ScoreBoardComponent
},
```

## Fix It — why the "correct" fix here is to leave it unchanged

This is a deliberately unusual case: Juice Shop's own guidance notes that in *this specific instance*, the route must remain as-is, since altering it would break the training app's own challenge-tracking functionality. This is called out explicitly to avoid the misleading appearance of "fixing" something that the target application actually needs to keep working.

## Impact (in a hypothetical real-world equivalent)

If a genuine internal/debug route were shipped this way in production, it would allow **any unauthenticated user** to discover and access functionality meant only for developers or QA — ranging from information disclosure to, in worse cases, administrative actions.

## Remediation (general principle, for a real app)

- Strip debug/admin routes from production builds entirely (environment-based build configuration), rather than relying on the route simply being "hard to find."
- If a debug route must exist in production, gate it behind proper authentication and role-based authorization — never rely on obscurity (an unlisted URL) as the only protection.

## References
- https://cwe.mitre.org/data/definitions/538.html
