 Day 03: High Availability Web Architecture using ALB, Target Groups & Custom AMI
 
 Project Overview
 
Deployed a fault-tolerant and highly available web application architecture on AWS. Incoming HTTP traffic is dynamically distributed across multiple EC2 instances using an **Application Load Balancer (ALB)**, backed by a custom AMI (Golden Image).


 Key Services & Concepts Covered
AWS EC2 & User Data: Automated web server setup via Shell Script.
AWS AMI (Golden Image): Created custom AMI templates to launch identical replica instances instantly.
AWS EBS: Understood root volume block storage lifecycle and persistence.
AWS Target Group:** Configured HTTP Health Checks on Port 80 for backend instances.
AWS Application Load Balancer (ALB): Layer 7 dynamic traffic routing.


Implementation & Proof of Work

 Step 1: Target Group Health Monitoring
Registered backend EC2 instances into the Target Group and validated that HTTP Health Checks passed (`Healthy` status).

![Target Group Health Check](./lg%201.png)


Step 2: Application Load Balancer Provisioning
Deployed an internet-facing Application Load Balancer (`webserver-lb`) across multiple Availability Zones in `Active` state.

![ALB Active Console](./lg%202.png)



Step 3: Dynamic Traffic Routing & High Availability Test
Accessed the web app using the Load Balancer's DNS URL. Refreshing the request or simulating failover proved dynamic routing across instances:

Response from Server 1:
[Server 1 Output](./lg%203.png)

Response from Server 2 (Dynamic Balancing / Failover):
[Server 2 Output](./lg%204.png)



 Infrastructure Cleanup Order
To prevent unnecessary billing, resources were deleted in sequence:
1. Detached/Deleted ASG and Target Group targets.
2. Deleted Application Load Balancer & Target Groups.
3. Terminated EC2 Instances (Handled `disableApiStop` / termination protection locks).
