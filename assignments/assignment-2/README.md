# Assignment 2 – Application Load Balancer with Multiple EC2 Instances
## CoderCo AWS – Second Assignment

## Overview

This is the second CoderCo AWS assignment.

The objective was to deploy two EC2 instances behind an Application Load Balancer (ALB) and ensure that all traffic flows through the load balancer. The EC2 instances are not directly accessible from the internet.

This assignment focuses on load balancing, health checks, multi-AZ deployment, and security group isolation.

## Objective

This assignment implements:

Deploy two EC2 instances in the same VPC

Place them in different Availability Zones

Configure an Application Load Balancer

Route all traffic through the ALB

Prevent direct public access to EC2 instances

## Architecture

The setup includes:

1 VPC

2 public subnets (across separate AZs)

2 EC2 instances

1 internet-facing Application Load Balancer

1 target group

Traffic flow:
Internet → ALB → Target Group → EC2 Instances

The architecture diagram is shown here:
[Architecture](./architecture)

## Implementation

### EC2 Instances

Launched two EC2 instances in different Availability Zones

Installed Apache using user data scripts

Configured each instance with different web content to verify load balancing

User data scripts are shown here:
[View User-Data](user-data/)

### Application Load Balancer

Created an internet-facing ALB

Attached it to two public subnets

Added an HTTP (port 80) listener

Created a target group

Registered both EC2 instances

Configured health checks on /

### Security Groups

ALB security group allows inbound HTTP from anywhere

EC2 security group allows inbound HTTP only from the ALB security group

EC2 instances are not publicly accessible

## Testing

Accessed the ALB DNS name in a browser

Refreshed multiple times to confirm traffic alternated between both instances

Verified both instances were healthy in the target group

Confirmed EC2 public IPs were not directly accessible

## Evidence

Screenshots of the full implementation are shown here:
[View Screenshots](screenshots/)


These include:

EC2 deployment

User data configuration

ALB setup

Target group health checks

Security group configuration

Load balancing verification

## Key Takeaways

How ALBs distribute traffic across multiple instances

How health checks determine availability

Why backend instances should not be publicly exposed

How security groups control internal traffic
