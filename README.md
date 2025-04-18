# Assignment-for-Group-Delta
Deploying Gateway Load Balancer (GWLB) Infrastructure on AWS
** Lab Overview
Goal:**
Set up a secure and scalable environment using AWS GWLB to route and inspect traffic between a public-facing application and internal systems.

**Architecture Highlights:**

2 VPCs: SecurityVPC and VPC1

GWLB deployed in SecurityVPC

GWLB endpoints in both VPCs

Traffic routed through appliances via GWLB ENIs

Use of NAT Gateways, Transit Gateway, and VPC endpoints

**Lab Setup Steps**
1. Deploy Base Infrastructure
Use the provided CloudFormation templates to spin up:

**VPCs**

Subnets (Public, Private, Firewall, Data, GWLB Endpoints)

NAT Gateways, NLB, and Transit Gateway

**Instructions:**

Region: us-east-1

Launch CloudFormation stack in AWS Console or via AWS CLI

Optional: Use CloudShell to upload templates to an S3 bucket

**2. Create Gateway Load Balancer Endpoint Service
In the Security VPC:**

**Go to VPC > Endpoint Services**

Click Create endpoint service

Select Gateway as type

Choose the existing GWLB

Uncheck "Acceptance required"

**3. Create GWLB Endpoints
In both SecurityVPC and VPC1:**

Go to VPC > Endpoints

Select the previously created service

Attach to appropriate subnets

**4. Configure Route Tables
VPC1 public subnets route 0.0.0.0/0 → GWLB endpoint**

VPC1 private subnets route → NAT Gateway and TGW

SecurityVPC data subnets route via GWLB ENIs
