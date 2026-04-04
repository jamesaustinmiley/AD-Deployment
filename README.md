<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployment</h1>
This tutorial outlines the installation of Active Directory on your dc-1 Virtual Machine, the promotion of dc-1's server to a Domain Controller, the creation of a Domain Admin user, and the joining of your client-1 VM to the domain. Active Directory is Microsoft software designed to manage user accounts and their associated properties, such as passwords and permissions, at scale. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure 
- Remote Desktop
- Server Manager
- Active Directory Domain Services 

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (25H2)

<h2>Deployment Steps</h2>

<p>
Log in to the dc-1 Virtual Machine, via Remote Desktop, using its Public IP Address and login credentials. 
</p>
<p> 
<img src="https://imgur.com/uMwwyZw.png" alt="dc-1"/>
</p>
<p>
Open Server Manager via the Start Menu search bar and click Add Roles and Features. 
</p>
<p>
<img src="https://imgur.com/pAtvk97.png" alt="Server Manager"/>
</p>
<p>
Proceed to Server Roles where you will install Active Directory Domain Services on the dc-1 server.  
</p>
<p>
<img src="https://imgur.com/ZgutBSj.png" alt="Server Roles"/>
</p>
<p>
Click Active Directory Domain Services and then click Add Features. 
</p>
<p>
<img src="https://imgur.com/ioHsGnd.png" alt="Add Features"/>
</p>
<p>
<img src="https://imgur.com/pePBVy9.png" alt="Active Directory Domain Services"/>
</p>
<p>
Continue on to the Confirmation page to complete the installation. Check the prompt that will restart the destination server after installation. 
</p>
<p>
<img src="https://imgur.com/fNFTOaE.png" alt="Confirmation"/>
</p>
<p>
Once the server has restarted, open Server Manager where you will see AD DS on the Dashboard. 
</p>
<p>
<img src="https://imgur.com/kOyTBVM.png" alt="Restart"/>
</p>
<p>
Click on the flag with the yellow triangle at the top of the Server Manager screen and then click Promote this Server to a Domain Controller. 
</p>
<p>
<img src="https://imgur.com/r3ca87B.png" alt="Flag"/>
</p>
<p>
On the Deployment Configuration page, select Add a New Forest and type mydomain.com as the Root Domain Name. 
</p>
<p>
<img src="https://imgur.com/ePOca05.png" alt="New Forest"/>
</p>
<p>
On the Domain Controller Options page, enter a password that will be used for Remote Desktop access. 
</p>
<p>
<img src="https://imgur.com/fkr0lom.png" alt="Domain Controller Options"/>
</p>
<p>
On the DNS Options page, make sure that the Create DNS Delegation box is unchecked. Proceed to the final page for installation.
</p>
<p>
<img src="https://imgur.com/Jqnz9L4.png" alt="DNS"/>
</p>
<br />

<p>
Restart and then log back into the dc-1 VM as mydomain.com\username.
</p>
<p>
<img src="https://imgur.com/crhp9Er.png" alt="mydomain.com"/>
</p>
<p>

</p>
<p>
<img src=".png" alt=""/>
</p>
<p>
<img src="https://imgur.com/OUhMrbv.png" alt="ADMINS"/>
</p>
<p>
<img src="https://imgur.com/B5xS1gY.png" alt="ADU2"/>
</p>
<p>
<img src="https://imgur.com/Gf9Zljp.png" alt="User"/>
</p>
<p>
<img src="https://imgur.com/x6bJKgW.png" alt="Jane Doe"/>
</p>
<p>
<img src="https://imgur.com/Yqu5OZP.png" alt="Finish"/>
</p>
<p>
<img src="https://imgur.com/WTePDoa.png" alt="Properties"/>
</p>
<p>
<img src="https://imgur.com/Gm09bOS.png" alt="Domain Admins"/>
</p>
<p>
<img src="https://imgur.com/ffepkoQ.png" alt="Properties 2"/>
</p>
<br />

<p>
Log into the Client-1 Virtual Machine via Remote Desktop as the original local admin (labuser) and finish the process of joining Client-1 to the domain (mydomain.com by going to Settings, System, About, and Device Specifications. Log in to dc-1 and verify that client-1 appears within Active Directory Users and Computers. Create a new organizational unit named _CLIENTS and move client-1 into it. Log back into client-1 as mydomain.com\jane_admin. In the Start menu, go to System and then Remote Desktop. Adding Domain Users to the Remote Desktop will allow all domain members, including non-administrative users, to log in to client-1.
</p>
<p>
<img src="https://imgur.com/teS2JGP.png" alt="System Properties"/>
</p>
<p>
<img src="https://imgur.com/5pv9Wzf.png" alt="Domain Change"/>
</p>
<p>
<img src="https://imgur.com/pRjLF2M.png" alt="Permission"/>
</p>
<p>
<img src="https://imgur.com/pxQsepU.png" alt="ADU Client-1"/>
</p>
<p>
<img src="https://imgur.com/6YRvwTL.png" alt="CLIENTS"/>
</p>
<p>
<img src="https://imgur.com/wcMqOdy.png" alt="Remote Desktop"/>
</p>
<p>
<img src="https://imgur.com/TInJwiS.png" alt="Select Users or Groups"/>
</p>
<p>
<img src="https://imgur.com/aNb00jl.png" alt="Remote Desktop Users"/>
</p>
<br />

<p>
Log in to the DC-1 virtual machine as jane_admin. Type PowerShell in the search bar, right-click Windows PowerShell ISE, and click Run as Administrator. Click on the Script down arrow to unveil a text box above PowerShell. Copy a script with code, save it as create-users on the Desktop, and paste it in the text box above PowerShell, where it can run and create new users to join the Active Directory. After running the script, open Active Directory Users and Computers and observe the new accounts that should be listed in the _EMPLOYEES organizational unit. You should be able to log in to the Client-1 VM as any of the new employees, since they are now members of the Domain Users group, which means they can use Remote Desktop. When logging in to Client-1 with one of the new employees, do so as mydomain.com\"employee name" (gig.foc) with Password1 as the password, which was part of the code used to create the new employees. 
</p>
<p>
<img src="https://imgur.com/BDD1FBx.png" alt="Powershell ISE"/>
</p>
<p>
<img src="https://imgur.com/OJ1RR4a.png" alt="Raw Code"/>
</p>
<p>
<img src="https://imgur.com/DXM7J2j.png" alt="New File"/>
</p>
<p>
<img src="https://imgur.com/NZm98SR.png" alt="Run Script"/>
</p>
<p>
<img src="https://imgur.com/ztlp3uP.png" alt="New Employees"/>
</p>
<p>
<img src="https://imgur.com/Ogse8U3.png" alt="Employee Log in"/>
</p>
