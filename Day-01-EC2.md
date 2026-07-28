 Day 01: Deploying Apache Web Server on AWS EC2

 Objective
Launch an Amazon Linux 2023 EC2 instance, configure network security rules for HTTP access, and deploy a custom web server using Apache (`httpd`).

---

 Architecture & Configuration
Cloud Provider:** Amazon Web Services (AWS)
Compute Service:** EC2 (`t2.micro` - Free Tier)
OS / AMI:** Amazon Linux 2023
Access Method:** EC2 Instance Connect (Web Browser Terminal)
  Networking:** Public Subnet with Auto-assigned Public IP



 Step-by-Step Practical Implementation

Step 1: EC2 Instance Launch with User Data

Launched the EC2 instance and supplied the following **User Data script** to automate Apache installation on boot:

```bash
#!/bin/bash
# Update software packages
yum update -y

# Install Apache Web Server
yum install -y httpd

# Start & enable Apache service on boot
systemctl start httpd
systemctl enable httpd
