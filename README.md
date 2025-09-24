<p align="center">
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/08b4eda2-473f-4cc3-a35e-44f13257e740" />


</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (24H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1013" height="670" alt="image" src="https://github.com/user-attachments/assets/ab8b9316-b813-4fbb-9739-5448e9314b0a" />


</p>
<p>
I started by logging into the VM's for dc-1 (as Jane) and client-1 (as cit.sel). In dc-1, I went to the Windows C drive in file explorer and added three new  folders: read-access, write-access, no-access, and accounting.
</p>
<br />

<p>
<img width="1421" height="897" alt="image" src="https://github.com/user-attachments/assets/a5708cd9-5dd8-4598-8d7f-446c4a6c54f7" />


</p>
<p>
I then went to the properties of the read-access folder, clicked the sharing tab, then added Domain Users and selected read only permission level. I then did the same thing for the write-access and no-access folders, but I gave write-access read/write permissions for domain users, and no-access read/write permissions for domain admins.
</p>
<br />

<p>
<img width="1222" height="528" alt="image" src="https://github.com/user-attachments/assets/ba9c610c-9650-41df-853a-4f18d98d9a0f" />


</p>
<p>
I then went to client-1 in order to test the file shares I just added. I went to file explorer and searched for \\dc-1.
</p>
<br />

<p>
<img width="1232" height="672" alt="image" src="https://github.com/user-attachments/assets/41a10513-02e4-4b42-afc0-27672468a4e8" />


</p>
<p>
I double clicked the read-access folder and tried to create a new folder inside it. Because the read-access folder only gives read access to domain users, cit.sel is unable to create anything inside of it.
</p>
<br />

<p>
<img width="1242" height="603" alt="image" src="https://github.com/user-attachments/assets/7d479fd8-6db2-4908-a978-39a13c9e69ed" />


</p>
<p>
I then went to the write-access folder and was able to create a new text document in it because domain users have read/write access.
</p>
<br />

<p>
<img width="1188" height="613" alt="image" src="https://github.com/user-attachments/assets/d60f90ae-5868-4ab2-82f7-091607c186ca" />


</p>
<p>
Next I tried to access the no-access folder, which only gave me an error message because cit.sel is not a domain admin.
</p>
<br />

<p>
<img width="927" height="643" alt="image" src="https://github.com/user-attachments/assets/a8eae31d-000a-4a2a-9641-2b50eeb938df" />


</p>
<p>
I then went back to dc-1 and went to active directory users and computers. I created a new organizational unit called _GROUPS for easier oganization.
</p>
<br />

<p>
<img width="917" height="691" alt="image" src="https://github.com/user-attachments/assets/425db64f-8d07-441e-be8c-463899825497" />


</p>
<p>
I right clicked in the GROUPS folder and clicked new group. I named the new group ACCOUNTANTS and left it as a global security group.
</p>
<br />

<p>
<img width="1465" height="732" alt="image" src="https://github.com/user-attachments/assets/6a6354c6-84fb-4099-ae13-07f9592cf1bd" />


</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1041" height="631" alt="image" src="https://github.com/user-attachments/assets/f353b0f0-39aa-4e12-953e-58fb9c6b8646" />


</p>
<p>
Back in client-1... I then logged out of client-1 as cit.sel for now.
</p>
<br />

<p>
<img width="1110" height="745" alt="image" src="https://github.com/user-attachments/assets/b9bc1b64-90de-4557-8ccb-4f79d33f7541" />


</p>
<p>
I added cit.sel as a member of the accountants group.
</p>
<br />

<p>
<img width="1011" height="511" alt="image" src="https://github.com/user-attachments/assets/c717231a-34b9-49a1-9026-d21ac15888db" />


</p>
<p>
I logged back into client-1 as cit.sel, and was able to access and edit the accounting folder. This concludes the project.
</p>
<br />

