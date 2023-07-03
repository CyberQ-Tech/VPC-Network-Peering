# VPC-Network-Peering

# Secure VPC (Virtual Private Cloud) Communication Connection in Google Cloud
![Network Diagram]( https://i.imgur.com/k5GdVXW.jpg)

## Summary

In this project, GCP is used to construct a secure private connection between two cloud networks.  

## Objective
The main objective of this project is to demonstrate how a secure private connection between two networks in different regions can be configured. A VPC is a virtual network that can be used like a physical network to execute business operations. 

Organizations leverage VPCs for numerous reasons related to production and different stages of the SDLC (Software Development Lifecycle). Establishing a secure communication channel between two networks makes the process of sharing data and resources more efficient and helps prevent data loss.

## Platform and Technologies Utilized

- Google Cloud Platform (GCP)
  - Virtual Private Cloud (VPC)
  - Compute Engine (2 Virtual Machines)
  - VPC Network Peering
  
- Additional Items
  - IP Subnetting 
  - Firewall Rules (Ingress)
  - SSH (Secure Shell) 

## Part 1: Creating the VPC Networks and Regional Placement

In this phase, two networks are deployed in separate geographical locations to simulate a global enterprise operation. Development is a collaborative effort that often requires individuals working on the same project in different environments.

Some of the configurations used to accomplish this include: 

-	Created (2) VPC Networks
-	Placed VPCs in different Regions
-	Configured Custom Subnets
-	Set Firewall Ingress Rules
<br/>
<b>VPC Deployment</b>

![VPC 1]( https://i.imgur.com/nG6V9bJ.jpg)

![VPC 2]( https://i.imgur.com/avTIvsx.jpg)

<br/>
<b>Subnet and Region</b>
![Subnet 1]( https://i.imgur.com/bjM8WQU.jpg)

