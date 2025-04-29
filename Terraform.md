## Terraform(IaC Tool) using Azure
### Terraform basics
- To automate and manage your infrastructure, your platform and services that run on that platform.
- Tool for infrastructure provisioning
  
🔧 `Purpose`
Terraform: Builds and provisions infrastructure (servers, networks, cloud resources).
Ansible: Configures and manages software and settings on infrastructure.

⚙️ `How They Work`
Terraform: Uses declarative language (you describe the desired state).
Ansible: Mostly procedural (you write the steps to reach the state).

🔁 `State Management`
Terraform: Maintains a state file to track resources.
Ansible: Stateless; it checks the current state during each run.

☁️ `Use Cases`
Terraform: Ideal for cloud provisioning (AWS, Azure, GCP).
Ansible: Best for configuration management (installing packages, setting configs).

![image](https://github.com/user-attachments/assets/8784567f-6f62-47b2-bb1c-3e836dc8ac90)


### Terraform files
- State File (terraform.tfstate)
 - The state file is crucial for tracking the current state of your infrastructure. Terraform maintains a record of all the resources it manages in this file. It is automatically generated and updated as Terraform applies changes to the infrastructure.

### Terraform basic commands
- **`terraform init`**    - Initializes the Terraform working directory.
  ![image](https://github.com/user-attachments/assets/f49caf21-7453-4701-a8bc-d214072ceda2)

- **`terraform plan`** - Creates an execution plan (dry run).
	-    **Created**: Resources that don’t exist yet, according to the configuration, are marked as `+ create`.
        
    -   **Updated**: Resources that need changes are marked as `~ update`.
        
    -   **Destroyed**: Resources that are no longer in the configuration are marked as `- destroy`.
      ![image](https://github.com/user-attachments/assets/925e1f28-dac5-4806-9c8c-0f9bf61da320)

- **`terraform apply`**: Applies the changes to your infrastructure.
![image](https://github.com/user-attachments/assets/4aebbe15-10b9-46e2-bb22-7e129a74d6b2)

- **`terraform destroy`**: -   Destroys all resources defined in your configuration.
![image](https://github.com/user-attachments/assets/2c6c0ab2-4f99-47c6-9f24-3d5b66ffe2df)

- **`terraform fmt`** -   Formats the Terraform configuration files to standardize them.
![image](https://github.com/user-attachments/assets/93e0eda2-73a5-4f9b-9443-33e434a1328a)

- **`terraform validate`** - Validates the syntax of the configuration files

![image](https://github.com/user-attachments/assets/7737d259-e0d2-4490-8a2f-16a3bc2043a8)

- **`terraform show`**  - Displays the Infrastructure
![image](https://github.com/user-attachments/assets/fc5a16ec-f926-4d2d-9acd-4eba77763cba)

