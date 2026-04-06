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
- Windows Administrative Tools
- Active Directory Users and Computers
- Windows Settings

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (25H2)

<h2>Steps</h2>

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
Restart and then log back into the dc-1 VM as mydomain.com\labuser.
</p>
<p>
<img src="https://imgur.com/crhp9Er.png" alt="mydomain.com"/>
</p>
<p>
Open Windows Administrative Tools, via the Start Menu search bar, and open Active Directory Users and Computers. 
</p>
<p>
<img src="https://imgur.com/aLTtzaJ.png" alt="Windows Administrative Tools"/>
</p>
<p>
Right-click mydomain.com and create two New Organizational Units named _EMPLOYEES and _ADMINS.
</p>
<p>
<img src="https://imgur.com/sK9DHlK.png" alt="New Organizational Units"/>
</p>
<p>
<img src="https://imgur.com/Io4Dwsg.png" alt="EMPLOYEES"/>
</p>
<p>
<img src="https://imgur.com/qzNtPVQ.png" alt="ADMINS"/>
</p>
<p>
Right-click the ADMINS folder to create a New User who will be a member of the ADMINS OU. 
</p>
<p>
<img src="https://imgur.com/TTPlKor.png" alt="New User"/>
</p>
<p>
Create login credentials for the New User (Jane Doe). 
</p>
<p>
<img src="https://imgur.com/t4k29cL.png" alt="Jane Doe User logon"/>
</p>
<p>
<img src="https://imgur.com/Ufvj3Sx.png" alt="Jane Doe Password"/>
</p>
<p>
Right-click Jane's account and select Properties. 
</p>
<p>
<img src="https://imgur.com/9I0NiMX.png" alt="Jane Doe Properties"/>
</p>
<p>
Click the Members Of tab where you will see that Jane is a member of the Domain Users Group. Click Add to begin the process of adding Jane to another group. 
</p>
<p>
<img src="https://imgur.com/gtsxGZ3.png" alt="Add"/>
</p>
<p>
Type Domain Admins in the text box and OK to add Jane to the Domain Admins Group. Back in the Members of tab, click Add under the Member of box and OK at the bottom of the screen to complete the process. 
</p>
<p>
<img src="https://imgur.com/NPA7wEJ.png" alt="Select Groups"/>
</p>
<p>
<img src="https://imgur.com/im0VbId.png" alt="Domain Admins"/>
</p>
<p>
Log out of dc-1 and log back into Remote Desktop as mydomain.com\jane_admin with whatever password you entered earlier. 
</p>
<p>
<img src="https://imgur.com/O9H3Soc.png" alt="mydomain.com\jane_admin"/>
</p>
<br />

<p>
Log in to the client-1 VM as the original local admin (labuser).
</p>
<p>
<img src="https://imgur.com/wvcinOB.png" alt="labuser"/>
</p>
<p>
Open Settings. Click on System. Click on About. Click on Domain or Workgroup in Related Links to begin the process of changing the client-1 domain. 
</p>
<p>
<img src="https://imgur.com/KCTGa3O.png" alt="Domain or Workgroup"/>
</p>
<p>
Under the Computer Name tab in System Properties, click Change, since we will be changing the client-1 domain. 
</p>
<p>
<img src="https://imgur.com/ATNEq18.png" alt="Change"/>
</p>
<p>
Click Domain and enter mydomain.com as the domain that client-1 will be joining. Grant mydomain.com\jane_admin permission to join. Now, the client-1 VM is a member of the mydomain.com domain. 
</p>
<p>
<img src="https://imgur.com/bmtZElH.png" alt="Domain Changes"/>
</p>
<p>
<img src="https://imgur.com/3Xu1kmR.png" alt="Permission"/>
</p>
<br />

<p>
Back in the dc-1 VM (the Domain Controller), open Active Directory Users and Computers. Click mydomain.com and open the Computers folder to verify that the client-1 VM has joined the domain. 
</p>
<p>
<img src="https://imgur.com/JlKWGzi.png" alt="Computers"/>
</p>
<p>
Right-click mydomain.com and create a new Organizational Unit named _CLIENTS. Drag the client-1 VM from Computers to _CLIENTS. 
</p>
<p>
<img src="https://imgur.com/eMLQqEs.png" alt="New OU"/>
</p>
<p>
<img src="https://imgur.com/ywPbrR1.png" alt="CLIENTS"/>
</p>
<p>
<img src="https://imgur.com/MEdyfcw.png" alt="Drag"/>
</p>
