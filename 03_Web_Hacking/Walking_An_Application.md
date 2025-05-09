# Walking An Application – TryHackMe

## Overview
This room introduces manual web application analysis using only browser-native developer tools. Rather than relying on automated scanners, it focuses on inspecting a site’s structure, behavior, and client-side logic manually to identify potentially sensitive content, misconfigurations, or exploitable features.

## 🧩 Key Concepts Covered

### Browser-Based Reconnaissance
- **View Source** – Identifying developer comments, exposed URLs, and hidden links.
- **Inspector** – Modifying page elements, bypassing visual blocks like paywalls.
- **Debugger (Sources)** – Pausing JavaScript execution, analyzing obfuscated/minified scripts.
- **Network Tab** – Monitoring real-time HTTP requests, AJAX behavior, and background data submission.

### Site Feature Mapping
- Learned to manually walk through a web application to document interactive features and endpoints:
  - Login/signup forms
  - News articles with access restrictions
  - Ticket submission systems
  - Hidden admin or staff areas

### Practical Vulnerability Indicators
- Developer comments exposing sensitive roadmap info
- Accessible directory listings due to misconfigurations
- Client-side paywall elements removable with CSS manipulation
- Obfuscated JavaScript controlling UI behavior
- AJAX requests leaking sensitive data through unprotected endpoints

## 💡 Takeaways
- Manual inspection often reveals what scanners miss—like hidden links, out-of-date frameworks, and configuration errors.
- The browser dev tools are essential for web pentesters: they simulate the user perspective while giving deep technical insight.
- Understanding client-side logic (JavaScript) can uncover hidden features and exposed functionality.
- Many web vulnerabilities are due to oversights in frontend handling, not backend alone.

## ✅ Status
Room completed.
