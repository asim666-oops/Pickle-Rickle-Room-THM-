# Pickle-Rickle-Room-THM-
## Description
This repository contains my full walkthrough of the Pickle Rick CTF room from TryHackMe.
The challenge focuses on practical web exploitation, enumeration, OSINT-style clue hunting, command execution abuse, and privilege escalation via sudo misconfiguration.

The goal:
➡️ Find all three secret ingredients hidden in the system that Rick needs to transform back from a pickle!

## Overview of the Attack Path

# Nmap scan shows SSH & HTTP open.

## Inspecting the website reveals:
- Username hidden in HTML comments
- Downloadable image (checked for stego)

## Directory enumeration exposes:
-  /assets/
- /robots.txt
- /login.php (hidden login page)

## Login using:

- Username: R1ckRul3s
- Password from robots.txt: Wubbalubbadubdub
- Gain access to a restricted command execution portal.
- Read the first ingredient, move through the filesystem, discover second ingredient in /home/rick/.
- Privilege escalation via NOPASSWD sudo → gain root access.
- Retrieve third ingredient from /root/.

## Vulnerabilities Exploited
- Information Disclosure in HTML
- Username (R1ckRul3s) leaked in page source.
- Sensitive Info in robots.txt
-Password-like string Wubbalubbadubdub stored in robots.txt.
- Weak Authentication
-Simple <user/pass> login to admin portal.

## Command Execution Panel

A web terminal allows arbitrary command execution (with limited commands blocked).

- Sudo Misconfiguration
- User www-data may run the following commands:
- (ALL) NOPASSWD: ALL
-Full root access without password.
- Poor File Permissions
- World-readable files containing secret ingredients.

# Tools Used
## Enumeration

- Nmap – Service discovery
- Gobuster – Directory brute-forcing

## Image & Metadata Analysis

- Exiftool – Metadata extraction
- Binwalk – Hidden data scanning
- Steghide – Steganography extraction attempt

## Post-Exploitation

- Linux shell commands
- Sudo exploitation
- File system enumeration

# What I Learned

✔ How to enumerate web applications using browser + CLI tools
✔ How to analyze images for hidden content
✔ How to identify weak configurations like exposed usernames/passwords
✔ How to bypass blocked Linux commands by using alternatives (less, "file name with spaces")
✔ The importance of robots.txt in CTFs
✔ How dangerous sudo NOPASSWD misconfigurations are
✔ Practical privilege escalation to root
✔ A structured approach for CTF problem-solving

# Conclusion

## The Pickle Rick room is an excellent beginner–intermediate CTF that teaches core penetration testing skills:

- Enumeration is everything
- Always check page source, robots.txt, and directories
- Privilege escalation often depends on small misconfigurations
- Command restrictions can be bypassed creatively
- Thinking logically leads to all three ingredients

# Successfully retrieved all three ingredients:

- mr. meeseek hair
- 1 jerry tear
- fleeb juice

### Mission complete → Rick is no longer a pickle! 🥒🔥
