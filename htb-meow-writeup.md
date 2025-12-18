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
nmap -sV -A 10.129.37.146 <img width="1919" height="349" alt="Screenshot 2025-12-18 000529" src="https://github.com/user-attachments/assets/19bd6745-bb63-49a1-8ae8-b367bc587f06" />

<img width="1911" height="771" alt="Screenshot 2025-12-18 000604" src="https://github.com/user-attachments/assets/73ca00a1-095f-4683-9d56-4dc713b7824d" /> 
ping 10.129.37.146 <img width="1001" height="414" alt="image" src="https://github.com/user-attachments/assets/e8596b54-9466-42f3-91bd-809fddf85dab" />

Enumeration
I'd attempted common usernames such as admin, administrator, etc with no luck until noticing a potential hint in the nmap output or service banner (or telnet test).
Telnet to port 23 revealed a login prompt with "root" and a message hinting at the password.
<img width="1911" height="788" alt="Screenshot 2025-12-18 004022" src="https://github.com/user-attachments/assets/c7730698-3edd-462f-9510-932751ac0bd9" />

## Initial Access & Flags
I Connected via telnet to port 23 using the credentials from the login banner.
telnet 10.129.37.146
login: root
password:
Once inside, I was already root. Ran the `ls` command in the root directory and found `flag.txt`.

```bash
cat flag.txt
Captured the flag "b40abdfe23665f766f9c61ecba8a4c19" <img width="986" height="261" alt="image" src="https://github.com/user-attachments/assets/b0c97397-5ea2-4d9c-9091-d317dfdcb2cd" />
This revealed the root flag — completing the box.

Key Takeaways:

Banners and non-standard ports (like telnet 23) can leak critical information.
Direct root logins are a huge risk in real systems.
