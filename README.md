# 10 Days of AWS Networking Zero to Hero

## Prerequisites:
1. Windows/Mac laptop
2. Basic Linux Commands

## Day 1: AWS VPC (Virtual Private Cloud) Part 1
Introduction to AWS VPC networking, including CIDR blocks, subnets, route tables, and internet gateway setup.
- What is AWS VPC (Virtual Private Cloud)?
- Key features of AWS VPC
- CIDR (Classless Inter-Domain Routing)
- Lab Session - Choose the appropriate CIDR Block
- IPv4 and IPv6
- Subnets in AWS VPC
- Types of Subnets in AWS VPC
- Subnet sizing for IPv4
- Subnet routing in AWS VPC
- Route table in AWS VPC
- Components of a Route table
- Internet Gateway (IGW) in AWS VPC
- Lab Session - Overview of the Default VPC in AWS

## Day 2: AWS VPC (Virtual Private Cloud) Part 2
Advanced VPC configurations including NAT instances, NAT gateways, NACLs, and Security Groups.
- Lab Session - Create a customized VPC in AWS
- NAT Gateway and NAT Instance in AWS VPC
- Differences between NAT Gateway and NAT Instance
- Lab Session - Create a NAT Instance in AWS VPC
- Lab Session - Create a NAT Gateway in AWS VPC
- Lab Session - Delete a NAT Gateway in AWS VPC

## Day 3: AWS VPC (Virtual Private Cloud) Part 3
Exploring VPC Flow Logs, DHCP options, VPC endpoints, and Elastic Network Interfaces (ENIs).
- Network Access Control List (NACL) in AWS VPC
- Lab Session - Create a Network Access Control List (NACL) in AWS VPC
- Security Group in AWS VPC
- Lab Session - Create a Security Group in AWS VPC
- Differences between NACL and Security Group in AWS VPC
- VPC Flow Logs and how to create them
- Lab Session - Enable VPC Flow Logs

## Day 4: AWS VPC (Virtual Private Cloud) Part 4
Advanced VPC options like DNS settings, Prefix Lists, and deletion procedures for custom VPC setups.
- Options for configuring an AWS VPC
- DHCP Option Set in AWS VPC
- DNS Hostnames and DNS Resolution in AWS VPC
- VPC Endpoints in AWS and types available
- Lab Session - Create a Gateway VPC Endpoint for S3 in AWS
- Prefix Lists in AWS VPC
- Elastic Network Interface (ENI) in AWS
- Lab Session - Create an ENI in AWS
- Lab Session - Delete an AWS VPC

## Day 5: AWS VPC Peering Part 1
Understanding VPC peering within and between regions, including setup, management, and termination.
- What is VPC Peering?
- Key aspects of VPC Peering
- Types of VPC Peering
- Lab Session - Intra-region VPC peering within the same AWS account
- Lab Session - Delete intra-region VPC peering within the same AWS account

## Day 6: AWS VPC Peering Part 2
- Lab Session - Establish intra-region VPC peering with a different AWS account
- Lab Session - Terminate intra-region VPC peering with a different AWS account
- Lab Session - Inter-region VPC peering within the same AWS account
- Lab Session - Remove inter-region VPC peering within the same AWS account
- Lab Session - Configure inter-region VPC peering with a different AWS account
- Lab Session - Remove inter-region VPC peering with a different AWS account

## Day 7: AWS Transit Gateway (TGW)
- What is AWS Transit Gateway?
- Advantages of using AWS Transit Gateway
- Different types of AWS Transit Gateway
- Key components of AWS Transit Gateway
- Difference between VPC Peering and Transit Gateway
- Lab Session - Establish inter-region Transit Gateway peering within the same AWS account
- Lab Session - Terminate inter-region Transit Gateway peering within the same AWS account

## Day 8: AWS Transit Gateway (TGW) Continued
- What is AWS RAM (Resource Access Manager)?
- Lab Session - Set up inter-region Transit Gateway peering with a different AWS account
- Lab Session - Terminate inter-region Transit Gateway peering with a different AWS account
- Lab Session - Delete RAM (Resource Access Manager) configurations
- Lab Session - Create intra-region Transit Gateway peering within the same AWS account
- Lab Session - Terminate intra-region Transit Gateway peering within the same AWS account
- Lab Session - Establish intra-region Transit Gateway peering with a different AWS account
- Lab Session - Terminate intra-region Transit Gateway peering with a different AWS account

## Day 9: Site-to-Site VPN
- What is a Customer Gateway?
- What is a Virtual Private Gateway?
- What is a Site-to-Site VPN Connection?
- Lab Session - Installation of Openswan in Amazon Linux
- Lab Session - Creation of Customer Gateway (CGW)
- Lab Session - Creation of Virtual Private Gateway
- Lab Session - Site-to-Site VPN Connection using Openswan
- Test the connectivity

## Day 10: AWS Client VPN
What is AWS Client VPN?
Features of Client VPN
Components of Client VPN
Limitations and rules of Client VPN
Lab Session - Creation of Active Directory in AWS
Lab Session - Creation of ACM
Lab Session - Creation of the client VPN endpoint
Test the connection using Private IP
Lab Session - Deletion of the client VPN endpoint


## Day 11: AWS Cloud WAN
- What is AWS Cloud WAN?
- Global and core network key concepts
- Get started with AWS Cloud WAN
- Create a global network
- Create a core network and core network policy
- Work with attachments
  - Add a transit gateway route table attachment
  - Add a VPC attachment
  - Add a Site-to-Site VPN attachment
