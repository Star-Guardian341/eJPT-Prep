# Subdomain Enumeration – TryHackMe

## Overview
This room focuses on expanding the attack surface of a target by discovering subdomains. Subdomains often host development sites, admin panels, or legacy services that may be less secure than the main domain. The room covers multiple enumeration techniques including brute force, OSINT, certificate transparency logs, and virtual host discovery.

## 🧩 Key Concepts Covered

### Certificate Transparency (CT) Logs
- SSL/TLS certificates are publicly logged when issued.
- Tools like `crt.sh` allow passive discovery of current and historical subdomains.

### Search Engine OSINT (Google Dorking)
- Search filters such as `site:*.domain.com -site:www.domain.com` reveal subdomains indexed by search engines.
- Useful for discovering public but forgotten subdomains.

### DNS Brute Force
- Tools like `dnsrecon` and `ffuf` use wordlists to brute force DNS records and discover hidden subdomains.
- Requires many DNS queries and is often automated for efficiency.

### Sublist3r (Automated OSINT)
- Aggregates subdomain results from various public sources.
- Faster than manual enumeration and combines multiple data sources.

### Virtual Host Enumeration
- Identifies subdomains not visible via DNS by manipulating the `Host` HTTP header.
- Used in shared hosting or internal dev environments.
- Tools like `ffuf` can fuzz host headers and filter responses using the `-fs` (filter size) option.

## 💡 Takeaways
- Subdomains can expose shadow infrastructure that is more vulnerable than the main application.
- Combining OSINT, brute force, and host-header manipulation gives comprehensive coverage.
- CT logs and Google search indexing are powerful passive recon methods.
- Tools like `ffuf` are versatile for both DNS and virtual host enumeration tasks.

## ✅ Status
Room completed.
