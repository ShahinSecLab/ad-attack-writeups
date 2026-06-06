# ntds dumping

**Date:** June 2026  
**Author:** ShahinSecLab  
**Category:**Credential Capture  
**Difficulty:** Easy  
**Tools:** NetExec, Evil-winrm


## NTDS Dumping (Attacker Perspective)

From an attacker perspective during this Active Directory lab, NTDS dumping was one of the most important and high-impact stages of the entire attack chain.

After gaining access to a system with elevated privileges on the Domain Controller, I focused on extracting the Active Directory database file (NTDS.dit). This file is critical because it contains the core authentication data of the entire domain.

Instead of targeting a single user or machine, I shifted focus toward the full domain credential database.

## What I Understood During the Process

While working on this technique, I realized that:

- NTDS.dit is the main database of Active Directory
- It stores all user accounts in the domain
- It contains password hashes (not plain passwords)
- These hashes can represent both normal users and privileged accounts

This made it clear that compromising this file is equivalent to gaining deep visibility into the entire domain environment.

## Why This Step Was Important in the Lab

In the attack flow, NTDS dumping represented the final and most powerful stage of credential access. Earlier steps helped to move deeper into the system, but this step provided:

- A complete list of domain user credentials (in hash form)
- Potential access to high-privilege accounts
- A way to extend control across the network



# Steps


## Step 1

During the Token Impersonation phase, a user named **"text"** was added to the **Domain Admin group**. After obtaining elevated privileges, this account became a high-privileged domain user.

In the next stage, the credentials of the same user were used to proceed with the NTDS dumping process as part of post-exploitation activity within the Active Directory environment.
















## What I Achieved

By reaching this stage, I demonstrated that:

- I had control over a Domain Controller-level environment
- I could extract sensitive authentication data from Active Directory
- I could use this data for further analysis and lateral movement in a real scenario

## Key Takeaway

## Step - 1

During the Token Impersonation phase, a user named **"text"** was added to the **Domain Admin group**. After obtaining elevated privileges, I gained control over this account and elevated it to a high-privileged domain user.

In the next stage, I used the credentials of the same user to proceed with the NTDS dumping process as part of post-exploitation activity within the Active Directory environment.

### Credentials:

- user name: `test`
- password: `@shahin123#!`

## Step -2 