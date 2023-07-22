<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Inspecting Network Traffic Between Azure Virtual Machines</h1>
In this project, I observe various network traffic between Azure virtual machines with Wireshark and experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Network Security Groups)
- Various Command-Line Tools
- Various Network Protocols (ICMP, SSH, DHCP, DNS, RDP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Create 2 virtual machines in Microsoft Azure, one running Windows 10 (named "VM1") and the other running Ubuntu ("VM2")
-  Connect to the Windows 10 VM (VM1) using Remote Desktop
-  Install and open Wireshark on VM1
-  Continuously ping VM2, create an inbound rule in VM2's Network Security Group to deny ICMP traffic, observe the results in Wireshark
-  Re-enable ICMP traffic in VM2's Network Security Group, observe the results in Wireshark
-  Use the SSH command to connect to VM2's terminal, observe SSH traffic in Wireshark, exit SSH
-  Use the ipconfig /renew command to request a new IP address, observe DHCP traffic in Wireshark
-  Use the nslookup command to translate popular domain names, observe DNS traffic in Wireshark
-  Observe ongoing RDP traffic in Wireshark
-  Delete Resource Groups in Azure
<h2>Actions and Observations</h2>

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
