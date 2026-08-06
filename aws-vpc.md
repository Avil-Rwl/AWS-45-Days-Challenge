 AWS VPC Networking & Public EC2 Deployment

Designed and implemented a custom AWS Virtual Private Cloud (VPC) from scratch to understand AWS networking fundamentals. Configured Public and Private Subnets, Internet Gateway, Route Table, and launched an EC2 instance inside the Public Subnet with internet connectivity.


 Architecture & Implementation Steps

 Step 1: Create Custom VPC

 Created a Custom VPC named my-aws-vpc
 Selected IPv4 CIDR Block
 Configured CIDR Range:


10.0.0.0/16




 Step 2: Create Public & Private Subnets

Created two subnets inside the VPC.

 Public Subnet


10.0.1.0/24


 Private Subnet


10.0.2.0/24


Both subnets were created in the same Availability Zone.



 Step 3: Internet Gateway Configuration

 Created an Internet Gateway (IGW)
 Attached the Internet Gateway to the Custom VPC

This enables internet connectivity for resources placed inside Public Subnets.



 Step 4: Route Table Configuration

Created a Custom Route Table.

Added the following route:

| Destination | Target |
|-------------|---------|
| 0.0.0.0/0 | Internet Gateway |

Associated the Route Table with the Public Subnet.



 Step 5: Launch Public EC2 Instance

Launched an EC2 Instance inside the Public Subnet.

Configuration:

 Custom VPC
 Public Subnet
 Auto Assign Public IP Enabled
 Security Group Configured

Allowed Ports:

 SSH (22)
 HTTP (80)
 HTTPS (443)



 Step 6: Connectivity Verification

Connected to the EC2 Instance using SSH.

Verified internet connectivity by updating system packages.

Installed Nginx Web Server.

Verified successful deployment by accessing the EC2 Public IP in a web browser.



 
 Project Verification

Successfully verified:

 Custom VPC Creation
 Public & Private Subnet Configuration
 Internet Gateway Attachment
 Route Table Association
 Public EC2 Deployment
 SSH Connectivity
 Internet Access
 Nginx Installation
 Web Server Accessible via Public IP


