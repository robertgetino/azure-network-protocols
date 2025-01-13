<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Step 1: Create a Resource Group, Windows 10 VM and Linux VM on Microsoft Azure
- Step 2: Using Remote Desktop to use the Windows 10 VM and use WireShark to observe ICMP traffic
- Step 3: Configuring a Firewall within Wireshark (Network Security Group)
- Step 4: Also use WireShark to observe DHCP and DNS traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/robertgetino/azure-network-protocols/blob/0917bf911caeacd4a58fbde6b1bb30806540541c/resourcegroup.png" height="80%" width="80%" alt="Disk Sanitization Steps"> <img src="https://github.com/robertgetino/azure-network-protocols/blob/5be744625a72963f5e0b5275024f3edf63a980e3/linuxvm.png" height="80%" width="80%" alt="Disk Sanitization Steps"> <img src="https://github.com/robertgetino/azure-network-protocols/blob/7eef3cd8c2070d8fb91937c071bfbc01da0e2293/windowsvm.png" height="80%" width="80%" alt="Disk Sanitization Steps"> <img src="https://github.com/robertgetino/azure-network-protocols/blob/bc23a07aa22386482900cf1d6dc42bdf37efb581/Wireshark%20installation.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this project, I create a resource group named RG-Network-Activities. Within the resource group, I create two virtual machines; Windows 10 and Linux. I ensure both VMs are in the same subnet and virtual network so they work properly and are in sync with one another. After they are created, I log into the Windows VM and then download and install Wireshark.
</p>
<br />

<p>
<img src="https://github.com/robertgetino/azure-network-protocols/blob/e22ab72ae3d99c3974fcb40bb520e01ce1bab9d9/ICMP.png" height="80%" width="80%" alt="Disk Sanitization Steps"> <img src="https://github.com/robertgetino/azure-network-protocols/blob/1d7448df3785eb92f13c4e8da92d8754f18a1ebc/securityrule.png" height="80%" width="80%" alt="Disk Sanitization Steps"> <img src="https://github.com/robertgetino/azure-network-protocols/blob/5c5c4de32bc7ced3f1f7e9ec9b7485e332cbe91b/icmp%20deny.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After I install Wireshark, I filter to ICMP traffic only, then connect to the Linux VM and attempt to ping it from within the Windows 10 VM, using Windows PowerShell. I observe the ping requests and replies Next, I configure a firewall, by initiating a non-stop ping from the Windows 10 VM to the Linux VM. In order to do this, I navigate to Network Security Group in the Linux VM on Microsoft Azure. I create a new security rule to block any inbound ICMP traffic from the Windows VM to the Linux VM. I then observe that the ICMP traffic on PowerShell gets timed out. I then stop the ping activity and delete the security rule.
</p>
<br />

<p>
<img src="https://github.com/robertgetino/azure-network-protocols/blob/fe1efde48c89bf7adf3924a846a96cd97e6e91c1/ssh.png" height="80%" width="80%" alt="Disk Sanitization Steps"> <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I filter to SSH traffic only from the Windows VM. I go to Windows PowerShell and enter the command "ssh labuser@(private ip address). I observe the SSH traffic on Wireshark and then exit the connection on PowerShell. I go back to Wireshark and filter by DHCP traffic only from the Windows VM to the Linux VM. Similarly when I filtered by SSH traffic, I go to Windows PowerShell and enter the command "ipconfig /renew". I observe what happens and I see the configuration of the Linux VM. I then exit from DHCP in PowerShell.
</p>
<br />
