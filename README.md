


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


- Next we Create Virtual network and subnet , We Search for virtual network on top and click on it :
  
  
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/0bc01dcb-997e-48a7-999d-7369ee83391f" />

- Once virtual network is selected,we select create then we fill in our parameters:
  - Subscription : you select your own base on account
  - Resource group : select the one we created
  - Virtual network name: create your own name (ex: Active-Dir-VN)
  - Region : select your region
  - Then we click create!
    

  <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/dbb206bc-9370-4920-9973-1a1ef0a83d3e" />
  

- Next we create our Virtual machine for the domain controller, we search on top for virtual machine :

  <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/f8b3402b-4cd9-4ebc-b738-969198b4863d" />

- Once it's been selected, we click create on top left
   - Subscription : you select your own base on account
  - Resource group : select the one we created
  - virtual name : create one base on your choice (ex: DC-1)
  - Region : select your region
  - image: select windows server 2022 datacenter 
  - zone : Zone 1
  - size : at least 2 vcpu!
  - Create a user name & password for VM
  - Next till we get to network
  -   Virtual network : we slecect the one we created
  -   subnet : defualt 
  - we click create !


    <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/97b35d5b-501e-4361-b8c6-848c9888fedc" />

    <img width="615" height="400" alt="image" src="https://github.com/user-attachments/assets/61e3ab22-776e-481b-aade-bd5443524e39" />

    <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/890d4e5c-52c2-4b37-bd2a-4a1e77c48ae8" />

    

- Next we create our Virtual machine for the client controller, we search on top for virtual machine :
 <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/f8b3402b-4cd9-4ebc-b738-969198b4863d" />

 
- Once it's been selected, we click create on top left
   - Subscription : you select your own base on account
  - Resource group : select the one we created
  - virtual name : create one base on your choice (ex: Client-1)
  - Region : select your region
  - image: select windows 10 enterprise
  - secuirty : standard
  - zone : Zone 1
  - size : at least 2 vcpu!
  - Create a user name & password for VM
  - Next till we get to network
  -   Virtual network : we slecect the one we created
  -   subnet : defualt 
  - we click create !
 
    <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/38e7b47c-07b2-4743-90af-dce9663ecf98" />

    <img width="615" height="400" alt="image" src="https://github.com/user-attachments/assets/61e3ab22-776e-481b-aade-bd5443524e39" />

    <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/890d4e5c-52c2-4b37-bd2a-4a1e77c48ae8" />


    

- Set Domain controller Ip address to static, open up DC-1 and the left select under networking -> network settings

  <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/b6ecf9ac-ff1c-4a07-b9a5-62b723414a15" />

  - Next we select the network interface card settings
  - click ip config bottom left corner
  - set it to static and click save
    
   <img width="546" height="102" alt="image" src="https://github.com/user-attachments/assets/835c056f-bd79-4ebb-8d98-36a63dea4b95" />

   <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/4f3dbb9d-af4f-48e7-8b93-0e54f6ec27d1" />

   <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/c066dd5d-a251-4186-9bb2-77f881095850" />

- Next we change the client-1's Dns settings to  to DC-1's private IP adress, click on Dc-1, to the right copy the private Ip

  <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/1784bf73-03ff-4d2c-9c00-a26ac948d377" />

- Next open up Client-1 and the left select under networking -> network settings, click on the network card
- We click on the left DNS servers, then select custom , paste our IP from DC-1 (10.0.0.4) then click save

  <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/a49c9d86-dfdf-4b28-9ac2-dd76f1c41043" />

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/623e6a14-6dbb-4965-92bc-8fc900a073ef" />

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/9d2c0d3f-6d27-4d09-987d-67ef1d6d5298" />


- Next we can login to our client-1 VM then run a ping command to ensure we set have sucessfully configured our Network settings
- open up powershell
- type ping 10.0.0.4 and click enter
- you should get a reply , if you did, then its working

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/d4b4bba3-1e4b-491c-9bcc-33e348f6b244" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/8660d453-356d-463f-86d0-53cb3fbff27f" />











 


### Step 3: Active Directory Installation
- Installed Active Directory Domain Services on Windows Server

- First we log into our DC-1 (windows server ),
  - Open up remote connection on your windows computer , copy and paste public Ip adress and login

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/17e87b76-9f45-4169-a582-75d082d5397b" />

 - Search for Server manger and open it
   - Click add roles and features, click Next , Next
   

   <img width="419" height="480" alt="image" src="https://github.com/user-attachments/assets/b3d2a553-079c-4383-b815-88ba3d0d8445" />

 
   <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/f8e54d16-2d3a-4004-85bf-2967ca27b1ef" />

- Next we select Active directory Domain services , and click add features

  <img width="550" height="500" alt="image" src="https://github.com/user-attachments/assets/13e72cd3-3b6b-49e9-82d8-e4e6b4bc53a0" />

- We click Next, Next and then select install

  <img width="500" height="418" alt="image" src="https://github.com/user-attachments/assets/9255d741-5ce2-4038-90a2-696c0d039842" />

- Once installed , we click close


  <img width="588" height="413" alt="image" src="https://github.com/user-attachments/assets/480230bb-4883-471f-aac1-7ace50acd6bc" />





- Promoted the server to a domain controller

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e55bb77f-4d1d-477a-939b-990423d73013" />

- Configured DNS during domain setup

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/ab48be20-bc0c-485c-9a24-a8667ed1365f" />


### Step 4: Domain Configuration
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


