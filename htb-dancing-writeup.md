# HackTheBox - Dancing Write-Up

**Author**: Keith Holmes  
**Date**: December 31, 2025  
**Difficulty**: Very Easy (Tier 0)  
**Skills Practiced**: Port Scanning, SMB Enumeration, Share Access  

## Overview
Dancing is a Windows machine focused on exploiting misconfigured SMB shares to gain access and retrieve the flag.

Target IP: 10.129.21.151

## Reconnaissance
Started with a full port scan:

```bash
nmap -sV -A 10.129.21.151: ![Nmap Scan Results](https://github.com/keefosec/cyber-writeups/blob/d65fad33c2c202633bb12f04cc28ef97dcd7d86a/nmap-scandancing.png)
(https://github.com/keefosec/cyber-writeups/blob/d65fad33c2c202633bb12f04cc28ef97dcd7d86a/nmap2-dancing.png)
Key finding: Port 445 open with SMB service.

Enumeration
Listed available SMB shares anonymously: ![SMB Shares](https://github.com/keefosec/cyber-writeups/blob/d65fad33c2c202633bb12f04cc28ef97dcd7d86a/smbclient-list.png)
smbclient -L //10.129.21.151

Discovered the WorkShares share was accessible without credentials.
SMB Shares Listed: 

Initial Access
Connected to the open share: ![SMB Shares](https://github.com/keefosec/cyber-writeups/blob/d65fad33c2c202633bb12f04cc28ef97dcd7d86a/anonymous-login.png)
smbclient //10.129.21.151/WorkShares

Flags

Navigated directories and located the flag file. ![Directory Listing](https://github.com/keefosec/cyber-writeups/blob/d65fad33c2c202633bb12f04cc28ef97dcd7d86a/smb-share-ls.png)
ls
get flag.txt
Directory Listing with Flag
Exited and viewed locally:
cat flag.txt
Downloaded and viewed the flag locally: ![Flag Output](https://github.com/keefosec/cyber-writeups/blob/d65fad33c2c202633bb12f04cc28ef97dcd7d86a/cat-flag-dancing.png)
cat flag.txt

Key Takeaways

SMB shares with anonymous access are a common misconfig in Windows environments.
Always enumerate open ports thoroughly — SMB can leak sensitive data.
Proper share permissions are critical for security.

References

HackTheBox Starting Point
smbclient documentation

Thanks for reading write-up #3!
