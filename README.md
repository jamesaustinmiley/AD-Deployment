<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployment (Azure)</h1>
This tutorial outlines the installation of Active Directory on your dc-1 virtual machine, the promotion of dc-1's server to a domain controller, the creation of a domain admin user, the joining of your client-1 virtual machine to the domain, modifying client-1 so that non-administrative users can log in, and the creation of these additional users. Active Directory is Microsoft software that is designed for the management of user accounts and their associated properties, such as passwords and permissions, on a large, centralized scale. <br />


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
Log in to the Dc-1 Virtual Machine via Remote Desktop using its Public IP Address. In the Start menu, click on Server Manager and then Add Roles and Features. Install Active Directory Domain Services on this server. Next, promote the Windows Server on the Dc-1 VM to a Domain Controller. From now on whenever you log into DC-1, instead of just typing the user name (labuser) you must type mydomain.com\user name (mydomain.com\labuser). 
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
In the dc-1 vm start menu, click on Active Directory Users and Computers. Create two organizational units ( _EMPLOYEES and _ADMINS). Create a Domain Admin user by adding a new employee (Jane Doe) to the _ADMINS folder which will make the employee a member of Domain Users. Right-click the employee and click Properties to add the employee to Domain Admins. As a Domain Admin user, this employee will have near-total control over the entire domain and its associated user accounts. 
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

<br />
