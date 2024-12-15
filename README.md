# Baston
Web Application to Host 4 Instances for Baston Host, App Server, Database Server 

#The Arctecture of the project
![Arctechture](https://github.com/user-attachments/assets/d964c411-6827-4ea6-a580-23f9253c9f9d)
Web Application Architecture on AWS

This project demonstrates a 3-tier architecture for a web application hosted on AWS. It includes:
Public Subnet: Bastion server, Web server, and NAT Gateway.
Private Subnet: Application server and RDS (Primary Database).
Security Groups: Configured to ensure secure communication between servers and components.
High Availability: Resources are distributed across two Availability Zones for redundancy

#4 Subnets and Monitring
![Monitring](https://github.com/user-attachments/assets/c80a2fdf-5083-44c4-8e6a-ec663984e122)
#EC2 Instances and Monitoring Overview

This screenshot shows 4 EC2 instances running on AWS in the us-west-2a Availability Zone:
App Server (t2.micro)
App Server 1 (t2.micro)
Web Server (t2.micro)
Bastion Host (t2.micro)
Monitoring Metrics:
CPU Utilization (%): Shows low CPU usage across all instances.
Network In/Out (bytes): Indicates incoming and outgoing network traffic, with a recent spike.
Network Packets (In/Out): Measures packet flow, showing an increase in packet counts.
CPU Credit Usage & Balance: Highlights CPU credit consumption and remaining credits for t2.micro instances.

#NAT Gataway
![NAT](https://github.com/user-attachments/assets/b107e389-1973-49c7-ba44-c7048e9d76af)
#NAT Gateway Overview
This NAT Gateway (nat-0e0f342dcca82c86b) is configured in a public subnet to enable instances in private subnets to access the internet securely.
Public IP: 35.165.27.50
Private IP: 192.168.1.89
VPC: Linked to vpc-05f25b79b2294bc7
Subnet: subnet-0b107ceb585ebde10
State: Available
The NAT Gateway allows outbound internet access for private instances while blocking incoming traffic for enhanced security.

#RouteTables
![routetables](https://github.com/user-attachments/assets/66f2bcd1-d28c-4abd-9ab8-daa148898c65)
Route Tables Overview
This screenshot displays 4 Route Tables in the VPC dashboard:
lab-private-table: Associated with private subnets.
lab-public-table: Associated with public subnets to allow internet access.
Main Route Table: Indicated by "Yes" in the Main column, which means it is the default for subnets without explicit associations.
These route tables control traffic flow between public and private subnets, NAT gateways, and the internet gateway.
#App Security Groups
![SGs](https://github.com/user-attachments/assets/4a08d5c8-530e-434d-87da-8f178110f2ad)
Security Groups Overview
This screenshot shows the Security Groups configured for instances within the VPC vpc-05f25b79b2294bbc7:
App-ServerSG
Security Group ID: sg-0cb87e3905f0bd228
Associated with Application Servers.
Web-ServerSG
Security Group ID: sg-0dc3fd1aafdb791bf
Associated with Web Servers.
DatabaseSG
Security Group ID: sg-07adcff3cf393fb1c
Associated with Database instances (RDS).
BastonSG
Security Group ID: sg-0895b1f74894f3083
Associated with the Bastion Host for secure SSH access.
Security Groups manage inbound and outbound rules to allow or restrict network traffic to specific resources.
Each Security Group is isolated and tied to instances for fine-grained control over traffic flow.
#SubnetGroup
![SubnetGroup](https://github.com/user-attachments/assets/6cfc7831-8fc3-4703-a35d-1f6e34e4757d)
RDS Subnet Group Overview
This screenshot shows the successful creation of a Database Subnet Group:
Name: database subnet
Description: Subnet Database
Status: Complete
VPC: vpc-05f25b79b2294bbc7
Purpose:
The database subnet group is configured for Amazon RDS, enabling the deployment of the database instance across private subnets within the specified VPC for high availability and security.
#RDS Database
![Database](https://github.com/user-attachments/assets/b2612678-eff3-4977-b67c-bb0aae4430c7)
RDS Database Overview
This screenshot shows a successfully created RDS database instance:
DB Identifier: database-1
Status: Available
Role: Instance
Engine: MariaDB
Region: us-west-2a
Size: db.t4g.micro
Purpose:
The RDS database instance is now available for use, supporting high availability and performance for the web application's backend.
