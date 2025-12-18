# HackTheBox - Meow Write-Up

**Author**: Keith Holmes  
**Date**: December 17, 2025  
**Difficulty**: Very Easy (Tier 0)  
**Skills Practiced**: Enumeration, Weak Credentials, Basic Linux Privilege Escalation  

## Overview
Meow is a beginner Linux machine focused on basic enumeration and exploiting weak/default credentials. The goal is to gain user access and escalate to root.

Target IP: 10.129.37.146

## Reconnaissance
Started with a full port scan:

```bash
nmap -sV -A 10.129.37.146 ![Nmap Scan Results](https://raw.githubusercontent.com/keefosec/cyber-writeups/main/nmap.png) 
 
ping 10.129.37.146 ![Ping Scan](https://raw.githubusercontent.com/keefosec/cyber-writeups/main/ping%20scan.png)

Enumeration
I'd attempted common usernames such as admin, administrator, etc with no luck until noticing a potential hint in the nmap output or service banner (or telnet test).
Telnet to port 23 revealed a login prompt with "root" and a message hinting at the password.
![Telnet Login](https://raw.githubusercontent.com/keefosec/cyber-writeups/main/telnet-login.png)

## Initial Access & Flags
I Connected via telnet to port 23 using the credentials from the login banner.
telnet 10.129.37.146
login: root
password:
Once inside, I was already root. Ran the `ls` command in the root directory and found `flag.txt`.

```bash
cat flag.txt
Captured the flag "b40abdfe23665f766f9c61ecba8a4c19" ![Flag Output](https://raw.githubusercontent.com/keefosec/cyber-writeups/main/flag-meow.png)
This revealed the root flag — completing the box.

Key Takeaways:

Banners and non-standard ports (like telnet 23) can leak critical information.
Direct root logins are a huge risk in real systems.
