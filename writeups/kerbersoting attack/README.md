# kerberosting attack

**Date:** June 2026  
**Author:** ShahinSecLab  
**Category:** Active Directory  
**Difficulty:** Medium 
**Tools:** Meterpreter, Incognito, Windows Access Tokens

# Table of content

- [What is Kerberoasting?](#what-is-kerberoasting)
- [How Kerberoasting Works](#how-kerberoasting-works)
- [Lab Setup](#lab-setup)
- [Attack Process](#attack-process)
  - [Step 1 – Find Service Accounts](#step-1--find-service-accounts)
  - [Step 2 – Request Service Tickets](#step-2--request-service-tickets)
  - [Step 3 – Extract the Ticket](#step-3--extract-the-ticket)
  - [Step 4 – Crack the Ticket Offline](#step-4--crack-the-ticket-offline)
  - [Step 5 – Use the Credentials](#step-5--use-the-credentials)
- [Why Kerberoasting is Dangerous](#why-kerberoasting-is-dangerous)
- [Detection](#detection)
- [Mitigation](#mitigation)
- [Impact](#impact)
- [Key Takeaways](#key-takeaways)
- [MITRE ATT&CK Mapping](#mitre-attck-mapping)
- [References](#references)