<p align="center">
<img width="270" height="187" alt="image" src="https://github.com/user-attachments/assets/c3457b89-c543-4076-9b48-f19872a657e8" />

<h1>Building Active Directory Infrastructure in Microsoft Azure</h1>
This tutorial focused on establishing the necessary infrastructure in Microsoft Azure for an Active Directory deployment. This included creating the required cloud resources, configuring a virtual network, deploying virtual machines, and confirming proper network communication between systems before implementing Active Directory Domain Services.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Azure Virtual Network
- Azure Resource Groups
- Remote Desktop Protocol (RDP)
- DNS

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 Pro
  

<h2>Open Resource Groups in Azure</h2>

<img width="1536" height="1024" alt="Lab1" src="https://github.com/user-attachments/assets/dd1f9fed-7847-4542-b265-1f1e0406da9c" />
</p>
<p>
Steps:
  
- Sign in to the Azure portal.
- Locate Resource groups from the Azure services menu.
- Select Create to begin building a new resource group for the lab environment.

Explanation:
 A resource group is used to organize related Azure resources in one location. Creating it first helps keep all lab components structured and easier to manage.

<h2>Create the Resource Group</h2>

<img width="1536" height="1024" alt="Lab2" src="https://github.com/user-attachments/assets/3f6e249f-1ce2-4950-877d-8ecbc5f0b832" />
</p>
<p>
Steps:
  
- Selected the appropriate Azure subscription.
- Entered the resource group name Active-Directory-Lab.
- Chose the region Canada Central.
- Reviewed the settings.
- Continued to create the resource group.

Explanation:
This created a dedicated container for all resources used in the lab, including virtual machines and networking components.

<h2>Create the Virtual Network</h2>

<p>
<img width="1536" height="1024" alt="Lab4" src="https://github.com/user-attachments/assets/ab329317-3b3d-481a-a61c-db40ebda6689" />
</p>
<p>
Step:

- Opened Virtual networks in Azure.
- Selected Create.
- Assigned the network to the Active-Directory-Lab resource group.
- Entered the virtual network name Active-Directory-VNet.
- Confirmed the region matched the resource group.
- Reviewed the default IP address space and subnet settings.
- Clicked Create.

Explanation:
 The virtual network allows the domain controller and client machine to communicate privately inside Azure. This is required for domain communication and DNS resolution.

<h2> Begin Creating the Domain Controller VM</h2>

<p>
  
<img width="1536" height="1024" alt="Lab5" src="https://github.com/user-attachments/assets/a45e8255-76a3-4ed1-a028-6df06d804b44" />
</p>
<p>
Steps:
  
- Opened Virtual machines in Azure.
- Clicked Create virtual machine.
- Selected the Active-Directory-Lab resource group.
- Entered the VM name dc-1.
- Selected the deployment region.
- Reviewed the basic configuration settings.

Explanation:
 This virtual machine was created to serve as the main server for the lab. It would later be promoted to a Domain Controller.

<h2>Configure dc-1 Operating System and Credentials</h2>

<p>
<img width="1536" height="1024" alt="Lab6" src="https://github.com/user-attachments/assets/bf194cfa-9233-47c5-a9bf-9a39fd46111d" />
</p>
<p>
Step:
  
- Selected Windows Server 2022 Datacenter Azure Edition as the image.
- Confirmed the VM architecture.
- Selected the VM size for the lab.
- Entered the administrator username.
- Entered and confirmed the administrator password.
- Continued through the setup wizard.

Explanation:
This step ensured that the server was deployed with a supported Windows Server operating system capable of running Active Directory Domain Services.

<h2>Configure Networking for dc-1</h2>

<p>
<img width="1536" height="1024" alt="Lab7" src="https://github.com/user-attachments/assets/b633b24b-eefb-444e-87f2-24fada2892c8" />
</p>
<p>
Steps:
  
- Opened the Networking tab during the dc-1 VM creation.
- Selected Active-Directory-VNet as the virtual network.
- Kept the default subnet.
- Assigned a public IP address for remote access.
- Set the network security group options.
- Allowed RDP (3389) inbound access.
- Reviewed the settings before deployment.

Explanation:
This placed dc-1 on the lab network and allowed it to be managed remotely through Remote Desktop.

<h2>Begin Creating the Client VM</h2>

<p>
<img width="1536" height="1024" alt="Lab8" src="https://github.com/user-attachments/assets/35ffd7b1-fcb3-43fc-b62e-251070cc6e87" />
</p>
<p>
Steps:
  
- Started another Create virtual machine process.
- Selected the Active-Directory-Lab resource group.
- Entered the virtual machine name Client-1.
- Chose the same region as dc-1.
- Reviewed the basic configuration settings.

Explanation:
This machine was created to simulate a workstation that would later connect to and join the domain.

<h2>Configure Networking for Client-1</h2>

<p>
<img width="1536" height="1024" alt="Lab10" src="https://github.com/user-attachments/assets/e9daa5f8-aa22-4291-92ee-c2916acd2d72" />
</p>
<p>
Step:
  
- Opened the Networking tab during the Client-1 setup.
- Selected Active-Directory-VNet.
- Kept the default subnet.
- Assigned a public IP address.
- Configured the network security settings.
- Allowed RDP (3389) inbound access.
- Continued with the deployment.

Explanation:
This ensured that Client-1 was on the same virtual network as dc-1 so both machines could communicate internally.



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




