


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

## Step 1 : Step 1 — Create an Azure Account

Go to the Microsoft cloud platform at: https://portal.azure.com
Click Start free or Sign in, Log in with a Microsoft account ,  (Outlook/Hotmail works)

Complete the following : Identity verification ,Phone verification ,Credit/debit card (for validation —  200$ is avalible as a free tier is offered)

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/3b104bcc-0b22-458c-8c05-237e893adfdf" />

Once finished, you’ll land in the Azure Portal Dashboard like the image below :

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/bb9159f3-b917-49f1-9bdc-1a5f43cd0822" />


### Step 2: Azure Infrastructure Setup

- Create resource group through azure by searching for resource group at the top :
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/6a81ae77-5837-4dd9-b89f-3eb7f4da59b1" />

- Once resource group is selected, now we fill in our parameters for the creating of the group:
  - Subscription : you select your own base on account
  - Resource group name : you could name whatever you like , (Ex: Active-Dir-Lab)
  - Region : select your region
  - Then we click create!
  
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/86c12fdd-27b6-4db1-be5c-a073ff8f42ad" />


  
- Created Azure virtual machines for the domain controller using :
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/ad3cf520-2d69-4c0a-95e6-4229955d1ab4" />

- Create Azure virtual machine for client using :
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


