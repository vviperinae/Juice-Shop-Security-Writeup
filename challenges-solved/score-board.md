<div align="left">
  <a href="./">↤ Back to Challenges</a>
</div>

# ୨୧ Score Board Access Control Bypass ୨୧
<br>

## ⑅ ‧₊˚ ↬ *Overview*
ʚɞ **Difficulty:** 1 Star<br>
ʚɞ **Category:** Broken Access Control<br>
ʚɞ **Target:** OWASP Juice Shop Score Board
<br>

## ⑅ ‧₊˚ ↬ *The Process*
The first goal in Juice Shop is usually finding the Score Board to track our progress, but there are no visible links to it in the UI. This suggests the developers might be relying on security through obscurity.

To find hidden routes, we can analyze the client-side JavaScript. Opening the browser's Developer Tools, we navigate to the `Sources` tab and search through the `main.js` bundle for keywords like `score` or `board`. 

We discover the routing configuration hardcoded in the frontend logic:

```javascript
  {
    path: '/score-board',
    component: ScoreBoardComponent
  },
```

Because the application only hides the button rather than enforcing actual server-side access controls, we can bypass the UI entirely. By appending the discovered route to our URL:

```text
http://localhost:3000/#/score-board
```

The application immediately routes us to the hidden component, solving the challenge and proving that hiding UI elements is not a valid access control mechanism.
<br>

## ⑅ ‧₊˚ ↬ *Remediation*
Sensitive endpoints and administrative views must be protected by strict server-side validation. The server must verify the user's session token and permissions before serving the requested component or its underlying API data, rather than just omitting the navigation link.
