# Project 1

## Deploying simple nginx application with firewall and bastion host in Azure

- This project sets up a secure NGINX web server in Azure using a bastion host and Azure Firewall with DNAT rules, allowing restricted browser-based access through the firewall's public IP.



1)	Created resource group
   ![image](https://github.com/user-attachments/assets/7e0247f1-6ab2-405e-9e67-1e363038fe8c)

2) Created VNet Enabling bastion host, firewall, subnets
   
   ![image](https://github.com/user-attachments/assets/fa33e3d6-1f0d-4581-9c86-f69d3b7dc6a7)
   ![image](https://github.com/user-attachments/assets/a4ffee09-2930-4711-9873-17bf4b7d04a2)
   ![image](https://github.com/user-attachments/assets/649b74a3-bd55-49c6-8a3b-9d656fbb143a)

   ![image](https://github.com/user-attachments/assets/1e434235-4ec2-4543-8461-aa14023462b4)

3) Creating Virtual Machines without Public IP
   
   ![image](https://github.com/user-attachments/assets/6f7972ac-a3e0-43e9-85d6-a2191e901ec8)
   ![image](https://github.com/user-attachments/assets/a3961cc4-322d-4f94-92e4-46898a1bac81)

4) Connect through bastion host to access VM
 
   ![image](https://github.com/user-attachments/assets/d46bb9a5-0bf5-4698-b7c2-276404dd158e)

   ![image](https://github.com/user-attachments/assets/041c8877-91b1-47fd-b183-bff4c779547b)

   Connected to VM using bastion successfully
   ![image](https://github.com/user-attachments/assets/de04f983-817f-46cf-abb6-0380a22847cc)

5) Installing and configuring custom html file at nginx in the VM
   
   ![image](https://github.com/user-attachments/assets/7a647302-07bd-40bd-bb58-8ad6a5082320)

   ![image](https://github.com/user-attachments/assets/cb51cdbc-f16e-4fd2-b0f0-98aff764e6c5)

   ![image](https://github.com/user-attachments/assets/e79dbe62-b9a4-4696-9462-5fc47df560db)

6) Configuring firewall:

   Click your project firewall
   
   ![image](https://github.com/user-attachments/assets/73bea29f-bc45-4b89-aa4c-be1c6573dc8e)

   Click Firewall policy:

   ![image](https://github.com/user-attachments/assets/01b95de7-82cb-4412-80e3-ea3a2004035a)

   Add rule collection inside DNAT Rules:

   ![image](https://github.com/user-attachments/assets/a989f904-04bb-4bad-b776-3334f4833d1b)

   Click add rule under under DNAT rules:

   ![image](https://github.com/user-attachments/assets/b86937eb-dbc4-4d1d-865c-39ecb209b67c)

   ![image](https://github.com/user-attachments/assets/240faec9-9e98-4a1d-9f73-a4faa0a2d8f5)


   - Here Source IP address is my browser IP because only allowing my browser to access the application.
   - Destination IP address is firewall Public IP.
   - Destination port you can use any port through that port only you gonna access the application.
   - Translated Address is VM's private IP
   - Translated Port is nginx configured on the VM at port 80



7) Add inbound rule in NSG:

   ![image](https://github.com/user-attachments/assets/c5e3481f-7884-4b14-81c1-f68b10ed1c15)

8) Accessing the application through firewall public IP:

   ![image](https://github.com/user-attachments/assets/dcdd1a9a-d4e7-454f-9ccd-5c85c73fcf45)

   



   
