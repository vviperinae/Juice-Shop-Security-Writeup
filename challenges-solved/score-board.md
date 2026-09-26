<div align="center">
[ 🏠 Home ](../README.md)
</div>
<br>

# ୨୧ Score Board Access Control Bypass ୨୧

## ⑅ ‧₊˚ ↬ *Overview*
ʚɞ **Difficulty:** 1 Star<br>
ʚɞ **Category:** Broken Access Control<br>
ʚɞ **Target:** OWASP Juice Shop Score Board<br>

<br>

## ⑅ ‧₊˚ ↬ *Description*
The application relies on security through obscurity to hide its challenge Score Board. The endpoint is not protected by server-side access controls, meaning any user who discovers the URL path can access the page without prior authorization.

<br>

## ⑅ ‧₊˚ ↬ *Steps to Reproduce*
⋈ 1. Navigate to the Juice Shop application in a browser.<br>
⋈ 2. Open the browser Developer Tools and navigate to the Sources tab.<br>
⋈ 3. Inspect the `main.js` client-side script.<br>
⋈ 4. Search the code for terms like "score" or "board".<br>
⋈ 5. Identify the routing path `#/score-board`.<br>
⋈ 6. Append `/#/score-board` to the base URL and hit enter to successfully bypass the hidden navigation.<br>

<br>

## ⑅ ‧₊˚ ↬ *Remediation*
Do not rely on hiding UI elements as a security control. Implement strict server-side access controls to ensure that only authorized administrative users can access sensitive routes and endpoints.
