 # 🚀 AWS VPC Networking Architecture – Public & Private Subnets

## 📌 Objective

The objective of this project was to design and deploy a custom Virtual Private Cloud (VPC) in Amazon Web Services (AWS), implementing a secure public and private subnet architecture with controlled internet access and properly configured EC2 instances.

---

## 🏗️ Architecture Overview

This project includes:

- Custom VPC ()
- 🌐 One Public Subnet
- 🔒 One Private Subnet
- Internet Gateway (IGW)
- NAT Gateway
- 🖥 Public EC2 Instance
- 🖥 Private EC2 Instance
- Secure Security Group configuration

### Key Design Principles

- Public resources are accessible from the internet
- Private resources are isolated from direct public access
- Private instances access the internet outbound-only via NAT Gateway
- Security groups follow least-privilege access rules

---

## 🗺️ Architecture Diagram

                Internet
                    │
            ┌────────────────┐
            │ Internet Gateway│
            └────────────────┘
                    │
          ┌────────────────────┐
          │        VPC         │
          │    10.0.0.0/16     │
          └────────────────────┘
             │              │
    ┌────────────────┐   ┌────────────────┐
    │ Public Subnet  │   │ Private Subnet │
    │ 10.0.1.0/24    │   │ 10.0.2.0/24    │
    └────────────────┘   └────────────────┘
         │                      │
   ┌──────────────┐       ┌──────────────┐
   │ Public EC2   │       │ Private EC2  │
   └──────────────┘       └──────────────┘
         │                      │
         │              ┌──────────────┐
         └─────────────▶│ NAT Gateway  │
                        └──────────────┘

---

## 🔧 Tasks Completed

### 1️⃣ VPC Creation

- Created a custom VPC with CIDR block 
- Created one public subnet
- Created one private subnet

---

### 2️⃣ 🌍 Internet Access Configuration

- Created and attached an Internet Gateway to the VPC
- Created a NAT Gateway in the public subnet

> The Internet Gateway allows inbound internet access to public resources, while the NAT Gateway enables private instances to initiate outbound internet connections without being publicly exposed.

---

### 3️⃣ 🛣 Route Tables

Configured routing as follows:

**Public Route Table**
0.0.0.0/0 → Internet Gateway


**Private Route Table**
0.0.0.0/0 → NAT Gateway


Each route table was correctly associated with its respective subnet.

---

### 4️⃣ 🖥 EC2 Deployment

#### Public EC2
- Launched in the public subnet
- Assigned a public IPv4 address
- Accessible via SSH and HTTP (restricted to my IP address)

#### Private EC2
- Launched in the private subnet
- No public IPv4 address assigned
- Not directly accessible from the internet

---

### 5️⃣ 🔐 Security Configuration

Security groups were configured using least-privilege principles:

**Public EC2 Security Group**
- SSH (Port 22) → Allowed from my IP only
- HTTP (Port 80) → Allowed from my IP only

**Private EC2 Security Group**
- SSH (Port 22) → Allowed only from internal VPC resources
- No direct public internet access permitted

This configuration ensures proper network segmentation and secure communication between resources.

---

## 📸 Implementation Evidence

Screenshots documenting the full setup are available here:

👉 **[Insert Screenshot Link Here]**

Included evidence shows:

- VPC and subnet creation
- Internet Gateway attachment
- NAT Gateway configuration
- Route table associations
- EC2 deployment
- Security group configuration
- Public EC2 HTTP access validation

---

## 📚 Key Learnings

- Practical understanding of public vs private subnet architecture
- How NAT Gateways provide secure outbound-only internet access
- Importance of correct route table associations
- Applying least-privilege security group rules
- Deploying secure infrastructure within AWS

---

## 🔐 Security Notice

All sensitive information (IP addresses, instance IDs, account details, and credentials) has been removed or rotated.

This repository contains no active production resources. 
