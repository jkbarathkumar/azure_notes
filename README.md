### Azure notes

### Deployment models
- Public cloud
It is a cloud computing environment where the **services** and **infrastructure** are provided by **third-party vendors** (like Amazon Web Services, Microsoft Azure, Google Cloud, etc.) and are made available to the general public.
> -   **Multi-tenant**: Multiple organizations share the same infrastructure.
> - **Scalable**: Easy to scale up or down depending on demand.
>  - **Cost-effective**: No need for businesses to own or maintain physical hardware.
> -   **Managed by providers**: Maintenance, updates, and security are handled by the cloud provider.


- Private cloud
A private cloud is a cloud computing environment that is exclusively used by one organization. 
It may be hosted on-premises or by a third-party provider but the infrastructure is dedicated to that single organization.
> -   **Single-tenant**: Only one organization uses the resources.  
>-   **More control**: Organizations have full control over the infrastructure, including security and privacy.  
>-   **Customization**: Can be tailored to meet the specific needs of the organization.
>-   **More costly**: Requires investment in hardware and resources or higher service fees if hosted by a provider.
- Hybrid cloud
A Hybrid Cloud is a type of cloud computing environment that combines **on-premises infrastructure** (private cloud or traditional data centers) with **public cloud resources** (like AWS, Azure, Google Cloud).
 It allows data and applications to be shared between the two environments, providing greater flexibility and deployment options.
 > -   **How It Works**: A hybrid cloud setup typically involves connecting your private on-premises network or data center with a public cloud. This can be done through a variety of connectivity options, such as **VPNs**, **dedicated links** (e.g., **AWS Direct Connect** or **Azure ExpressRoute**), or **VNet Peering** in some cases.

-   **Flexibility** to choose where to run applications and store data (on-premises or in the cloud).
-   **Seamless integration** between private and public cloud environments.
-   **Secure communication** between on-premises systems and cloud systems (often using VPNs, Direct Connect, or ExpressRoute).    
-   Allows organizations to gradually move to the cloud without fully migrating all their infrastructure.




#### VNet
- It is a private, isolated network in the cloud that allows you to securely connect different resources such as virtual machines, databases, and other services within a specific environment.
- **Connectivity**:
	- **Subnets**: You can create multiple subnets to organize resources based on their roles, security requirements, or other factors.
	-   **Peering**: Virtual networks can be connected with each other via VNet Peering, allowing resources in different VNets to communicate securely.
	-   **VPN Gateway**: If you want to connect your on-premises network to the VNet, you can use a VPN Gateway to establish a secure connection over the internet.
-    **Security**: VNets are integrated with Azure's security features, such as Network Security Groups (NSGs) and Azure Firewall, to control the flow of traffic in and out of the network. You can define rules based on IP addresses, ports, and protocols.
-   **Public and Private Endpoints**: Azure allows you to define private IP addresses for resources in the VNet, but you can also expose certain resources to the public internet using public IPs or load balancers.
	- ### Example:
	- Imagine you're deploying a multi-tier web application in a cloud environment:
		-   You might have a **public subnet** for web servers that need to be accessed over the internet.
		-   You could place **database servers** in a **private subnet** that are not directly accessible from the outside world.
		-   The resources in these subnets can communicate with each other over the private VNet network, providing secure and efficient interaction without exposing sensitive services like databases to the public internet.



#### Bastion
- It acts as a **secure gateway** to access other servers or resources within a private network. 
- It's typically used to provide controlled access to **internal systems** in a **private subnet** from an **external network** (such as the internet), while minimizing exposure to security risks.
### How a Bastion Host Works:

-   **External Access**: The Bastion Host is placed in a **public subnet** (accessible from the internet) while the resources it provides access to (like web servers, databases, etc.) are placed in **private subnets** (not accessible from the internet).
    
-   **Secure Access Method**: Users or administrators connect to the Bastion Host first, and once connected, they can access other internal servers and resources through secure means (SSH, RDP, etc.).
    

#### Example Flow:

1.  A user wants to access a private server within a cloud network.
    
2.  The user first connects to the **Bastion Host** via SSH (for Linux) or RDP (for Windows), using strong authentication (e.g., a public-private key pair or multi-factor authentication).
    
3.  Once connected to the Bastion Host, the user can then **SSH or RDP** into the private server (behind the Bastion Host) without that server being directly exposed to the public internet.



### Availability Set
 - An **Availability Set** in Azure is a `grouping of virtual machines (VMs)` designed to ensure `high availability` by distributing them across different `fault and update domains`.
 - It protects your app from `downtime` due to hardware failures or planned maintenance.
### Scale sets
- Create and manages a group of load balancer VMs.
- Supports manual scaling and Auto Scaling










##Create VNet,VMs and NSG
### Vnet
![image](https://github.com/user-attachments/assets/34509d1c-5e1b-4f47-9260-188b82068f7a)


### Three subnets
![image](https://github.com/user-attachments/assets/788ebb0b-4ff7-4e70-b765-74924295df21)
![image](https://github.com/user-attachments/assets/e7ae9653-d74e-407a-92fb-6a50ace14530)
![image](https://github.com/user-attachments/assets/fa9b4788-bb77-4dc1-be14-ab32fa1bb0fa)
![image](https://github.com/user-attachments/assets/b954b7af-915c-47ff-b660-f28595c2a901)


### Three VM's
![image](https://github.com/user-attachments/assets/a8de9905-303a-4b4b-a87b-e515f0e2968a)

### NSG

For private
![image](https://github.com/user-attachments/assets/a33885dd-cd1f-46bd-a9a0-1a51a991d9c8)

For public
![image](https://github.com/user-attachments/assets/56eb77ba-abbe-4717-8115-55120489ce1a)






Hierarchy of Scope Levels in Azure
Azure has a structured hierarchy for organizing and managing access. From the broadest to the most specific, the levels are:

🔹 1. Tenant Level (Directory-Level)
Also called: Azure Active Directory (AAD) level

What it is: The overall identity and directory level that contains users, groups, domains, and policies.

Roles here:

Global Administrator

User Administrator

Security Reader, etc.

Applies to: Entire directory and identity-related resources

Portal navigation: Azure Active Directory (not part of resource groups)

🔹 2. Management Group
What it is: A way to organize multiple subscriptions under a single hierarchy (for large orgs).

Roles here: RBAC roles like Owner, Reader, etc.

Use case: Apply policies, role assignments, or budgets across multiple subscriptions.

Example: Assign a policy to enforce tagging rules on all subscriptions under a business unit.

🔹 3. Subscription Level
What it is: A container for billing, services, and deployed resources.

Roles here: RBAC roles (Owner, Contributor, Reader) affect all resources in the subscription.

Use case: Control who can deploy or manage resources in a specific subscription.

🔹 4. Resource Group Level
What it is: A logical container for grouping related resources (VMs, storage, network).

Roles here: Apply to all resources inside the group.

Use case: Give a team access to manage only a particular application’s resources.

🔹 5. Resource Level
What it is: Individual Azure services (e.g., a specific VM, storage account).

Roles here: Very granular control (e.g., only give access to one VM).

Use case: Least privilege access to specific items.

![image](https://github.com/user-attachments/assets/67251105-9a12-4ce6-aa33-1980d9dfc3fc)






