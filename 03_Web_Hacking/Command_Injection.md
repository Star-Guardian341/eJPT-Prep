# Command Injection – TryHackMe

## Overview
This room focuses on identifying, exploiting, and mitigating command injection vulnerabilities in web applications. Command injection allows an attacker to execute arbitrary OS commands on a server, often leading to remote code execution (RCE). You’ll learn how to test for both verbose and blind injection and practice exploiting vulnerable systems.

## 🧩 Key Concepts Covered

### What is Command Injection?
- Abuse of application functionality to execute system commands.
- Impact includes reading sensitive files, executing system-level commands, and escalating privileges.
- Common in apps using user input within system calls (e.g., `system()`, `exec()` in PHP/Python).

### Application Behavior
- Apps often use input to build system commands (e.g., grep, ls).
- Unsanitized input can allow chaining commands via `;`, `&&`, `|`, etc.
- Command injection = Remote Code Execution under web app privileges.

### Types of Command Injection
- **Verbose**: Command output is displayed in the browser (e.g., whoami, ls).
- **Blind**: No output; success is measured via behavior (e.g., time delays with `sleep`, `ping`, or file creation).

### Detection Techniques
- Try payloads like:
  - `; whoami`
  - `&& ls`
  - `| sleep 5`
  - `; ping -c 5 127.0.0.1`
- Blind detection methods:
  - Use of time delay commands like `sleep`, `ping`
  - Redirecting output to files and reading them (`whoami > output.txt && cat output.txt`)

### Exploitation Examples
- **Linux Payloads**:
  - `whoami` – Shows running user
  - `ls` – List files
  - `sleep 5` – Blind testing
  - `nc` – Reverse shell

- **Windows Payloads**:
  - `whoami`
  - `dir`
  - `timeout 5` – Simulate delay for blind detection

### Prevention Techniques
- Avoid dangerous functions like `system()`, `exec()`, `passthru()` (PHP).
- Whitelist/validate input formats (e.g., digits only).
- Sanitize user input and use parameterized commands.
- Reject input containing metacharacters like `;`, `|`, `&`, `>`.

### Bypassing Filters
- Input filters can be bypassed using encoded characters or hex values.
- Example: Use `$IFS` or hex-encoded characters in Linux to evade simple string checks.

## 💻 Practical Lab Summary
- Tested verbose and blind injection payloads in a sandboxed web app.
- Found and exfiltrated contents of `/home/tryhackme/flag.txt` using techniques like `cat`, `;`, and file inclusion chaining.

## 💡 Takeaways
- Command injection is high-impact and often leads to full system compromise.
- Always test both for output and behavioral side effects.
- Input sanitization and minimal use of system-level commands is critical.
- Practice with various payloads and OS differences is essential.

## ✅ Status
Room completed.
