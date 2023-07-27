<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Exploring Networking Concepts in Azure</h1>
In this project, I inspect various types of network traffic (ICMP, SSH, DHCP, DNS, RDP) between Azure virtual machines using Wireshark and practice creating rules in a Network Security Group. <br />

<h2>Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Network Security Groups)
- Various Command Line Tools
- Various Network Protocols (ICMP, SSH, DHCP, DNS, RDP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Create 2 virtual machines in Microsoft Azure, one running Windows 10 (named "VM1") and the other running Ubuntu ("VM2")
-  Log into the Windows 10 VM (VM1) using Remote Desktop
-  Install and open Wireshark on VM1
-  Continuously ping VM2, create an inbound rule in VM2's Network Security Group to deny ICMP traffic, observe the results in Wireshark
-  Re-enable ICMP traffic in VM2's Network Security Group, observe the results in Wireshark
-  Use the SSH command to remotely access VM2's command line, observe SSH traffic in Wireshark, exit SSH
-  Use the ipconfig /renew command to request a new IP address, observe DHCP traffic in Wireshark
-  Use the nslookup command to translate popular domain names, observe DNS traffic in Wireshark
-  Observe ongoing RDP traffic in Wireshark

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/aTnvPKe.jpg" height="75%" width="75%"/>
</p>
<p>
I began by creating 2 virtual machines in Azure: one running Windows 10 (VM1) and the other running Ubuntu (VM2). In order to ensure the virtual machines could communicate, I assigned them to the same vnet (virtual network) and subnet.</p><br />

<p>
<img src="https://i.imgur.com/ctEz1W1.jpg" height="75%" width="75%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I copied VM1's public IP address and pasted it into Remote Desktop Connection so I could login to the machine remotely.
</p>
<br />

<p>
<img src="https://i.imgur.com/VZGvtbc.jpg" height="75%" width="75%"/>
</p>
<p>
Once I was logged in to VM1, I downloaded and installed Wireshark. Wireshark is a free and open-source packet analyzer which can be used to observe and inspect network traffic.

</p>
<br />

<p>
<img src="https://i.imgur.com/EKxk84b.jpg" height="75%" width="75%" alt="Disk Sanitization Steps"/>
</p>
<p>
With Wireshark now installed, I opened the application and filtered for ICMP (Internet Control Message Protocol) traffic (green bar near the top of the screen) and opened Command Prompt. In order to send ICMP traffic over the network, I continuously pinged VM2's private IP address, which was 10.0.0.5. You can see that Wireshark displays information for each ping request (VM1 to VM2) and reply (VM2 to VM1).
</p>
<br />

<p>
<img src="https://i.imgur.com/J4HOKrv.jpg" height="75%" width="75%"/>
</p>
<p>
With the continuous ping still active, I went back to the Azure portal and opened VM2's Network Security Group. From within this blade, you can create inbound and outbound rules to filter network traffic between Azure resources in a virtual network (similar to a traditional firewall). I then created an inbound security rule to deny all ICMP traffic to VM2. 
</p>
<br />

<p>
<img src="https://i.imgur.com/1arBPVK.jpg" height="75%" width="75%"/>
</p>
<p>
Once the rule was created, the ping from VM1 to VM2 started to fail. In Wireshark, you can see consecutive ping requests from VM1 with no reply from VM2, as well as a (no response Found!) message repeatedly popping up. 
</p>
<br />

<p>
<img src="https://i.imgur.com/Fukat11.jpg" height="13%" width="13%"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/RnyheVK.jpg" height="75%" width="75%" alt="Disk Sanitization Steps"/>
</p>
<p>
After observing the ping fail, I went back to VM2's Network Security Group and changed the inbound security rule to allow ICMP traffic. As a result, VM1 was once again able to ping VM2.
</p>
<br />

<p>
<img src="https://i.imgur.com/bkqGUu8.jpg" height="75%" width="75%"/>
</p>
<p>
Next, I filtered for SSH traffic in Wireshark and used the SSH (Secure Shell) command to remotely connect to VM2's command line. Connecting to VM2 via SSH and executing Linux commands generated SSH packets that could be observed in Wireshark. Using the “exit” command, I ended the SSH session and returned to VM1's command prompt.
</p>
<br />

<p>
<img src="https://i.imgur.com/XcidF0h.jpg" height="75%" width="75%" alt="Disk Sanitization Steps"/>
</p>
<p>
In order to view DHCP traffic, I filtered for DHCP in Wireshark and used the “ipconfig /renew” command to attempt to issue a new IP address to VM1. Although the private IP address did not change, the command generated DHCP traffic and displayed the DHCP handshake in Wireshark (discover, offer, request, acknowledgement).
</p>
<br />

<p>
<img src="https://i.imgur.com/fYafCBE.jpg" height="75%" width="75%"/>
</p>
<p>
Next, I filtered for DNS (Domain Name System) traffic and used the nslookup command to look up amazon.com's IP address. In Wireshark, we can see the IP address of VM1's DNS server (168.63.129.16), as well as queries for A and AAAA records (associated with domain name-to-IPv4 and IPv6 translation, respectively).
</p>
<br />

<p>
<img src="https://i.imgur.com/TBqCQMw.jpg" height="75%" width="75%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, I filtered for RDP (Remote Desktop Protocol) traffic by typing tcp.port == 3389 into Wireshark's search bar (3389 is the port number associated with RDP). This resulted in a non-stop spam of network traffic from my host machine (97.113.18.186) to VM1 (10.0.0.5), as every input from my host machine results in data being sent over TCP port 3389 while Remote Desktop Connection is open.
</p>
<br />
