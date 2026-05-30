# token impersonation attack

**Date:** May 2026  
**Author:** ShahinSecLab  
**Category:** Network Attack / Credential Capture  
**Difficulty:** Easy  
**Tools:** Meterpreter, Incognito, Windows Access Tokens

## Table of Contents

- [Introduction](#introduction)
- [Lab Setup](#lab-setup)
- [Attack Flow](#attack-flow)
- [Step 1 - Get a Meterpreter Session](#step-1---get-a-meterpreter-session)
- [Step 2 - Load Incognito](#step-2---load-incognito)
- [Step 3 - List Available Tokens](#step-3---list-available-tokens)
- [Step 4 - Impersonate the Administrator Token](#step-4---impersonate-the-administrator-token)
- [Step 5 - Verify Access](#step-5---verify-access)
- [Why It Worked](#why-it-worked)
- [Detection](#detection)
- [Mitigation](#mitigation)
- [Key Takeaways](#key-takeaways)
- [References](#references)
- [Disclaimer](#disclaimer)

# Introduction

In this lab, I practiced a Windows Token Impersonation attack.

Windows creates an access token whenever a user logs in. The token contains information about that user's permissions and privileges.

If a privileged token is available on a compromised machine, it may be possible to impersonate that token and perform actions as that user.

The goal of this lab was to identify available tokens and impersonate a privileged account from an existing Meterpreter session.

# lab Setup

| Machine             | Role              |   Ip          |
| ------------------- | ----------------- |---------------|
| Kali Linux          | Attacker          | 192.168.5.128 |
| Windows 10          | Victim            | 192.168.5.135 |
| Windows Server 2019 | Domain Controller | 192.168.5.134 |
