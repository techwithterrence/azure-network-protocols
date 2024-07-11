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

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>


<h2>Part 1 (Create our Resources)</h2>

1.	Create a Resource Group

2.	Create a Windows 10 Virtual Machine (VM)
a.	While creating the VM, select the previously created Resource Group
b.	While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/38ea4224-8f99-4d98-a776-cc364dafdd36)

3.	Create a Linux (Ubuntu) VM
a.	While create the VM, select the previously created Resource Group and Vnet

4.	Observe Your Virtual Network within Network Watcher


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/83098675-abfc-4914-a0dc-b01bef720873)


<h2>Part 2 (Observe ICMP Traffic)</h2>

5.	Use Remote Desktop to connect to your Windows 10 Virtual Machine

![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/c590dd64-49c7-4b15-8c45-70765ddad49a)


6.	Within your Windows 10 Virtual Machine, Install Wireshark

![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/856e98f3-e029-4077-ac95-89ff7fac1f71)



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/a0174eb2-928d-459d-afed-08055aa6e40c)



7.	Open Wireshark and filter for ICMP traffic only

8.	Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
a.	Observe ping requests and replies within WireShark

9.	From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark

10.	Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
a.	Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
b.	Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
c.	Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
d.	Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
e.	Stop the ping activity

<h2>Part 2 (Observe SSH Traffic)</h2>

11.	Back in Wireshark, filter for SSH traffic only

12.	From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
a.	Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
b.	Exit the SSH connection by typing ‘exit’ and pressing [Enter]

<h2>Part 2 (Observe DHCP Traffic)</h2>

13.	Back in Wireshark, filter for DHCP traffic only

14.	From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
a.	Observe the DHCP traffic appearing in WireShark

Part 2 (Observe DNS Traffic)</h2>

15.	Back in Wireshark, filter for DNS traffic only

16.	From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
a.	Observe the DNS traffic being show in WireShark

<h2>Part 2 (Observe RDP Traffic)</h2>

17.	Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)

18.	Oserve the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
a.	Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

<h2>Lab Cleanup (DON’T FORGET THIS)</h2>

19.	Close your Remote Desktop connection

20.	Delete the Resource Group(s) created at the beginning of this lab

21.	Verify Resource Group Deletion




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
