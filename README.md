<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>


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

- Step 1: Create our Resources

</p>
Create a Resource Group
<p>
  <p>
      <img src="https://imgur.com/Ch3udlA.png" alt="Disk Sanitization Steps"/>
           <p>
Create a Windows 10 Virtual Machine (VM)
 <p>
While creating the VM, select the previously created Resource Group
  <p>
While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
   <p>
Create a Linux (Ubuntu) VM
    <p>
While create the VM, select the previously created Resource Group and Vnet
     <p>
      <img src="https://imgur.com/KYDc6H9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>

- Step 2: Observe ICMP Traffic
  Use Remote Desktop to connect to your Windows 10 Virtual Machine
  </p>
Within your Windows 10 Virtual Machine, Install Wireshark
    <p>
         <p>
      <img src="https://imgur.com/aaQsTbq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
Open Wireshark and filter for ICMP traffic only
    <p>
      <p>
      <img src="https://imgur.com/fauwnwl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
    <p>
Observe ping requests and replies within WireShark
    <p>
      <img src="https://imgur.com/yfYxtN1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
    <p>
      <p>
      <img src="https://imgur.com/LWyusr6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
    <p>
     <p>
      <img src="https://imgur.com/eluzcpY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>

Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
    <p>
       <p>
      <img src="https://imgur.com/TJjrDY4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
    <p>
    <p>
      <img src="https://imgur.com/3RWMA5v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
    <p>
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
    <p>
Stop the ping activity

- Step 3: Observe SSH Traffic
Back in Wireshark, filter for SSH traffic only
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
  <p>
      <img src="https://imgur.com/b2osLIY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
Exit the SSH connection by typing ‘exit’ and pressing [Enter]
<p>
      <img src="https://imgur.com/b2osLIY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
- Step 4: Observe DHCP Traffic
Back in Wireshark, filter for DHCP traffic only
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
Observe the DHCP traffic appearing in WireShark
<p>
      <img src="https://imgur.com/JOP9SYy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>

- Step 5: Observe DNS Traffic
Back in Wireshark, filter for DNS traffic only
From your Windows 10 VM within a command line, use nslookup to see what google.com's IP addresses are
Observe the DNS traffic being show in WireShark
<p>
       <img src="https://imgur.com/jOysRFv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
- Step 6: (Observe RDP Traffic)
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
Oserve the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted
<p>
  <img src="https://imgur.com/0oLcQxe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>
- Step 7: Lab Cleanup 
Close your Remote Desktop connection
Delete the Resource Group(s) created at the beginning of this lab
Verify Resource Group Deletion
<p>
  <img src="https://imgur.com/e2WnppT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
           <p>


