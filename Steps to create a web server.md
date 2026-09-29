1. Create a resource group where all related resources can be saved. (This is like a folder where files and sub-folders can be saved)
2. Create a virtual network with one subnet. (For now, we will use just one subnet. Later, when we're comfortable, we can introduce multiple subnets, such as public and private subnets.)
   > Think of the Virtual Network (VNet) as the overall network environment. We define its address space, for example: VNet address space: 10.0.0.0/16
   > Within that VNet, we can then create smaller networks called subnets. For example: **Subnet 1**: ```10.0.1.0/24```, **Subnet 2**: ```10.0.2.0/24```, and **Subnet 3**: ```10.0.3.0/24```
3. Create a network security group. (This is like a firewall where we configure what can access our resources)
   > An Inbound rule is created to allow web access to our resources via HTTP and HTTPS. Also, SSH is allowed to enable us manage and configure the Linux VM
   <img width="1901" height="810" alt="image" src="https://github.com/user-attachments/assets/ca095296-e0f5-47bf-b220-240a03e99ac4" />   
4. Create a VM. In the network tab of our VM, we used the VNet we created earlies and for the NSG, we used the one created above <br> <img width="1085" height="867" alt="image" src="https://github.com/user-attachments/assets/ffc98965-473f-403b-a140-781c2af63527" />
      > If an error occurred during deployment. You can view the reason on why the deployment failed by going to Resource Groups > open your resources group > Click Deployments under Settings > Open: the failed deployment and click Operation details, then check the Status message <br> <img width="1906" height="721" alt="image" src="https://github.com/user-attachments/assets/ac436e1d-211e-4614-9e6f-ffc91a349d35" /> <br> <img width="1903" height="923" alt="image" src="https://github.com/user-attachments/assets/403aae3f-6778-4b6a-b708-5c6ade035bb5" />

5. VM is now deployed successfully. <br> <img width="1913" height="784" alt="image" src="https://github.com/user-attachments/assets/bade5467-431e-4a88-8f47-f45e1e29d3a6" />
6. Next we will SSH into our VM using ```ssh -i <private-key-file-path> samuelo@<publicIPAddress>``` <br> <img width="1271" height="126" alt="image" src="https://github.com/user-attachments/assets/cc49234e-a932-46b3-ba48-2e338f73734f" />
7.  Update using ```sudo apt update``` and install web server like Apache or Nginx using ```sudo apt install nginx -y``` or ```sudo apt install apache2 -y```
        - > For this VM Apache2 is used
9. Apache2 is now installed but no SSL, so we will be installing SSL in the next step <br> <img width="1724" height="1069" alt="image" src="https://github.com/user-attachments/assets/4010e60a-066a-47db-9aa5-5cb71aa37c76" />
10. To install SSL, run ```sudo apt install certbot python3-certbot-apache -y``` and ```sudo certbot apache```
11. My VM public IP is now connected to a domain name samuelo.name.ng, and SSL was install on the domain <br> <img width="1117" height="1027" alt="image" src="https://github.com/user-attachments/assets/37d84e09-633d-453e-b398-2068898e4bc0" /> <br> <img width="1628" height="1079" alt="image" src="https://github.com/user-attachments/assets/782602e5-640c-4060-bcb8-980bbaf8dd20" />


# Note for the NSG
> The source was changed from **Any** to **IP address**. This will only allow a specific IP address to SSH into the VM for security purpose
> <img width="571" height="912" alt="image" src="https://github.com/user-attachments/assets/7e851f39-66ff-4412-8daf-9206a64bc340" />


