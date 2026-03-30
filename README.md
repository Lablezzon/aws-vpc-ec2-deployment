# aws-vpc-ec2-deployment
AWS VPC Architecture & EC2 Deployment Project
 
 Overview
This project demonstrates the design and implementation of a custom Virtual Private Cloud (VPC) in Amazon Web Services, including network segmentation, security configuration, and deployment of a virtual machine using Amazon EC2.
The goal is to build a secure, scalable, and production-aligned cloud network architecture from scratch, following core cloud networking and DevOps best practices.

Architecture Design
The architecture was first modeled using draw.io to visualize:
•	CIDR block allocation 
•	Multi-subnet design across availability zones 
•	Internet connectivity via Internet Gateway 
•	Traffic flow and routing 
•	Security layers (NACLs & Security Groups) 

Core Components Implemented
1. Virtual Private Cloud (VPC)
•	Custom CIDR block defined 
•	DNS hostnames and resolution enabled 
•	Default tenancy configuration 
•	Logical isolation of cloud resources 

2. Subnet Architecture
•	Created multiple subnets across different Availability Zones 
•	Removed default subnets to enforce custom architecture 
•	Designed subnet segmentation (e.g., frontend/backend-ready structure) 

3. Internet Gateway (IGW)
•	Created and attached IGW to VPC 
•	Enabled outbound internet access for public resources 

4. Route Tables
•	Configured custom route tables 
•	Associated subnets with route tables 
•	Defined route: 
o	0.0.0.0/0 → Internet Gateway 
•	Enabled controlled internet traffic routing 

5. Network Security Configuration
🔐 Network Access Control Lists (NACLs)
•	Created dedicated NACLs per subnet 
•	Configured: 
o	Inbound and outbound rules 
o	RDP (3389) access restriction 
o	DNS (TCP/UDP 53) rules 
•	Implemented subnet-level stateless security 
🔐 Security Groups
•	Created security groups per subnet/workload 
•	Configured: 
o	Inbound rules (RDP, required services) 
o	Outbound rules (allow all or restricted as needed) 
•	Implemented instance-level stateful security 

6. VPC Flow Logs
•	Enabled traffic monitoring using VPC Flow Logs 
•	Captured: 
o	Accepted traffic 
o	Rejected traffic 
•	Delivered logs to Amazon S3 
•	Supports auditing, troubleshooting, and security analysis 

EC2 Instance Deployment
Instance Configuration
•	OS: Windows Server 
•	Instance Type: t3.micro 
•	Storage: GP3 (custom size) 
•	Key Pair authentication configured 
•	Subnet and security group explicitly assigned 

Connectivity Setup
•	Remote access via RDP (Port 3389) 
•	Public IP assigned 
•	Password decrypted using key pair 
•	Network rules updated to allow secure access 

Network Adjustments for Connectivity
•	Updated NACL inbound rules to allow: 
o	RDP (3389) 
o	DNS (TCP/UDP 53) 
•	Updated Security Group rules to allow: 
o	RDP from trusted IP 

Observability & Validation
•	Verified: 
o	Subnet associations 
o	Route table configurations 
o	Security layers (NACLs & SGs) 
•	Monitored traffic using Flow Logs 
•	Confirmed internet access from EC2 instance 

 Resource Cleanup (Cost Optimization)
To prevent unnecessary billing:
•	Terminated EC2 instances 
•	Deleted key pairs 
•	Removed EBS volumes 
•	Deleted NACLs and Security Groups 
•	Cleaned up VPC resources 

 Key DevOps & Cloud Concepts Demonstrated
•	Infrastructure provisioning in AWS 
•	Network segmentation and isolation 
•	Defense-in-depth security (NACL + SG) 
•	Cloud observability with flow logs 
•	Secure remote access configuration 
•	Resource lifecycle management 

Possible Improvements (Future Work)
•	Automate provisioning using Terraform or AWS CloudFormation 
•	Implement public/private subnet architecture with NAT Gateway 
•	Add Application Load Balancer (ALB) 
•	Integrate CI/CD pipeline (GitHub Actions / Azure DevOps) 
•	Enable IAM roles for secure access control 
•	Deploy containerized workloads using Docker + ECS/EKS 

 Project Documentation
Full step-by-step guide available here: 


Conclusion
This project establishes a strong foundation in cloud networking and infrastructure engineering, demonstrating the ability to design, secure, and deploy scalable environments in AWS. It reflects practical DevOps skills applicable to real-world cloud architectures.
