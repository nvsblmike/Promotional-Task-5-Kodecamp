# Setting Up a VPC in AWS

## Step 1: Creating the VPC
- I navigated to the VPC Dashboard after opening the AWS management console.
- I clicked on create VPC. I then named it KCVPC. I left the values as default as seen in the screenshot.

  ![image](https://github.com/user-attachments/assets/5421b239-a931-43fc-b775-b8713f8555e3)

## Step 2: Creating Subnets
- In the VPC Dashboard, I went to Subnets.
- I clicked on Create subnet and named it PublicSubnet.
- I set the IPv4 CIDR block to 10.0.1.0/24.
- I clicked on Create subnet again and named it PrivateSubnet.
- I set the IPv4 CIDR block to 10.0.2.0/24.
  ![image](https://github.com/user-attachments/assets/b8361f7e-5427-4067-abdd-150ad4b5d646)


## Step 3: Configuring an Internet Gateway (IGW)
- In the VPC Dashboard, I clicked on "Internet Gateways" to create an internet gateway.
- I named it KCVPC-IGW and attached it to the KCVPC VPC.

   ![image](https://github.com/user-attachments/assets/83933153-3035-4085-a81a-acb0e00c5a74)

## Step 4: Configuring Route Tables
- In the VPC Dashboard, I clicked on "Route Tables" to create a route table.
- I named it PublicRouteTable.
- I edited the routes to make it attached to the IGW just created.
- I then associated the public subnet with PublicRouteTable.
- I also created a route table for the private subnet and associated it as I did for the public subnet.
  ![image](https://github.com/user-attachments/assets/ce80df0d-03c5-406f-ac3e-e15aa2bae486)
  ![image](https://github.com/user-attachments/assets/cc6e9d3d-aec3-47eb-b81f-825a222c2201)



## Step 5: Configuring the NAT Gateway
- In the VPC Dashboard, I clicked on "NAT Gateways" to create a NAT gateway.
- I selected the PublicSubnet and allocated a new Elastic IP.
- I also updated the PrivateRouteTable by adding destination - 0.0.0.0/0 and selecting NAT Gateway as target.
  ![image](https://github.com/user-attachments/assets/ceeccfe2-4621-4deb-84c2-3c683d0f3ddd)


## Step 6: Setting Up Security Groups
- In the VPC Dashboard, I clicked on "Security Groups" to create a security group.
- I named it PublicSecurityGroup.
- I set the inbound and outbound rules as stated in the instructions. Please see in the screenshot.
- I also set up security group for private instances.
  ![image](https://github.com/user-attachments/assets/914bc738-a483-4b0b-a1f9-144e3484453e)
  ![image](https://github.com/user-attachments/assets/d13408fb-0743-4a3a-ac54-792635722354)



## Step 7: Configuring Network ACLs
- In the VPC Dashboard, I clicked on "Network ACLs" to create a network ACL.
- I created for both the private and public subnets.
  ![image](https://github.com/user-attachments/assets/55a155a2-ba9c-4fbf-a7af-4b2537e1089b)
  ![image](https://github.com/user-attachments/assets/18457347-683b-4915-93d3-0d560b6eefc4)
![image](https://github.com/user-attachments/assets/5d5d3665-0801-4317-be8c-c72250460844)


## Step 8: Launching an EC2 Instance in Public Subnet
- I went to the EC2 Dashboard and clicked on launch instance.
- I named it PublicInstance.
- I created same for PrivateInstance.

![image](https://github.com/user-attachments/assets/61171ccf-c087-4911-85d0-a61b18c39e5b)

## Architectural Diagram
![image](https://github.com/user-attachments/assets/6c42167e-e799-46f6-8d68-1871831d39fb)



### Purpose and Function of Each Component

- **VPC (Virtual Private Cloud)**: A logically isolated network within the AWS cloud where you can launch AWS resources.
- **Subnets**: Sub-divisions within a VPC to group resources based on security and operational needs. Public subnets have direct access to the internet, while private subnets do not.
- **Internet Gateway (IGW)**: A gateway that allows communication between resources in your VPC and the internet.
- **Route Tables**: Tables that define how traffic is directed within the VPC. The public route table routes traffic to the IGW, while the private route table routes traffic through the NAT Gateway.
- **NAT Gateway**: A gateway that allows instances in a private subnet to connect to the internet while preventing the internet from initiating connections with those instances.
- **Security Groups**: Virtual firewalls for instances to control inbound and outbound traffic.
- **Network ACLs (Access Control Lists)**: Additional layer of security at the subnet level to control inbound and outbound traffic.

## Screenshots
Screenshots for each step and the VPC Architectural Diagram can be found [here](https://docs.google.com/document/d/149ULfyAiB0FIpdxClxw1hQI8V9YhDat_KuhNotjQemY/edit?usp=sharing).

---

