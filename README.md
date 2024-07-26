# Configuring and Implementing a Honeypot in Azure

![Banner](https)

To start the Azure Honeynet project, the first step is to set up the virtual machines (VMs) that will be used. These virtual machines, which function as cloud-based computers, will form the core of our honeynet. Here’s how we’ll proceed in Microsoft Azure:

1. Sign in to the Azure portal: If you don't have an account yet, **[you'll need to create one!](https://portal.azure.com)**

<details close> 
<summary> 2. Create a virtual machine: </summary>

- In the Azure portal, proceed to the 'Virtual machines' section.. 
  
  ![azure portal](https://github.com)

  
- Click on 'Create', then 'Virtual machine'. This is where we'll set up our new VM!
 
  ![VM create](https://github.com)
  
  </details>
  
  
  <details close> 
<summary> 3. Configure the VM settings: </summary>
  
  - **Subscription and resource group:** We'll select our Azure subscription and resource group (Which is way to group and manage resources in Azure!). For the purpose of the project, I already created a resource group called ```RG-Cyber-Lab``` 
  
  - **Virtual Machine Name:** For the purpose of this project, I named mine, ```Lab-HoneyNet```

  - **Region:** For the purpose of this project, I chose the region, ```(US) East US 2```
  
  - **Availability Options:** Since the sole purpose of this machine is to serve as a honeypot, there is no need for availability features. Therefore, select ```No infrastructure redundancy required```

  - **Image:** Select ```Windows 10 Pro, version 21H2 - x64 Gen2```
  
  ![VM create](https://github.com)
  
  - **Networking**: When setting up the virtual network, we will use the default settings. For this lab, I named mine ```Lab-VNet```.
  
  ![netowork](https://github.com)


  </details>


<details close> 
<summary> 4. NSG/Inbound Security Rule Configuration: </summary>
 
  - **Access the Network Security Group (NSG):** In the Azure portal, use the search bar at the top to find 'Network Security Groups'. Select the NSG associated with your virtual machine.
  
  - **Create an inbound security rule:**  Within the NSG, locate the 'Inbound security rules' section, where you can manage the traffic allowed to reach your VM. Click on 'Add' to set up a new rule.
    
  - **Configure the rule:** You’ll need to enter specific details for the new rule.
  
  - **Source:** This specifies the origin of the incoming traffic. Set this to ```Any``` to permit traffic from all locations.
  
  - **Source port ranges:** This defines the ports on the source (the initiating computer) that are allowed. Set this to ```*``` or ```Any``` to allow all ports.

  - **Destination:** This indicates where the traffic is headed. Set this to ```Any``` to direct traffic to your VM.
  
  - **Destination port ranges:** : This specifies the ports on your VM that can receive traffic. Set this to ```*``` or ```Any``` to open all ports.
  
  - **Priority:** Assigning priorities in Network Security Groups (NSGs) is crucial as it dictates the order in which rules are applied. Rules with lower priority numbers are processed before those with higher numbers. For this lab, set the priority to ```300``` to ensure the honeypot operates as intended.

  - **Action:** Set this to ```Allow```, which will permit traffic matching this rule to reach your VM.
  
 ![NSG](https://github.com/)

  
  - **Review & Create:** After configuring all the necessary details for the inbound rule, click 'Add' to finalize the rule creation.
 
 
</details>

# Conclusion

By setting up our VMs and allowing unrestricted inbound security rules, we're essentially leaving the front door of our VM wide open. Normally, this would be highly risky and not advisable in a production environment due to the increased vulnerability to attacks. However, for our honeynet, this is precisely the goal!

This approach helps us attract potential attackers and monitor their activities within a controlled setting.
 
