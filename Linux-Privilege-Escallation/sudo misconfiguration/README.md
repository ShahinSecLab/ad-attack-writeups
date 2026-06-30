# Sudo Misconfiguration

**Sudo **Misconfiguration <br>
**Date:** June 2026 <br>
**Author:** ShahinSecLab <br>
**Category:** Privilege Escalation <br>
**Difficulty:** Easy <br>
**Tools:** SSH, sudo, find, GTFOBins 


## Table of Contents

- [Introduction](#introduction)
- [Why This Attack Works](#why-this-attack-works)
- [Lab Setup](#lab-setup)
- [What I Needed Before Starting](#what-i-needed-before-starting)
- [What I Understood During the Process](#what-i-understood-during-the-process)
- [Attack Flow](#attack-flow)
- [Step 1 — Connecting to the Target and Checking Sudo Permissions](#step-1--connecting-to-the-target-and-checking-sudo-permissions)
- [Step 2 — Picking a Binary and Checking GTFOBins](#step-2--picking-a-binary-and-checking-gtfobins)
- [Step 3 — Abusing find with Sudo to Get a Root Shell](#step-3--abusing-find-with-sudo-to-get-a-root-shell)
- [Step 4 — Confirming Full Root Access](#step-4--confirming-full-root-access)
- [How Defenders Can Catch This](#how-defenders-can-catch-this)
- [How to Prevent It](#how-to-prevent-it)
- [What I Achieved](#what-i-achieved)

## Introduction

Sudo Misconfiguration is one of the most common and easiest privilege escalation techniques on Linux. When a normal user is allowed to run certain binaries as root through sudo — especially with NOPASSWD — and that binary has a way to spawn a shell or execute commands, the user can break out into a full root shell with almost no effort.

## Why This Attack Works

Sudo is meant to let normal users run specific commands as root without giving them full root access. But the problem comes in when the binaries allowed through sudo are not just simple, harmless tools. Many common Linux binaries like find, vim, awk, less, nmap, and man have hidden functions that let them execute shell commands.
If sudo allows a user to run one of these binaries as root, the user can trigger that hidden shell escape function. Since the binary itself is running as root, the shell it spawns is also root — completely bypassing the whole point of sudo restrictions.

## Lab Setup
```
| Component        | Details                                  |
|------------------|------------------------------------------|
| Attacker Machine | Kali Linux                               |
| Victim Machine   | Debian Linux                             |
| Victim IP        | 192.168.5.133                            |
| Access Method    | SSH with valid low-privilege credentials |
| Network          | VMware Host-Only Network                 |
```

## What I Needed Before Starting
```
| What                                     | Why                                            |
|------------------------------------------|------------------------------------------------|
| SSH credentials for a low-privilege user | Starting point for the attack                  |
| `sudo -l` access                         | To see which commands I could run as root      |
| GTFOBins website                         | To find the shell escape for the allowed binary|
```