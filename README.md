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

- Step 1: Create a Resource Group, Windows 10 VM and Linux VM on Microsoft Azure
- Step 2: Using Remote Desktop to use the Windows 10 VM and use WireShark to observe ICMP traffic
- Step 3: Configuring a Firewall within Wireshark (Network Security Group)
- Step 4: Also use WireShark to observe DHCP and DNS traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Step 1, I create a Microsoft Azure account and create a resource group. Within the resource group, I create two virtual machines; Windows 10 and Linux. I ensure both VMs are in the same subnet and virtual network so they work properly and are in sync with one another.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Step 2, I use the Windows 10 Virtual Machine to install Wireshark. Next I filter to ICMP traffic only, then go to the Linux VM and attempt to ping it from within the Windows 10 VM. I observe the ping requests and replies in Wireshark. Finally, I open a command line in the Windows 10 VM and ping a public website and observe the traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Step 3, I configure a Firewall within WireShark. I begin by initiating a non-stop ping on the Windows 10 VM to the Ubuntu VM. Next, I go to the Ubuntu VM Network Security Group and disable ICMP traffic. I observed that traffic in the Windows 10 VM. I then reenabled the ICMP traffic in Ubuntu in the Network Security Group. Finally, I disable the non-stop ping in Windows.
</p>
<br />
