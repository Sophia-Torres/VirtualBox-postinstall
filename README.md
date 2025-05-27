![image](https://github.com/user-attachments/assets/d341aa27-38e2-4010-a238-9fbbd122516b)

<h1>VirtualBox - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration insde of Oracle Virtual Box for the virtual machines,Windows Server 2019 and Windows 10 <br />




<h2>Environments and Technologies Used</h2>

- Oracle Virtual Box
- Active Directory


<h2>Operating Systems Used </h2>

- Windows 10 ISO
- Windows Server 2019 ISO
 </b>

<h2>Post-Install Configuration Objectives</h2>

- Setup Windows Server 2019 virtual machine as a Domain Controller
- Setup Windows 10 virtual machine as a client connected to the domain
- Configure internal networking, NAT, DHCP, and Active Directory
- Use Powershell to automate the creation of 1,000 users in Active Directory

<h2>Setup Windows Server 2019 virtual machine as a Domain Controller</h2>
- With VirtualBox click "New" to setup a new virtual machine (we will be setting up Windows Server 2019)

![image](https://github.com/user-attachments/assets/c6b65845-0530-4b42-8dc9-e575623334dc)

- Name the Virtual Machine "DC" for Domain Controller
- Select the ISO image from the location in which you downloaded the ISO to
- Sections "Type" and "Version" should autopopulate to "Microsoft Windows" and "Windows Server 2019 (64-bit)
- Mark the checkbox next to "Skip Unattended Installation"

![image](https://github.com/user-attachments/assets/73d172e9-7bb9-4c71-9629-6f9fc1ed8f40)

- Default settings under other drop down menus are fine, just make sure your the amount of RAM allocated for the virtual machine is at least 2GB
- Click Finish
- Now select settings

![image](https://github.com/user-attachments/assets/618a01ac-289a-4dc9-be88-aedb18f0ba47)

- Select the Network tab on the left hand side
- Click on Adapter 2 in the main pane
- Mark the checkbox to Enable Network adapater
- In the Dropdown menu next to "Attached to:" select "Internal Network"
- Click OK at the bottom right

![image](https://github.com/user-attachments/assets/1fc85eae-c4f6-400d-af72-ae499a472136)

- Double click "DC" virtual machine to begin installing Windows Server 2019
- When installing make sure you click one of the "Desktop" versions so that you have a GUI interface

![image](https://github.com/user-attachments/assets/755f484b-7964-4f7e-a48c-6984e61774a5)

- During installation set up password
- After installation is done log in with password

<img width="1004" alt="image" src="https://github.com/user-attachments/assets/9e7990b7-170f-4404-bb14-fe21151649d5" />

- Open Ethernet settings and select "Change adapter options"

![image](https://github.com/user-attachments/assets/42b7abf2-ca24-4ebc-86b1-70c4b4205654)

- Check the IPs of the networks and then rename them to differentiate between your host network and your virtual machine's internal network

<img width="1343" alt="image" src="https://github.com/user-attachments/assets/131ddb70-51d9-4fb8-81f2-eddd92234b2f" />

- Right click your Internal network and select Properties
- Double click "Interner Protocol Version 4 (TCP/IPv4)
- Assign the IP address to 172.16.0.1
- Assign the subnet mask to 255.255.255.0
- Assign the DNS server to itself, 172.16.0.1
- Click  OK

![image](https://github.com/user-attachments/assets/d454b1e3-699e-4ff9-ae9f-713130d345ac)


- Open System Settings and click "rename this PC" and rename it to "DC"
- Restart Windows
- After logging back in go into Server Manager
- Select "Add Roles and features"
- Installation process will begin, make sure you select "Active Directory Domain Services"

![image](https://github.com/user-attachments/assets/a41b98c9-225e-4240-b271-c4917f768051)

- In the Server Manager Dashboard click the yellow triangle next to the flag
- In the pop up window select "Promote this server to domain controller" to initiate Post-deployment Configuration

![image](https://github.com/user-attachments/assets/e5479897-c28e-46da-9c7a-5dd66a9b2837)

- For deployment operation select "Add a new forest"
- Use "mydomain.com" for Root domain name
- Configure password
- Finish installation
- Restart Windows
- Login should now show username as MYDOMAIN\Administrator

<img width="1064" alt="image" src="https://github.com/user-attachments/assets/36b89f78-f245-45c7-8b08-8846c8fce324" />

- Create our own dedicated domain admin account to replace default account made
- Open "Active Directory Users and Computers" window
- Create an Organizational Unit called "_ADMINS" for the Admin account in "mydomain.com"
- Inside the "_ADMINS" create your new user

![image](https://github.com/user-attachments/assets/7719dec8-82d1-407a-a3c0-3aa412c56202)

- Assign the new user to be an admin by double clicking the username
- Select the "Member of" tab
- Click on "Add"
- Type in "Domain Admins" and click "Check Names"
- Select "OK" and then select "Apply"
- Log out and then log back in using the new admin user we created

![image](https://github.com/user-attachments/assets/610a25b5-e86e-40d3-b568-212f37bb9731)

<h2>Configure internal networking, NAT, DHCP, and Active Directory</h2>

- Go back to "Add Roles" and Features in the Server Manager
- On the "Server Roles" page check mark "Remote Access"
- On the "Role Services" page check mark "Routing"
- Install
- Once done go to "Tools" in the Server Manager and select "Routing and Remote Access"
- Right click on "DC (local) in left pane and select "Configure and Enable Routing and Remote Access"

![image](https://github.com/user-attachments/assets/af6c51d9-9343-4062-b586-6fe0f3d32027)

- Start Setup
- Make sure you select "Network address translation (NAT)" under the "Configuration" page
- For the "NAT Internet Connection" page select your host's external network as the Network Interface that is going to connect you to the internet
- Finish Setup

![image](https://github.com/user-attachments/assets/49cab1e4-9004-4507-8bac-1e4c4021678d)

- Go back to Server Manager and select "Add Roles and features"
- On the "Server Roles" page checkmark the "DHCP Server" box
- Install
- Once finished go back to "Tools" in Server Manager and select "DHCP"
- Create Scope for IPv4 by right clicking "IPv4" under the "dc.mydomain.com" tab in the left pane
- "New Scope Wizard" window will open click next to begin setup

![image](https://github.com/user-attachments/assets/286d68e2-bb14-4a41-af11-5178cf3b199e)

Name the Scope
For the Start IP Address enter "172.16.0.100" 
For the End IP Address enter "172.16.0.200"
Configure the Subnet Mask to "255.255.255.0"

![image](https://github.com/user-attachments/assets/5ac918ce-4980-4ca5-9b2e-4052c6274380)

- Add the IP address "172.16.0.1" to the "Router (Default Gateway) page
- Finish Setup
- Right click "dc.mydomain.com" and select authorize
- Right click again and select "refresh"


<h2>Use Powershell to automate the creation of 1,000 users in Active Directory</h2>

- Save Powershell script zip folder to desktop for easy access and extract (script and curated name list is in this folder)
- Open Windows Powershell ISE and run as administrator
- Select "Open" in Powershell and select the script we saved and extracted
- For lab purposes enter "Set-ExecutionPolicy Unrestricted" and enter so that script can be executed

![image](https://github.com/user-attachments/assets/8c134e1f-6486-4c3b-9805-968657ecdb61)

- Select "yes to all" in pop up window
- Go to directory where curated list of names are saved to the desktop my entering "cd C:\Users\a-storres\Desktop\AD_PS-master\AD_PS-master"
- Enter "ls" to see the name.txt
- Click green play button to run script
- User names from the names.txt will start generating

![image](https://github.com/user-attachments/assets/b17cff86-355e-4a6a-b153-b6e2a06209c8)
























<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
