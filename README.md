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

- Windows Server 2022 (Datacenter Azure Edition Hotpatch-x64 Gen2)
- Windows 11 Pro (Version 25H2-x64)
  

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

<h2>Configure DC-1 Private IP Address</h2>

<p>
<img width="1536" height="1024" alt="Lab12" src="https://github.com/user-attachments/assets/5cb77edb-e6ae-49f2-9b3f-43e46849bb9f" />
</p>
<p>
Steps:
  
- Navigated to the Network Interface settings for the DC-1 virtual machine.
- Selected IP configurations to modify the network settings.
- Opened the primary IP configuration (ipconfig1).
- Changed the Private IP allocation setting from Dynamic to Static.
- Verified the assigned private IP address (10.0.0.4).
- Confirmed the public IP address association for remote access.
- Saved the configuration changes.

Explanation:
This step ensures that the DC-1 domain controller maintains a consistent private IP address, which is critical for reliable DNS services and proper communication within the Active Directory environment.


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

<h2>Client-1 Operating System and Credentials</h2>

<p>
<img width="1536" height="1024" alt="Lab9" src="https://github.com/user-attachments/assets/060f395e-11f0-4e5e-8134-5b30a653a064" />
</p>
<p>
Step:
  
- Selected Windows 11 Pro as the image.
- Confirmed the VM architecture.
- Selected the VM size for the lab.
- Entered the administrator username.
- Entered and confirmed the administrator password.
- Continued through the setup wizard.

Explanation:
This step ensured that the client computer was deployed with a supported Windows operating system that will later be connected to the DC-1 domain controller as part of the Active Directory environment.

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

<h2>Verify Both Virtual Machines Are Running</h2>

<p>
<img width="1536" height="1024" alt="Lab13" src="https://github.com/user-attachments/assets/434dd4d7-2b83-4b28-82eb-2c5b2124019c" />
</p>
<p>
Step:
  
- Returned to the Virtual machines page.
- Verified that dc-1 and Client-1 appeared in the list.
- Confirmed both virtual machines showed a Running status.

Explanation:
 This confirmed that both systems were deployed successfully and were ready for configuration and testing.

<h2> Connect to dc-1 with Remote Desktop</h2>

<p>
<img width="1536" height="1024" alt="Lab14" src="https://github.com/user-attachments/assets/481b5ee5-596d-40b1-92cf-27926146a439" />
</p>
<p>
Step:

- Opened the dc-1 virtual machine details in Azure.
- Located the public IP address for dc-1.
- Opened Remote Desktop Connection on the local computer.
- Entered the public IP address.
- Entered the administrator credentials.
- Started the remote session.

Explanation:
 Remote Desktop provides administrative access to the server so configuration tasks can be completed directly inside the VM.

<h2>Verify Server Manager on dc-1</h2>

<p>
<img width="1536" height="1024" alt="Lab16" src="https://github.com/user-attachments/assets/0a571eb0-7346-4b4b-a6e4-2e9fed680de2" />
</p>
<p>
Step:
  
- Signed in to dc-1 through Remote Desktop.
- Waited for the Windows Server desktop to load.
- Confirmed that Server Manager opened successfully.
- Verified the server was ready for further setup.

Explanation:
 Server Manager is the main administrative tool used to install server roles and manage Windows Server services.

<h2>Adjust Windows Firewall Settings for Lab Testing</h2>

<p>
<img width="1536" height="1024" alt="Lab19" src="https://github.com/user-attachments/assets/89318695-0a7c-4dae-8979-74b88d413de3" />
</p>
<p>
Step-by-step
  
- Opened Windows Defender Firewall with Advanced Security on dc-1.
- Reviewed the firewall profile settings.
- Adjusted the firewall configuration for the lab environment.
- Confirmed the changes were applied.

Explanation:
 In a lab environment, firewall settings are sometimes adjusted to make connectivity testing easier between systems. This helps avoid blocked communication during setup and troubleshooting

</p>
<br />

<h2> Begin Connectivity Testing from Client-1</h2>

<p>
<img width="1512" height="982" alt="Lab23" src="https://github.com/user-attachments/assets/a8a735b1-122a-4041-96ae-868c8b633bab" />
</p>
<p>
Step:
  
- Logged into Client-1.
- Opened Windows PowerShell.
- Entered the following command:
  ping 10.0.0.4
- Ran the command to test connectivity to the domain controller.

Explanation:
 This test checks whether the client machine can communicate with the server over the private network.

</p>
<br />

<h2>Verify Network Connectivity and DNS Settings</h2>

<p>
<img width="1536" height="1024" alt="Lab24" src="https://github.com/user-attachments/assets/5e375322-6c5a-4203-9d20-cdb9b0db998a" />
</p>
<p>
Step:
  
- Confirmed that the ping to 10.0.0.4 was successful.
- Entered the following command:
  ipconfig /all
- Reviewed the network adapter details.
- Verified the client IP configuration.
- Confirmed the DNS server setting pointed to 10.0.0.4.

Explanation:
 This final verification confirmed that Client-1 could communicate with dc-1 and that the DNS settings were correctly configured to point to the domain controller. That completed the infrastructure setup required before deploying Active Directory.

<h2>Summary</h2>

By the end of this phase, the Azure environment was fully prepared for the Active Directory deployment. The resource group and virtual network were created, the domain controller and client virtual machines were deployed, remote access was configured, and connectivity between systems was successfully verified. This completed the foundational infrastructure needed for the next part of the lab.





