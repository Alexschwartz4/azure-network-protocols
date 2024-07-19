<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Setup Resources in Azure
<p>

</p>
<p>
Create the Domain Controller VM (Windows Server 2022) named “DC-1”
 </p>
<img src="https://imgur.com/AfsY0Rp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 </p>
Set Domain Controller’s NIC Private IP address to be static
 </p>
 <img src="https://imgur.com/dkd3YDU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 </p>
Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet of DC-1
 </p>
  <img src="https://imgur.com/QJptNyi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
<br />
