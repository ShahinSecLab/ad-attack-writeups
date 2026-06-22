# File Permission Service

**Date:** June 2026
**Author:** ShahinSecLab
**Category:** Privilege Escalation
**Difficulty:** Easy
**Tools:** msfvenom, Metasploit, winPEAS, accesschk.exe

## Table of Contents

- [Introduction](#introduction)
- [Why This Attack Works](#why-this-attack-works)
- [Lab Setup](#lab-setup)
- [What I Needed Before Starting](#what-i-needed-before-starting)
- [What I Understood During the Process](#what-i-understood-during-the-process)
- [Attack Flow](#attack-flow)
- [Step 1 — Running winPEAS to Find the Vulnerable Service](#step-1--running-winpeas-to-find-the-vulnerable-service)
- [Step 2 — Checking the Service Configuration](#step-2--checking-the-service-configuration)
- [Step 3 — Checking Binary File Permissions with accesschkexe](#step-3--checking-binary-file-permissions-with-accesschkexe)
- [Step 4 — Backing Up the Original Service Binary](#step-4--backing-up-the-original-service-binary)
- [Step 5 — Uploading the Payload and Replacing the Service Binary](#step-5--uploading-the-payload-and-replacing-the-service-binary)
- [Step 6 — Getting a SYSTEM Shell and Dumping Hashes](#step-6--getting-a-system-shell-and-dumping-hashes)
- [How Defenders Can Catch This](#how-defenders-can-catch-this)
- [How to Prevent It](#how-to-prevent-it)
- [What I Achieved](#what-i-achieved)

## Introduction

File Permission Service is a local privilege escalation technique. The idea is simple — when a Windows service binary has weak file permissions, a low privilege user can replace the real binary with a malicious one. When the service starts, it runs the malicious binary as SYSTEM — giving full control of the machine without needing any exploit or CVE.

## Why This Attack Works

Windows services often run as SYSTEM. If the actual binary file that the service runs has weak permissions — meaning normal users can overwrite it — I can swap it out with my own payload. The next time the service starts, Windows runs my file thinking it is the real one, and I get a SYSTEM shell.

## Lab Setup
```
|   Component          |         Details          |
|----------------------|--------------------------|
| **Attacker Machine** | Kali Linux               |
| **Attacker IP**      | `192.168.5.128`          |
| **Victim Machine**   | Windows 10 (MSEDGEWIN10) |
| **Victim IP**        | `192.168.5.129`          |
| **Network**          | VMware Host-Only Network |
| **Domain**           | WORKGROUP                |
```

## Tools Prepared on Kali Before Starting

```
|        Tool      |          Location           |         Purpose                            |
|------------------|-----------------------------|--------------------------------------------|
| `winPEASany.exe` | `/home/kali/Desktop/tools/` | Find privilege escalation paths.           |
| `accesschk.exe`  | `/home/kali/Desktop/tools/` | Check file and service permissions.        |
| `rev.exe`        | `/home/kali/Desktop/`       | Malicious payload generated with `msfvenom`|
| `Metasploit`     | Built into Kali             | Catch reverse shells.                      |
```
