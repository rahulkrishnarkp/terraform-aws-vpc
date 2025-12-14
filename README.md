# Terraform AWS VPC

This repository contains Terraform code to provision a custom AWS Virtual Private Cloud (VPC).
It demonstrates core AWS networking concepts implemented using Infrastructure as Code (IaC).

---

## Overview

The project creates a basic but production-aligned VPC setup with clear separation between
public and private networking components.

The focus is on **intentional network design**, explicit routing, and clean Terraform practices.

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
- Serves as the isolated network boundary

### Public Subnet
- CIDR: `10.0.0.0/24`
- Availability Zone: `ap-south-1a`
- Associated with a route table that routes traffic to an Internet Gateway
- Public IPs are expected to be managed using Elastic IPs

### Private Subnet
- CIDR: `10.0.1.0/24`
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

## How to Run

```bash
terraform init
terraform plan
terraform apply

