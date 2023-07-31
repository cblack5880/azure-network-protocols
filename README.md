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

I switched back to client 1 and opened DC-1 network folder. As you can see, The user doesnt have access to the "no-access" folder, because its not an admin.

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/341ed22c-5987-4ddb-814e-987d3131e9a2)

This user also doesn't have the ability to create a .txt file because its a "read access" only folder

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/d25d702f-71bd-450c-891a-ed9fd26d08ef)

I was able to create a file in the "write-access" folder.

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/39f48a74-ad30-4fd5-bb9f-0c0f973a5c5a)

I will now create a security group folder in DC-1/ Active Directory. From there, I will create the "accountants" folder.

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/b1d83103-cac9-4a6c-981f-41ba7d6b4091)


On the “accounting” folder I created earlier, I will set the following permissions:
Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”

![image](https://github.com/cblack5880/azure-network-protocols/assets/138612466/a1437521-b266-4494-bb86-5b0e47936b52)





# azure-network-protocols
