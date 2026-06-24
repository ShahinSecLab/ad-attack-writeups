# Scheduled Task Manipulation

**Date:** June 2026<br>
**Author:** ShahinSecLab<br>
**Category:** Privilege Escalation<br>
**Difficulty:** Easy<br>
**Tools:** msfvenom, Metasploit, accesschk.exe

# Table of Contents

- [Introduction](#introduction)
- [Why This Attack Works](#why-this-attack-works)
- [Lab Setup](#lab-setup)
- [What I Needed Before Starting](#what-i-needed-before-starting)
- [What I Understood During the Process](#what-i-understood-during-the-process)
- [Attack Flow](#attack-flow)
- [Step 1 — Exploring the File System](#step-1--exploring-the-file-system)
- [Step 2 — Checking the BGinfo Folder](#step-2--checking-the-bginfo-folder)
- [Step 3 — Finding the Vulnerable Script in DevTools](#step-3--finding-the-vulnerable-script-in-devtools)
- [Step 4 — Checking File Permissions on CleanUp.ps1](#step-4--checking-file-permissions-on-cleanupps1)
- [Step 5 — Injecting the Payload into CleanUp.ps1](#step-5--injecting-the-payload-into-cleanupps1)
- [Step 6 — Waiting for the Shell](#step-6--waiting-for-the-shell)
- [How Defenders Can Catch This](#how-defenders-can-catch-this)
- [How to Prevent It](#how-to-prevent-it)
- [What I Achieved](#what-i-achieved)

