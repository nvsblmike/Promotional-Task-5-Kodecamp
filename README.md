# Setting Up a VPC in AWS

## Step 1: Creating the VPC
- I navigated to the VPC Dashboard after opening the AWS management console.
- I clicked on create VPC. I then named it KCVPC. I left the values as default as seen in the screenshot.

## Step 2: Creating Subnets
- In the VPC Dashboard, I went to Subnets.
- I clicked on Create subnet and named it PublicSubnet.
- I set the IPv4 CIDR block to 10.0.1.0/24.
- I clicked on Create subnet again and named it PrivateSubnet.
- I set the IPv4 CIDR block to 10.0.2.0/24.

## Step 3: Configuring an Internet Gateway (IGW)
- In the VPC Dashboard, I clicked on "Internet Gateways" to create an internet gateway.
- I named it KCVPC-IGW and attached it to the KCVPC VPC.

## Step 4: Configuring Route Tables
- In the VPC Dashboard, I clicked on "Route Tables" to create a route table.
- I named it PublicRouteTable.
- I edited the routes to make it attached to the IGW just created.
- I then associated the public subnet with PublicRouteTable.
- I also created a route table for the private subnet and associated it as I did for the public subnet.

## Step 5: Configuring the NAT Gateway
- In the VPC Dashboard, I clicked on "NAT Gateways" to create a NAT gateway.
- I selected the PublicSubnet and allocated a new Elastic IP.
- I also updated the PrivateRouteTable by adding destination - 0.0.0.0/0 and selecting NAT Gateway as target.

## Step 6: Setting Up Security Groups
- In the VPC Dashboard, I clicked on "Security Groups" to create a security group.
- I named it PublicSecurityGroup.
- I set the inbound and outbound rules as stated in the instructions. Please see in the screenshot.
- I also set up security group for private instances.

## Step 7: Configuring Network ACLs
- In the VPC Dashboard, I clicked on "Network ACLs" to create a network ACL.
- I created for both the private and public subnets.

## Step 8: Launching an EC2 Instance in Public Subnet
- I went to the EC2 Dashboard and clicked on launch instance.
- I named it PublicInstance.
- I created same for PrivateInstance.

### Purpose and Function of Each Component

- **VPC (Virtual Private Cloud)**: A logically isolated network within the AWS cloud where you can launch AWS resources.
- **Subnets**: Sub-divisions within a VPC to group resources based on security and operational needs. Public subnets have direct access to the internet, while private subnets do not.
- **Internet Gateway (IGW)**: A gateway that allows communication between resources in your VPC and the internet.
- **Route Tables**: Tables that define how traffic is directed within the VPC. The public route table routes traffic to the IGW, while the private route table routes traffic through the NAT Gateway.
- **NAT Gateway**: A gateway that allows instances in a private subnet to connect to the internet while preventing the internet from initiating connections with those instances.
- **Security Groups**: Virtual firewalls for instances to control inbound and outbound traffic.
- **Network ACLs (Access Control Lists)**: Additional layer of security at the subnet level to control inbound and outbound traffic.

## Screenshots
Screenshots for each step can be found [here](https://docs.google.com/document/d/149ULfyAiB0FIpdxClxw1hQI8V9YhDat_KuhNotjQemY/edit?usp=sharing).

---

