# Server-Side Request Forgery (SSRF) – TryHackMe

## 💻 Overview
This room explores Server-Side Request Forgery (SSRF), a vulnerability that allows attackers to make requests from the vulnerable server to internal services or arbitrary locations. The room covers SSRF basics, types (regular vs blind), payload injection points, filter bypass techniques, and a hands-on lab challenge.

## 🧩 Key Concepts Covered

### What is SSRF?
- SSRF allows attackers to manipulate a server into sending HTTP requests to unintended destinations.
- **Two types:**
  - **Regular SSRF**: Response is visible to the attacker.
  - **Blind SSRF**: No response shown, attacker must monitor out-of-band services.

### Impact of SSRF
- Internal network scanning
- Access to internal admin endpoints or cloud metadata
- Disclosure of internal services and sensitive data

### Common Injection Points
- Full URL parameters (e.g., `url=http://...`)
- Hidden form fields
- Hostname-based parameters
- URL path segments

### SSRF Filter Bypass Techniques

#### Deny List Bypass
- Restricted values like `localhost`, `127.0.0.1`, or `169.254.169.254` may be blocked.
- Bypassed using equivalents or encodings: `0`, `127.1`, `0000`, `017700000001`, `2130706433`, `127.0.0.1.nip.io`

#### Allow List Bypass
- Allow lists may approve domains like `website.thm`
- Bypassed with subdomains like `website.thm.attacker.com`

#### Open Redirects
- Use internal redirects (e.g., `/redirect?url=https://evil.com`) to circumvent SSRF protections.

### Practical SSRF Lab (Acme IT Support)
- Found two endpoints:
  - `/private`: blocked from user IP
  - `/customers/new-account-page`: avatar selector feature
- Avatar selection uses server-side fetch of selected image
- Used directory traversal (`x/../private`) to bypass path-based deny rule and read `/private`
- Retrieved base64-encoded content of internal endpoint via avatar preview

## 🏁 Flags

- **SSRF Examples Site Flag**: Discovered through simulation (not shown here)
- **Acme Lab Flag**: Retrieved by decoding base64 content of `/private` via bypass

## 💡 Takeaways
- SSRF vulnerabilities are powerful due to server trust in internal resources.
- Many services (like AWS metadata at `169.254.169.254`) are exploitable via SSRF.
- Input validation (with strict allow lists) is crucial to prevention.
- Open redirects and clever encodings are common ways to escalate SSRF.

## ✅ Status
Room completed.

