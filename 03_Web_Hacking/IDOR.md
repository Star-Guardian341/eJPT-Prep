
# IDOR – TryHackMe

## Overview
This room focuses on identifying and exploiting **Insecure Direct Object Reference (IDOR)** vulnerabilities. These flaws occur when an application exposes internal objects (like user records, files, or tickets) via parameters (e.g., `user_id=123`) without proper authorization checks, allowing attackers to access unauthorized data.

## 🧩 Key Concepts Covered

### Basic IDOR Vulnerability
- Occurs when object references (like `?user_id=1305`) are exposed and trusted without server-side validation.
- By manually modifying the value (e.g., `user_id=1000`), users can access others’ data if no access control is enforced.

### Encoded IDs
- Web apps may Base64-encode object IDs (e.g., `MTIz` for `123`), but the underlying logic remains the same.
- Attackers can decode, tamper with, and re-encode these values to test for IDOR.
- Tools: [base64decode.org](https://www.base64decode.org), [base64encode.org](https://www.base64encode.org)

### Hashed IDs
- IDs may be hashed using MD5 or SHA1 (e.g., `123` → `202cb962ac59075b964b07152d234b70`)
- Online hash lookup tools like [CrackStation](https://crackstation.net) can reverse weak hashes.

### Unpredictable IDs & Manual Comparison
- When IDs aren't obvious, creating two accounts and comparing their data structures (e.g., `user_id` values) can reveal if IDOR is possible.
- Swapping known IDs between sessions is a common detection tactic.

### Hidden or Dynamic Endpoints
- Not all IDOR vulnerabilities are visible in the address bar.
- Some are discovered via:
  - **AJAX calls**
  - **Network tab in DevTools**
  - **Unreferenced query parameters (parameter mining)**

### Practical IDOR Exploitation
- The provided web app used an endpoint:

- After logging in and observing DevTools → Network tab, the endpoint was found returning user account data in JSON format.
- Changing `id=2` or `id=3` while logged in allowed access to other users' data — confirming an IDOR vulnerability.

## 💡 Takeaways
- IDOR vulnerabilities are often simple but critical, especially in user data or account control.
- Parameter manipulation is a key skill in testing web app authorization logic.
- Even Base64 or hashed IDs are not secure unless paired with access control.
- Always check AJAX requests and background APIs, not just URLs.

## ✅ Status
Room completed.
