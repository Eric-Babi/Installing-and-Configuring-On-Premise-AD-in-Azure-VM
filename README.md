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

- Create Two VMs, one to be Client and another a server that host Domain Controller (DC-1)
- Test VMs Online Connectivity
- Allow inbound ICMP traffic on DC-1's Firewall
- Test Communication between VMs by perpertual ping
- Promote server to domain
- Created Organzational Units (OU) in Active Directory 
- Join Client-1 to Domain
- Allow Remote Desktop for all domain users on Client-1
- Automate creation of multiple additional domain users using a script on Powershell ISE 
- Test New User Accounts ability to log onto Client-1 computer. Admin should be able to log into client-1 as well. 

<h2>Deployment and Configuration Steps</h2>
1. Deploying and Provisioning Windows Server Machine (DC-1)
<p>
   <br/>
<img src="https://i.imgur.com/0uajV1y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <br/>
 -  Setting a static private IP for DC-1 to allow consistency in access of resources by clients
   <p>
      
   </p>
 - Go to DC-1's network settings --> select networking --> click the hyperlink next to "network interface" --> "IP Configurations" --> "ipconfig1"
 </p>
 - change the assignment from dynamic to static (this ensures DC-1's IP address will not change). 
 <p>
 - Restart the Server for changes to take effect
  <p>
<img src="https://i.imgur.com/qRgFYWf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
<br />

2. Deploying and Provisioning Windows Client Copmuter (Client-1)
<p>
   
</p>
   - Check the NIC settings to make sure both VMs are on the same "Vnet" [Client-1-vnet/default]. This will ensure both VMs can communicate & connect with each other later in this lab.
   <p>
   - change client-1 DNS to point to the private IP of DC-1 to allow client-1 to join the domain and for name resolution. 
      <p>
            <br/>
<img src="https://i.imgur.com/EAt2puh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  - Restart client-1
<p>
   <br/>
3. Test Communication between DC-1 and Client-1 using pepertul ping
   <p>
      <p>
   - Remote Desktop into DC-1 and Client-1
<img src="https://i.imgur.com/s3feTsG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  - On windows Frewall settings, allow inbound traffic for ICMP on DC-1's Firewall.
<img src="https://i.imgur.com/a5TWV06.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  - Communication between DC-1 and Client-1 Successful
</p>
<p>
 Before firewall settings were changed, the ping command from Client-1 was timing out
<img src="https://i.imgur.com/IaWD7HW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
4. Install Active Directory on DC-1 and set up DC-1 as the Domain Controller
   <p>
      <p>
   - Remote Desktop into DC-1 and log in with respect to the domain (babi.com/labuser)
</p>
<p>
5. Create Organisational Units (OU) in AD
   <p>
      <p>
   - Set-up EMPLOYEE and ADMIN OUs
<img src="https://i.imgur.com/HiNhfpB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
6. Create New users and assign one in Admin Group and the other in domain users group
   <p>
      <p>
   - Admin User - babi.com/smith
          <p>
              <p>
<img src="https://i.imgur.com/t6HKQPi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
 - Domain User - babi.com/karen
          <p>
              <p>
<img src="https://i.imgur.com/gwYGZrG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
7. Add client-1 to domain
   <p>
      <p>
   <img src="https://i.imgur.com/XbaX26v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
          <p>
              <p>

8. Enable remote desktop for domain users on client-1
</p>
<p>
   - remote desktop client-1 using admin credentials
   <p>
      <p>
<img src="https://i.imgur.com/0hm6nwp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
   
9. Remote desktop client-1 using domain user credentials (babi.com\karen)
</p>
<p>
   - this proves that any domain user can now remote desktop client-1
   <p>
      <p>
      - as you can see, whoami commands shows its karen smith who is one of the domain users and the hostname is client-1.
         <p>
      <p>
     
<img src="https://i.imgur.com/6GQrJ2c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
     - and babi.com\karen cannot log into DC-1 since she is not an admin and since DC-1 was not enabled to allow remote desktop by domain users
   <p>
      <p>     
<img src="https://i.imgur.com/MHMdgYr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
10. Automate creation of additional domain users using Powershell
</p>
<p>
   - remote desktop DC-1 using admin credentials
   <p>
      <p>
   - run powershell SE script to add more users
   <p>
      <p>
<img src="https://i.imgur.com/Dxgke0q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<br />

11. Finally, remote desktop client-1 using one of the random users created through script
<p>
<p>
<img src="https://i.imgur.com/SM226Pz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
12. Disable and enable domain user account
<br />
<p>
13. Reset user password
</p>
</p>
<p>
14. Add domain user account to admin group 
</p>
</p>

