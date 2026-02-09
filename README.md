<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployment (Azure)</h1>
This tutorial outlines the installation of Active Directory on your dc-1 virtual machine, the promotion of dc-1's server to a domain controller, the creation of a domain admin user, the joining of your client-1 virtual machine to the domain, modifying client-1 so that non-administrative users can log in, and the creation of these additional users. Active Directory is Microsoft software designed to manage user accounts and their associated properties, such as passwords and permissions, at scale. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure 
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (25H2)

<h2>Deployment and Configuration Steps</h2>

<p>
Log in to the Dc-1 Virtual Machine via Remote Desktop using its Public IP Address. In the Start menu, click on Server Manager and then Add Roles and Features. Install Active Directory Domain Services on this server. Next, promote the Windows Server on the Dc-1 VM to a Domain Controller. From now on, whenever you log into DC-1, instead of just typing the username (labuser), you must type mydomain.com\username (mydomain.com\labuser). 
</p>
<p> 
<img src="https://imgur.com/mv6IIdD.png" alt="Add Roles and Features"/>
</p>
<p>
<img src="https://imgur.com/Ebrmbe6.png" alt="Active Directory Domain Services"/>
</p>
<p>
<img src="https://imgur.com/Wqe8KPc.png" alt="Confirmation"/>
</p>
<p>
<img src="https://imgur.com/JTmmxZ0.png" alt="Promote Server"/>
</p>
<p>
<img src="https://imgur.com/fQb7bco.png" alt="Root Domain"/>
</p>
<p>
<img src="https://imgur.com/83gZBLj.png" alt="Review Options"/>
</p>
<p>
<img src="https://imgur.com/0vrITxS.png" alt="Prerequisites Check"/>
</p>
<br />

<p>
In the DC-1 VM start menu, click on Active Directory Users and Computers. Create two organizational units ( _EMPLOYEES and _ADMINS). Create a Domain Admin user by adding a new employee (Jane Doe) to the _ADMINS folder, which will make the employee a member of Domain Users. Right-click the employee and click Properties to add the employee to Domain Admins. As a Domain Admin, this employee will have near-total control over the domain and its associated user accounts.
</p>
<p>
<img src="https://imgur.com/P7PVclQ.png" alt="ADUC"/>
</p>
<p>
<img src="https://imgur.com/v9pRPVk.png" alt="OU"/>
</p>
<p>
<img src="https://imgur.com/nqJpuIB.png" alt="EMPLOYEES"/>
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
