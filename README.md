<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

# Configuring On-Premises Active Directory Within Azure Virtual Machines

## Project Summary
This project follows IT Support curriculum and demonstrates how to configure an on-premises-style Active Directory environment using Microsoft Azure virtual machines. The lab simulates a traditional enterprise network by deploying a domain controller, creating users and groups, and joining a client computer to the domain.

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
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/ad3cf520-2d69-4c0a-95e6-4229955d1ab4" />

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e12d6b5c-3a1f-48ec-a65a-0be1ad5608aa" />


- Configured internal networking between virtual machines

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/b99dd306-19ba-4403-9b86-0f051880f0be" />


### Step 2: Active Directory Installation
- Installed Active Directory Domain Services on Windows Server
  
  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/19135c8a-e185-4910-bd72-48b26de161e9" />

- Promoted the server to a domain controller

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e55bb77f-4d1d-477a-939b-990423d73013" />

- Configured DNS during domain setup

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/ab48be20-bc0c-485c-9a24-a8667ed1365f" />


### Step 3: Domain Configuration
- Created Organizational Units (OUs)

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/cc9057fa-0cba-475a-a1df-a6dc2daa5198" />

- Created domain users using powershell and security groups

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/57e6f542-e246-4278-a7c9-661774ad92c3" />

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/66360302-d618-4f31-aa01-62c73a374255" />



### Step 4: Client Domain Join
- Joined the Windows 10 virtual machine to the domain

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/3cc69921-24d1-456c-a502-2222b971bef4" />

- Logged in using a domain user account to verify functionality

<img width="396" height="159" alt="image" src="https://github.com/user-attachments/assets/dd845c14-7f58-4e09-b212-8206540edefb" />
  

---

## Skills Demonstrated
- Windows Server administration
- Active Directory management
- User and access control
- Cloud-hosted lab environments

