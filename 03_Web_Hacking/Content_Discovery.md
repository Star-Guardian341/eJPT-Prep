# Content Discovery – TryHackMe

## Overview
This room focuses on discovering hidden or non-obvious web content that may be valuable to an attacker. Content discovery includes locating admin panels, backup files, development folders, outdated content, and misconfigured services. The techniques covered range from manual inspection and OSINT to automated fuzzing using tools like ffuf, dirb, and gobuster.

## 🧩 Key Concepts Covered

### Manual Discovery
- **robots.txt** – Can expose restricted paths not meant for users.
- **sitemap.xml** – May list forgotten or outdated URLs.
- **HTTP Headers** – Can reveal backend technologies like NGINX or PHP versions.
- **Favicons** – Can identify frameworks based on icon hash (MD5 lookup).
- **Framework Clues** – Page source comments, footer credits, and JS/CSS directories often hint at what stack is being used.

### OSINT Techniques
- **Google Dorking** – Leverages advanced Google search filters (e.g., `site:`, `inurl:`, `filetype:`) to locate sensitive pages.
- **Wayback Machine** – Reveals old or deleted pages that may still be active.
- **Wappalyzer** – Identifies a website's tech stack, plugins, and services.
- **GitHub & S3 Buckets** – Public repos or misconfigured cloud buckets may expose passwords, config files, or source code.

### Automated Discovery
- **Wordlists** – Commonly used filenames/directories sourced from SecLists.
- **Tools**:
  - `ffuf` – Fast and flexible fuzzing tool.
  - `dirb` – Simple directory brute-forcer.
  - `gobuster` – Powerful Go-based tool for directory and file brute-forcing.

## 💡 Takeaways
- Hidden content often reveals admin portals, misconfigured files, and backup data.
- Manual inspection (robots.txt, favicons, headers) can expose valuable targets early.
- Google Dorking and the Wayback Machine remain critical OSINT tools.
- Automated fuzzing with curated wordlists is essential for comprehensive enumeration.
- Combining manual, automated, and OSINT strategies leads to deeper visibility into a target.

## ✅ Status
Room completed.
