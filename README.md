<p align="center">
<img width="335" height="150" alt="image" src="https://github.com/user-attachments/assets/bf6c6284-578a-44a2-9d99-0945a141d086" />


<h1>Building Active Directory Infrastructure in Microsoft Azure</h1>
This tutorial focuses on establishing the necessary infrastructure in Microsoft Azure for an Active Directory deployment. This includes creating the required cloud resources, configuring a virtual network, deploying virtual machines, and confirming proper network communication between systems before implementing Active Directory Domain Services.<br />

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
  
- Open in to the Azure portal.
- Locate Resource groups from the Azure services menu.
- Click Create to begin building a new resource group for the lab environment.

Explanation:
 A resource group is used to organize related Azure resources in one location. Creating it first helps keep all lab components structured and easier to manage.

<h2>Create the Resource Group</h2>

<img width="1536" height="1024" alt="Lab2" src="https://github.com/user-attachments/assets/3f6e249f-1ce2-4950-877d-8ecbc5f0b832" />
</p>
<p>
Steps:
  
- Select the appropriate Azure subscription.
- Click the resource group name Active-Directory-Lab.
- Choose the region Canada Central.
- Review the settings.
- Continue to create the resource group.

Explanation:
This creates a dedicated container for all resources used in the lab, including virtual machines and networking components.

<h2>Create the Virtual Network</h2>

<p>
<img width="1536" height="1024" alt="Lab4" src="https://github.com/user-attachments/assets/ab329317-3b3d-481a-a61c-db40ebda6689" />
</p>
<p>
Step:

- Launch Virtual networks in Azure.
- Select Create.
- Assign the network to the Active-Directory-Lab resource group.
- Enter the virtual network name Active-Directory-VNet.
- Verify the region is the same as the resource group.
- Review the default IP address space and subnet settings.
- Click Create.

Explanation:
 The virtual network allows the domain controller and client machine to communicate privately inside Azure. This is required for domain communication and DNS resolution.

<h2> Begin Creating the Domain Controller VM</h2>

<p>
  
<img width="1536" height="1024" alt="Lab5" src="https://github.com/user-attachments/assets/a45e8255-76a3-4ed1-a028-6df06d804b44" />
</p>
<p>
Steps:
  
- Open Virtual machines in Azure.
- Click Create virtual machine.
- Select the Active-Directory-Lab resource group.
- Enter the VM name dc-1.
- Select the deployment region Canada Central. (The same as the resource group)
- Review the basic configuration settings.

Explanation:
 This virtual machine is to serve as the main server for the lab. It will be promoted to a Domain Controller.

<h2>Configure dc-1 Operating System and Credentials</h2>

<p>
<img width="1536" height="1024" alt="Lab6" src="https://github.com/user-attachments/assets/bf194cfa-9233-47c5-a9bf-9a39fd46111d" />
</p>
<p>
Step:
  
- Select Windows Server 2022 Datacenter Azure Edition as the image.
- Confirm the VM architecture is set to x64.
- Select the VM size for the lab.
- Type the administrator username.
- Enter and confirm the administrator password.
- Continue through the setup wizard.

Explanation:
This step ensured that the server was deployed with a supported Windows Server operating system capable of running Active Directory Domain Services.

<h2>Configure Networking for dc-1</h2>

<p>
<img width="1536" height="1024" alt="Lab7" src="https://github.com/user-attachments/assets/b633b24b-eefb-444e-87f2-24fada2892c8" />
</p>
<p>
Steps:
  
- Open the Networking tab during the dc-1 VM creation.
- Select Active-Directory-VNet as the virtual network.
- Choose default subnet.
- Assign a public IP address for remote access.
- Set the network security group options.
- Allow RDP (3389) inbound access.
- Review the settings before deployment.

Explanation:
This placed dc-1 on the lab network and allowed it to be managed remotely through Remote Desktop.

<h2>Configure DC-1 Private IP Address</h2>

<p>
<img width="1536" height="1024" alt="Lab12" src="https://github.com/user-attachments/assets/5cb77edb-e6ae-49f2-9b3f-43e46849bb9f" />
</p>
<p>
Steps:
  
- Navigate to the Network Interface settings for the DC-1 virtual machine.
- Select IP configurations to modify the network settings.
- Open the primary IP configuration (ipconfig1).
- Change the Private IP allocation setting from Dynamic to Static.
- Confirm the assigned private IP address (10.0.0.4).
- Verify the public IP address for remote access.
- Save the configuration changes.

Explanation:
This step ensures that the DC-1 domain controller maintains a consistent private IP address, which is critical for reliable DNS services and proper communication within the Active Directory environment.


<h2>Begin Creating the Client VM</h2>

<p>
<img width="1536" height="1024" alt="Lab8" src="https://github.com/user-attachments/assets/35ffd7b1-fcb3-43fc-b62e-251070cc6e87" />
</p>
<p>
Steps:
  
- Start another Create virtual machine process.
- Select the Active-Directory-Lab resource group.
- Enter the virtual machine name Client-1.
- Chose the same region as dc-1.
- Review the basic configuration settings.

Explanation:
This machine is created to simulate a workstation that will later connect to and join the domain.

<h2>Client-1 Operating System and Credentials</h2>

<p>
<img width="1536" height="1024" alt="Lab9" src="https://github.com/user-attachments/assets/060f395e-11f0-4e5e-8134-5b30a653a064" />
</p>
<p>
Step:
  
- Select Windows 11 Pro as the image.
- Confirm the VM architecture.
- Select the VM size for the lab.
- Enter the administrator username.
- Enter and confirm the administrator password.
- Continue through the setup wizard.

Explanation:
This step varifies that the client computer is deployed with a supported Windows operating system that will later be connected to the DC-1 domain controller as part of the Active Directory environment.

<h2>Configure Networking for Client-1</h2>

<p>
<img width="1536" height="1024" alt="Lab10" src="https://github.com/user-attachments/assets/e9daa5f8-aa22-4291-92ee-c2916acd2d72" />
</p>
<p>
Step:
  
- Opened the Networking tab during the Client-1 setup.
- Selected Active-Directory-VNet.
- Keep the default subnet.
- Assign a public IP address.
- Configure the network security settings.
- Allow RDP (3389) inbound access.
- Continue with the deployment.

Explanation:
This confirms that Client-1 is on the same virtual network as dc-1 so both machines could communicate internally.

<h2>Verify Both Virtual Machines Are Running</h2>

<p>
<img width="1536" height="1024" alt="Lab13" src="https://github.com/user-attachments/assets/434dd4d7-2b83-4b28-82eb-2c5b2124019c" />
</p>
<p>
Step:
  
- Return to the Virtual machines page.
- Verify that dc-1 and Client-1 shows on the list.
- Confirm both virtual machines shows a Running status.

Explanation:
 This confirms that both systems are deployed successfully and are ready for configuration and testing.

<h2> Connect to dc-1 with Remote Desktop</h2>

<p>
<img width="1536" height="1024" alt="Lab14" src="https://github.com/user-attachments/assets/481b5ee5-596d-40b1-92cf-27926146a439" />
</p>
<p>
Step:

- Open the dc-1 virtual machine details in Azure.
- Locate the public IP address for dc-1.
- Open Remote Desktop Connection on the local computer.
- Enter the public IP address.
- Type the administrator credentials.
- Launch the remote desktop.

Explanation:
 Remote Desktop provides administrative access to the server so configuration tasks can be completed directly inside the VM.

<h2>Verify Server Manager on dc-1</h2>

<p>
<img width="1536" height="1024" alt="Lab16" src="https://github.com/user-attachments/assets/0a571eb0-7346-4b4b-a6e4-2e9fed680de2" />
</p>
<p>
Step:
  
- Sign in to dc-1 through Remote Desktop.
- Wait for the Windows Server desktop to load.
- Confirm that Server Manager opened successfully.
- Verify the server was ready for further setup.

Explanation:
 Server Manager is the main administrative tool used to install server roles and manage Windows Server services.

<h2>Adjust Windows Firewall Settings for Lab Testing</h2>

<p>
<img width="1536" height="1024" alt="Lab19" src="https://github.com/user-attachments/assets/89318695-0a7c-4dae-8979-74b88d413de3" />
</p>
<p>
Step:
  
- Open Windows Defender Firewall with Advanced Security on dc-1.
- Review the firewall profile settings.
- Adjust the firewall configuration for the lab environment.
- Confirm the changes were applied.

Explanation:
 In a lab environment, firewall settings are sometimes adjusted to make connectivity testing easier between systems. This helps avoid blocked communication during setup and troubleshooting

<h2> Begin Connectivity Testing from Client-1</h2>

<p>
<img width="1512" height="982" alt="Lab23" src="https://github.com/user-attachments/assets/a8a735b1-122a-4041-96ae-868c8b633bab" />
</p>
<p>
Step:
  
- Log into Client-1.
- Open Windows PowerShell.
- Type the following command:
  ping 10.0.0.4
- Run the command to test connectivity to the domain controller.

Explanation:
 This test checks whether the client machine can communicate with the server over the private network.

<h2>Verify Network Connectivity and DNS Settings</h2>

<p>
<img width="1536" height="1024" alt="Lab24" src="https://github.com/user-attachments/assets/5e375322-6c5a-4203-9d20-cdb9b0db998a" />
</p>
<p>
Step:
  
- Confirm that the ping to 10.0.0.4 was successful.
- Type the following command:
  ipconfig /all
- Review the network adapter details.
- Verify the client IP configuration.
- Confirm the DNS server setting pointed to 10.0.0.4.

Explanation:
 This final verification confirmed that Client-1 could communicate with dc-1 and that the DNS settings were correctly configured to point to the domain controller. That completed the infrastructure setup required before deploying Active Directory.

<h2>Summary</h2>

By the end of this phase, the Azure environment was fully prepared for the Active Directory deployment. The resource group and virtual network were created, the domain controller and client virtual machines were deployed, remote access was configured, and connectivity between systems was successfully verified. This completed the foundational infrastructure needed for the next part of the lab.





