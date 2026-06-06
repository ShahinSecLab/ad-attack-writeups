# golden ticket generation

**Date:** June 2026  
**Author:** ShahinSecLab  
**Category:**Credential Capture  
**Difficulty:** Easy  
**Tools:** NetExec, Evil-winrm

## Table of Contents

- [What is a Golden Ticket?](#what-is-a-golden-ticket)
- [Why This Attack is Dangerous](#why-this-attack-is-dangerous)
- [What I Needed Before Starting](#what-i-needed-before-starting)
- [What I Understood During the Process](#what-i-understood-during-the-process)
- [Step 1 — Getting a Shell on the Domain Controller](#step-1--getting-a-shell-on-the-domain-controller)
- [Step 2 — Uploading Mimikatz to the DC](#step-2--uploading-mimikatz-to-the-dc)
- [Step 3 — Dumping the krbtgt Hash](#step-3--dumping-the-krbtgt-hash)
- [Step 4 — Generating the Golden Ticket](#step-4--generating-the-golden-ticket)
- [Step 5 — Using the Golden Ticket](#step-5--using-the-golden-ticket)
- [What I Achieved](#what-i-achieved)

# What is Golden Ticket ?

A Golden Ticket is a forged Kerberos ticket that gives an attacker unlimited access to every resource in the domain — forever, or until the krbtgt account password is changed twice.
The whole attack is based on one thing — the krbtgt account. This is a special account in Active Directory that signs every single Kerberos ticket in the domain. If I get its password hash, I can forge my own tickets and pretend to be any user, including Domain Admin — without ever touching the real account.