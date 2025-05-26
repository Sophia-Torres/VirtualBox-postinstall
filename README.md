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

<h2>Configuration Steps</h2>
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
