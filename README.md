<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>


![wireshark-1](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/bfbfbf05-8ed7-4eff-8332-b7a38ac6361c)




<h1>Wireshark, Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04



![Lets-Get-Started-2-1-1024x480](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/3be048a1-0dbc-4c7d-95ff-0ab098d5f0bf)



<h2>Follow My Steps Below!</h2>


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



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/2ed7df9e-a10d-4011-bde2-271ae8206bf5)




7.	Open Wireshark and filter for ICMP traffic only



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/4c338527-8b16-44e9-a929-c0661a7e8c3c)




8.	Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
a.	Observe ping requests and replies within WireShark


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/d56b3352-c54c-4874-b7ff-3226b6719683)


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/d3983335-2278-48a4-9b49-f14c9881bbd3)





10.	From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/2ee41aeb-04df-4c28-9a65-0dadeddd68a8)



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/36903ad2-db2d-48f2-8d5b-64cdec03bb95)



11.	Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM

![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/96b8929f-b511-4be2-b6eb-a1fdb02e7d1b)

a.	Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic

![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/f576ec9f-b112-4fc0-a26a-0413edfaf876)


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/7c9c23ba-fa25-4c7b-a8e6-f10dd91a3b62)


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/41b59aaf-a08c-49bc-ba49-f1b6b0737ecf)



b.	Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/77456d1a-77ef-41d1-be5b-d46a614286b9)




c.	Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/dffc818c-f4a7-4e45-8b41-35876f06e408)



d.	Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/a07b7691-f210-4197-a9a4-d23ab43372e0)

e.	Stop the ping activity

<h2>Part 3 (Observe SSH Traffic)</h2>

11.	Back in Wireshark, filter for SSH traffic only


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/8db81084-8be9-4471-8bb0-3df04c7c6a1f)


12.	From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/718f3859-67c5-4e3f-979e-3864d340a332)




a.	Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/656d5e73-9ee6-45f2-a3cd-01b2adafc192)



b.	Exit the SSH connection by typing ‘exit’ and pressing [Enter]

<h2>Part 2 (Observe DHCP Traffic)</h2>

13.	Back in Wireshark, filter for DHCP traffic only



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/443f17c3-0e5e-4d2a-a69f-bfe4a9279d1b)



14.	From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
a.	Observe the DHCP traffic appearing in WireShark


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/34c2b279-0e2d-47e8-b8c3-1ae751ef3cd4)


Part 4 (Observe DNS Traffic)</h2>

15.	Back in Wireshark, filter for DNS traffic only


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/90832a27-73ad-46e7-9de6-036d602e35ca)


16.	From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
a.	Observe the DNS traffic being show in WireShark



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/30f15665-96df-4d20-ac3a-0fe4548aacb7)



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/faf77ec3-169e-4fe9-92dd-f90b3dbd62f5)


<h2>Part 5 (Observe RDP Traffic)</h2>

17.	Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)



![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/9c1a54cf-852a-41f7-aa9a-a706a38c083c)





18.	Oserve the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
a.	Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted


![image](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/3628513b-6850-4764-b8f0-c6a7203fcafc)




<h2>Lab Cleanup (DON’T FORGET THIS)</h2>

19.	Close your Remote Desktop connection

20.	Delete the Resource Group(s) created at the beginning of this lab

21.	Verify Resource Group Deletion







![Complete-Stamp-1024x356](https://github.com/techwithterrence/azure-network-protocols/assets/174138674/50b8f661-2f15-415f-abdf-896cbc32dd4d)



