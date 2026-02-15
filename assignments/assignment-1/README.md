# AWS VPC Networking Architecture – Public & Private Subnets

## Objective

The objective of this project was to design and deploy a custom Virtual Private Cloud (VPC) in **Amazon Web Services (AWS)**, implementing public and private subnet architecture with controlled internet access and secure EC2 deployment.

---

## Architecture Overview

This project implements:

- Custom VPC (CIDR: `10.0.0.0/16`)  
- **Public Subnet**  
- **Private Subnet**  
- Internet Gateway (IGW)  
- NAT Gateway  
- **Public EC2 Instance**  
- **Private EC2 Instance**  
- Secure Security Group configuration  

See the architecture diagram in:
[Architecture](./architecture)


**Key Architecture Principles:**

- Public resources are internet-accessible  
- Private resources remain isolated  
- Outbound-only internet access for private instances via NAT Gateway  

---

## Tasks Implemented

### 1️⃣ VPC Creation

- Created a custom VPC with CIDR block `10.0.0.0/16`  
- Created:
  - One Public Subnet  
  - One Private Subnet  

---

### 2️⃣ Internet Access Configuration

- Created and attached an **Internet Gateway** to the VPC  
- Created a **NAT Gateway** in the public subnet  

> The Internet Gateway allows inbound internet access to public resources, while the NAT Gateway enables outbound-only internet access for private resources.

---

### 3️⃣ Route Tables

- **Public Route Table**
  - `0.0.0.0/0 → Internet Gateway`  
- **Private Route Table**
  - `0.0.0.0/0 → NAT Gateway`  

Each route table was associated with its respective subnet to enforce proper routing.

---

### 4️⃣ EC2 Deployment

Using **Amazon EC2**:

- **Public EC2**
  - Deployed in the public subnet  
  - Assigned a public IPv4 address  
  - Accessible via SSH and HTTP (restricted to my IP)  

- **Private EC2**
  - Deployed in the private subnet  
  - No public IPv4 address assigned  
  - Not directly accessible from the internet  

---

### 5️⃣ Security Configuration

Security groups were configured with least-privilege access:

- **Public EC2 Security Group**
  - SSH (Port 22) → Allowed from my IP only  
  - HTTP (Port 80) → Allowed from my IP only  

- **Private EC2 Security Group**
  - SSH (Port 22) → Allowed only from internal VPC resources  
  - No public access permitted  

This setup ensures proper network isolation between subnets.

---

## Implementation Evidence

Step-by-step screenshots documenting the full setup are available here:  

👉 [View Screenshots](screenshots/)


Included screenshots demonstrate:

- VPC creation  
- Subnet configuration  
- Internet Gateway attachment  
- NAT Gateway setup  
- Route table associations  
- EC2 instance deployment  
- Security group rules  
- Public EC2 HTTP access validation  

---

## Key Concepts Learned

- Difference between **public** and **private subnets**  
- How **NAT Gateways** provide outbound-only internet access  
- Importance of correct **route table associations**  
- Designing **secure security groups** using least privilege  
- Deploying and isolating EC2 instances within a VPC  

---

## Security Notice

All sensitive information (IP addresses, instance IDs, account IDs, and credentials) has been removed or rotated.  

This project contains no active production resources.
