<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
<h2> Part 1: Preparing AD infrastructure</h2>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create a Domain Controller in microsoft azure and set NIC IP to static
- Setup up Client VM in azure
- set Client-1s dns settings to the domain controller private ip address
- Ping Domain Controllers IP address in Client-1 to confirm the connection

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/bkRB5wV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setting the private NIC IP address to static means that the IP address won't change ever. Since we are using DC-1 as a DNS server we need to make sure that the IP address does not change. If the IP address changes the setting for Client-1 will no longer be valid. To make the Ip address chnages go to the DC-1 VM ceated -> Networking -> Network Settings -> Click the NIC -> IP configurations -> change IP address configuration to static
</p>
<br />

<p>
<img src="https://i.imgur.com/G0wXKoR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Disabling the firewall in DC-1 for testing in Client-1. In DC-1, right click start menu -> run -> type wf.msc -> turn firewall off.
</p>
<br />

<p>
<img src="https://i.imgur.com/1xG1qvY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Changing Client-1s DNS settings and NIC to point to DC-1s private IP address. network Settings -> NIC -> DNS Servers -> custom -> type DC-1s private IP address. Doint this will allow Client-1 to join the domain. To searchanything like google.com, Client-1 will look to DC-1 for it. 
</p>
<br />

<p>
<img src="https://i.imgur.com/XUtBeZR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Pinging DC-1s private IP address to confirm the conection. If the ping timed out then that would mean that DC-1 is in a different virtual network or that the windws fiewall in DC-1 is blocking the ping. ipconfig /all should show DC-1s private IP address as the DNS server. 
</p>
<br />
