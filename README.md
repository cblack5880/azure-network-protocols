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
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create some sample file shares with various permissions
- Attempt to access file shares as a normal user
- Create an “ACCOUNTANTS” Security Group, assign permissions, and test access
  
<h2>Actions and Observations</h2>

First, I will pick a login to use from the DC-1 active directory. These users are in the _EMPLOYEES section.

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/74e8d516-a60e-45d9-b881-fd08d0a37354)

On DC-1, on the C:\ drive, I created 4 folders: “read-access”, “write-access”, “no-access”, and “accounting”.

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/8c528e54-418e-4cb5-9437-b64de5232c61)

From here, I will be setting the permissions to these folders:
Set the following permissions (share the folder) for the “Domain Users” group:

Folder: “read-access”, Group: “Domain Users”, Permission: “Read”

Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”

Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”

This shows the setup for the "Read Access" folder

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/a78abe1f-f982-418f-aac6-de9c1018e1b3)

Write Access will have read and write.
The "No Access" folder will be reserved for the Domain Admins 

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/db5893b5-5ef0-436a-9ccc-81af5514953e)




# azure-network-protocols
