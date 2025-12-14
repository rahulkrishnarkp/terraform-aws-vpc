# Terraform AWS VPC

This repository contains Terraform code to provision an AWS Virtual Private Cloud (VPC)
with a clear separation of public and private networking components.

The project demonstrates practical AWS networking fundamentals implemented using
Infrastructure as Code (IaC).

---

## Overview

The goal of this project is to build a basic yet production-aligned VPC setup using Terraform.
It focuses on explicit routing, subnet isolation, and clean infrastructure design.

This VPC can act as a foundation for workloads such as EC2, ALB, NAT Gateway, and other
AWS services.

---

## Architecture

![AWS VPC Resource Map](screenshots/vpc.png)

---

## Resources Created

- AWS VPC
- Public subnet
- Private subnet
- Internet Gateway
- Public route table
- Private route table
- Explicit route table associations

---

## Network Design

### VPC
- CIDR block: `10.0.0.0/16`
- Acts as the network boundary for all resources

### Public Subnet
- CIDR block: `10.0.0.0/24`
- Availability Zone: `ap-south-1a`
- Associated with a route table that routes traffic to an Internet Gateway
- Public IPs are managed using Elastic IPs (auto-assign disabled)

### Private Subnet
- CIDR block: `10.0.1.0/24`
- Availability Zone: `ap-south-1b`
- Associated with a private route table
- No direct internet access

---

## Routing Strategy

- Public route table routes `0.0.0.0/0` traffic to the Internet Gateway
- Private route table contains no internet route
- AWS default main route table is left unused intentionally

---

## Tools & Technologies

- Terraform
- AWS VPC, Subnets, Route Tables, Internet Gateway
- Git and GitHub

---

## How to Use

```bash
terraform init
terraform plan
terraform apply