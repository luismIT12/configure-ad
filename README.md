<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

# Configuring On-Premises Active Directory Within Azure Virtual Machines

## Project Summary
This project follows the CourseCareers IT Support curriculum and demonstrates how to configure an on-premises-style Active Directory environment using Microsoft Azure virtual machines. The lab simulates a traditional enterprise network by deploying a domain controller, creating users and groups, and joining a client computer to the domain.

This project highlights foundational Windows Server and identity management skills used in real-world IT environments.

### Languages Used
- PowerShell

### Environments Used
- Microsoft Azure
- Windows Server 2022
- Windows 10

### Technologies / Applications / Services Used
- Active Directory Domain Services (AD DS)
- DNS
- Microsoft Azure Virtual Machines
---

## Demonstration

### Step 1: Azure Infrastructure Setup
- Created Azure virtual machines for the domain controller and client machine
- Configured internal networking between virtual machines

### Step 2: Active Directory Installation
- Installed Active Directory Domain Services on Windows Server
- Promoted the server to a domain controller
- Configured DNS during domain setup

### Step 3: Domain Configuration
- Created Organizational Units (OUs)
- Created domain users and security groups

### Step 4: Client Domain Join
- Joined the Windows 10 virtual machine to the domain
- Logged in using a domain user account to verify functionality

---

## Skills Demonstrated
- Windows Server administration
- Active Directory management
- User and access control
- Cloud-hosted lab environments

