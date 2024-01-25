<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>
</p>

<h1>Installing-and-Configuring-On-Premise-AD-in-Azure-VM</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Create Two VMs, one to be Client and another a server that host Domain Controller (DC-1)
- Step 2: Test VMs Online Connectivity
- Step 3: Allow inbound ICMP traffic on DC-1's Firewall
- Step 4: Test Communication between VMs by perpertual ping
- Step 5: Promote server to domain
- Step 6: Created Organzational Units (OU) in Active Directory 
- Step 7: Join Client-1 to Domain
- Step 8: Allow Remote Desktop for all domain users on Client-1
- Step 9: Automate creation of multiple additional domain users using a script on Powershell ISE 
- Step 10: Test New User Accounts ability to log onto Client-1 computer. Admin should be able to log into client-1 as well. 

<h2>Deployment and Configuration Steps</h2>
1. Deploying and Provisioning Windows Server Machine (DC-1)
<p>
   <br/>
<img src="https://i.imgur.com/0uajV1y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <br/>
 -  Setting a static private IP for DC-1 to allow consistency in access of resources by clients
  - Restart the Server for changes to take effect
  <p>
<img src="https://i.imgur.com/qRgFYWf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
<br />

2. Deploying and Provisioning Windows Client Copmuter (Client-1)
   - Ensure waiting for DC-1 to be completely deployed before creating Client-1 so that virtual network for DC-1 is also applied to Client-1
<p>
   <br/>
<img src="https://i.imgur.com/0uajV1y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>







<p>
<img src="https://i.imgur.com/KopD75T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Successful deployment of client computer.
</p>
<br />

<p>
<img src="https://i.imgur.com/G4BgNkB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here i am going into the server firewall settings to allow ICMP traffic inbound so client computer can communicate with server.
</p>
<br />

<p>
<img src="https://i.imgur.com/UgCQRGg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here i executed a ping command from the client computer to the server to ensure connectivity. As you can see, the connection was successful.
</p>
<br />

<p>
<img src="https://i.imgur.com/KVGdRrP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Active Directory has been installed and the server was promoted to domain status. Next, i will create an admin account & a user account.
</p>
<br />

<p>
<img src="https://i.imgur.com/WFtcVkQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created an employee called jane admin & added her to the Domains Admin group. Next, i will connect client computer to the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/jVQzEdu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Changed client DNS to server private ip address so to allow it to connect to the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/Cdj3FYo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Used ipconfig /all to verify client computer connection to the server. Client DNS is 10.0.0.4 which is the same as the server private ip address.
</p>
<br />

<p>
<img src="https://i.imgur.com/ve164yk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Allowing all domain users remote desktop access to server via client computer.
</p>
<br />

<p>
<img src="https://i.imgur.com/yxEBpGc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Using Powershell ISE to generate random users to domain users in server.
</p>
<br />

<p>
<img src="https://i.imgur.com/wZXTSB8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Logged in as a random non-administrative user on client computer accessing the server.
</p>
<br />
</p>

