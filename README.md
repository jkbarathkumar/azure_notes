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
