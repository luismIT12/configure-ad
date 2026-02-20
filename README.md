


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

- Next were going to set u a new forest as mydomain.com (can be anything if you like, just remember it)
  - Top left corner click under flag icon to promte this server to domain controller 
 
  <img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/7c141ad5-738d-450b-bbb8-0fb84efa8425" />


- Select add a new forest and type in mydomain.com

  <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e55bb77f-4d1d-477a-939b-990423d73013" />


  - Once we click next, we have to create a password and repeat it again, click next
 
  <img width="600" height="550" alt="image" src="https://github.com/user-attachments/assets/cbb19500-7729-4944-bffd-d1a4cc85b0f3" />

 - Unselect "create dns delegration" and click next

   <img width="525" height="414" alt="image" src="https://github.com/user-attachments/assets/3e5766a5-5816-44a4-bcfe-95f435ab39e9" />


- We click Next , Next then install

  <img width="600" height="450" alt="image" src="https://github.com/user-attachments/assets/90431f8e-c0c2-44c9-885e-71cb48285326" />



- After installtion is compelete, it will log you off automatically and restart VM, now we just log in to for confirmation
    - Once logged in, you should see your server manager similar to below
<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/f7ee804b-7a76-48bb-94da-95927edd6c5c" />




### Step 4: Domain Configuration
- Create a Domain Admin user within the domain
    - Log into DC-1 Server
    - Click bottom left corner "start" then click window adminstivtie tools then select active directory users and Computers
 
  <img width="500" height="441" alt="image" src="https://github.com/user-attachments/assets/14e5bf55-b287-4ca4-b150-2dc8e174c58f" />

  - Once opened, we click under my domain then right click , select new OU (organizational unit)

    <img width="464" height="305" alt="image" src="https://github.com/user-attachments/assets/d297b820-4e8d-46e0-8bf2-45cbad81973d" />

   - We are Creating the new OU, were going to name it "_EMPLOYEES" , also a second one called "_ADMINS"
 
     <img width="425" height="400" alt="image" src="https://github.com/user-attachments/assets/bf10426c-fa70-4d65-b8cd-9d1c66bb89cf" />

     <img width="500" height="390" alt="image" src="https://github.com/user-attachments/assets/035b1088-0dec-4db7-addf-e7b1e8c55e46" />

    - Next were going to create a new user ,First open up _ADMINS , right click then click New --> User
     
      <img width="500" height="383" alt="image" src="https://github.com/user-attachments/assets/169ec1bf-1f04-4c7c-8e95-2059199d3bd5" />

    - Fill in the boxes with your prefer name, user, password, (example Mines is Bob Lee)
      
      <img width="500" height="383" alt="image" src="https://github.com/user-attachments/assets/be4634b5-da92-48c6-9385-e8bec6c06015" />

    - Next Choose your password (unclick change password next login) then click next then finish
 
      <img width="400" height="345" alt="image" src="https://github.com/user-attachments/assets/be2275d1-78be-4478-ae97-4244508c8ea2" />

    - Next we give admin access to our user Bob_lee by adding him to  “Domain Admins” Security Group
        - right click under bob lee, click properties
          
      <img width="525" height="380" alt="image" src="https://github.com/user-attachments/assets/022baa98-b576-4951-a6b2-d9ed8804f35c" />

    - Next click under member of , Then click add, then type in "Domain Admins" then click check name then click ok
 
      <img width="625" height="400" alt="image" src="https://github.com/user-attachments/assets/632da9fa-13b7-4c94-a5e6-f6dc5553eba2" />

    - Lastly log off the VM (DC-1 ) & were log back in but using our new user bob lee's credentials
        - Use mydomain.com\Bob_lee & your , it should work

    <img width="800" height="522" alt="image" src="https://github.com/user-attachments/assets/bfc4ed55-ad41-4177-beaf-0b5b31d1b05a" />





### Step 5: Client Domain Join
- Log on to The client 1 VM, verify the computer is "client 1"

<img width="501" height="358" alt="image" src="https://github.com/user-attachments/assets/4bc38567-eb3e-4f81-9ed5-5e87b3bbbca4" />

- Search for about under start " then click on the right rename pc , then change domain group, click on member of type in "mydomain.com" then ok

  <img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/fb916173-13e3-4f70-8c2a-1b2dd0714222" />

- Once ok is clicked, a pop up windows will ask for logon credentials , thats how you know it's correct
    - provide the user's username & password (Bob_lee)
 
  
  <img width="644" height="369" alt="image" src="https://github.com/user-attachments/assets/e1738cfd-15b3-468a-8e39-e3bdba1c618b" />

- The change take affect it will prompt to restart VM

  <img width="500" height="274" alt="image" src="https://github.com/user-attachments/assets/c71c0e1d-37bd-4734-8744-b95b0e83c2f2" />

- Now we log in to our DC-1 (sever VM to confirm Client 1 is a part of the domain)

  - We type at the bottom " Active directory users & computers"
 
    <img width="500" height="359" alt="image" src="https://github.com/user-attachments/assets/d5944b6d-bb3c-45fd-8d03-6e369722526d" />

  - Under mydomain.com --> computers it should show --> client-1 (our Client VM)

 <img width="510" height="308" alt="image" src="https://github.com/user-attachments/assets/c4862e17-5a85-4fe3-aab2-e20fe15d39cd" />


### Step 6: Add Users (we adding using scripts as EX)
- First we have to Setup Remote Desktop for non-administrative users on Client-1
    - Log into Client-1 as mydomain.com\Bob_lee (your user created)
    
  <img width="507" height="367" alt="image" src="https://github.com/user-attachments/assets/c449da90-11e7-435b-8ab9-10b48fac5763" />

  - search for about , then look for remote destop

  <img width="550" height="384" alt="image" src="https://github.com/user-attachments/assets/cd34614b-4f9f-476d-892b-39f42a16c8fd" />


- select users that access remotely, then click add, type in domain users, then click check names, then click ok

<img width="554" height="268" alt="image" src="https://github.com/user-attachments/assets/b402fd59-b45e-497e-b3c9-56c8cf7473aa" />


- You can now log into Client-1 as a normal, non-administrative user now


 - Next were going to Create a bunch of additional users and attempt to log into client-1 with one of the users
     - Log in to DC-1 (server ) as Bob_Lee or your (User) & Open PowerShell_ise as an administrator
  
   <img width="500" height="480" alt="image" src="https://github.com/user-attachments/assets/eb897648-2ce5-481e-85a9-a6383199bbbd" />

   - Create a new File and paste the contents of the script (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) into it

   <img width="560" height="354" alt="image" src="https://github.com/user-attachments/assets/b858ec5d-b863-43ac-b01c-caa3a15602ca" />

  - Once the script is pasted, click the green arrow run

<img width="500" height="239" alt="image" src="https://github.com/user-attachments/assets/046e4b8e-6c6f-47f6-a612-2e40c76d1ea3" />

- if you check users now under active directory you should see a bunch of new random one generated base on the script

<img width="554" height="233" alt="image" src="https://github.com/user-attachments/assets/8d40fb49-ca7f-40b8-a8a1-39f68d4553e0" />

- Now for testing, you can log in as a random user created (EX : i am using Bado.cicup), you have successfully completed this lab!

  <img width="511" height="450" alt="image" src="https://github.com/user-attachments/assets/20b76bb5-6887-48d7-aa83-553ac0272a04" />


  <img width="577" height="247" alt="image" src="https://github.com/user-attachments/assets/33fcf558-f396-4c9a-87a8-fee5738aa3e7" />



























  

---


