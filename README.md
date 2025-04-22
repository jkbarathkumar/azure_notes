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
