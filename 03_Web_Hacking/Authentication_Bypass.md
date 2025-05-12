# Authentication Bypasses – TryHackMe

## Overview
This room focuses on exploiting weaknesses in authentication mechanisms to gain unauthorized access or escalate privileges. Topics include username enumeration, password brute forcing, logic flaws in password reset flows, and manipulating session cookies to gain admin access.

## 🧩 Key Concepts Covered

### Username Enumeration via ffuf
- Used the `/signup` form to identify already-registered usernames by matching the error message `"username already exists"`.
- Tool: `ffuf`
- Wordlist: `SecLists/Usernames/Names/names.txt`
- Output saved to `valid_usernames.txt` for brute-force login attempts.

### Brute-Force Login (Username + Password)
- Used valid usernames and a list of common passwords to attempt logins via POST requests to `/login`.
- Identified a valid credential pair by filtering out HTTP 200 responses.
- Tool: `ffuf`
- Wordlists: `valid_usernames.txt` and `10-million-password-list-top-100.txt`

### Password Reset Logic Flaw
- Application used PHP’s `$_REQUEST`, combining GET and POST data.
- Exploited this to override the email destination of a password reset.
- Crafted a request where the GET parameter targeted the victim, but the POST `email` value sent the reset link to the attacker.

### Cookie-Based Privilege Escalation
- Inspected cookies like `logged_in=true; admin=false` and modified them to gain admin access.
- Example:
  - Changing `admin=false` to `admin=true` resulted in elevated privileges.
- Also demonstrated Base64-decoded session cookies, where values like `{"id":1,"admin":false}` could be manipulated and re-encoded to `{"id":1,"admin":true}`.

## 💡 Takeaways
- Authentication logic flaws can lead to full account compromise, even without knowing the password.
- Brute-force attacks become significantly more effective when username enumeration is possible.
- Using `$_REQUEST` in PHP introduces dangerous behavior if not carefully scoped.
- Plaintext or poorly encoded cookies can reveal and grant unauthorized access to sensitive functions.

## ✅ Status
Room completed.
