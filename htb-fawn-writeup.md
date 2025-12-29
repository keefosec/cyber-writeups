# HackTheBox - Fawn Write-Up

**Author**: Keith Holmes  
**Date**: December 29, 2025  
**Difficulty**: Very Easy (Tier 0)  
**Skills Practiced**: Port Scanning, FTP Enumeration, Anonymous Access  

## Overview
Fawn is a Linux machine focused on exploiting a common misconfigured service to gain initial access and retrieve the flag.

## Reconnaissance
Started with a full port scan:

```bash
nmap -sV -A 10.129.20.63 ![Nmap Scan Results](https://github.com/keefosec/cyber-writeups/blob/feeba93b92240b5a72407385460d924e29a5aba2/nmap-fawn.png)

Key finding: FTP on port 21 with anonymous login enabled. 

## Enumeration & Access
Connected to FTP on port 21:

```bash
ftp 10.129.20.63
Tried common usernames like root (failed), then used anonymous with blank password:
Name: anonymous
Password: [Enter]
Login successful. ![FTP Login](https://github.com/keefosec/cyber-writeups/blob/feeba93b92240b5a72407385460d924e29a5aba2/ftp-login.png)

Logged in anonymously and listed directories/files. ![Directory Listing](https://github.com/keefosec/cyber-writeups/blob/feeba93b92240b5a72407385460d924e29a5aba2/ls-flag.png)

Navigated to find the flag. ![Flag Output](https://github.com/keefosec/cyber-writeups/blob/feeba93b92240b5a72407385460d924e29a5aba2/cat-flag.png)
