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

![Subnet 2]( https://i.imgur.com/OOqDSar.jpg)

<br/>
<b>Firewall Rules</b>

![Firewall 1]( https://i.imgur.com/05Q1mwt.jpg)

Note: I used the same steps to create the VPC #2 with these exceptions:

-	Different VPC name and subnet
-	Placed VPC #2 in a different region
-	Configured a different IPv4 range (ex: 172.16.0.0/24)
  --	This ensures no collision between IP ranges between the VPCs


## Part 2: Creating Virtual Machines and Subnetting

In this phase, the two virtual machines are created, and one is placed in each of the VPC networks. In addition, the VMs are linked to the proper subnets to ensure only ingress communication from the approved subnet range is allowed. 

Some of the configurations used to accomplish this include: 

-	Created (2) Virtual Machines
-	Subnetting IP Addresses

<b>VM Deployment</b>

![VM 1]( https://i.imgur.com/OrjqED1.jpg)

![VM 2]( https://i.imgur.com/wnWDsn8.jpg)

<br/>
<b>Linking Subnet to VPC</b>

![Link Subnet 1]( https://i.imgur.com/xTtcJHH.jpg)

![Link Subnet 2]( https://i.imgur.com/abTFyP1.jpg)

Note: I used the same steps to create VM #2 with these exceptions:

-	Different name
-	Placed VM #2 in a different region
-	Linked VPC to subnet 


![VM 3]( https://i.imgur.com/2Nep4SO.jpg)

<b>VM #2</b>

![VM 4]( https://i.imgur.com/YJ9DOJ4.jpg)


## Part 3: Test Internal IP Connection via SSH

In this phase, the connection between both VPCs is tested using SSH. This is accomplished by attempting to ping the opposing VPC using its internal IP address. This ping will fail, and all data packets will be lost because VPC Peering has not been configured. 


<b>VM #1 Attempting to Ping VM #2: The data packets for the internal IP are lost. Only the external IP is reachable.</b>

![SSH 1]( https://i.imgur.com/NPnDCQs.jpg)

<b>VM #2 Attempting to Ping VM #1: The data packets for the internal IP are lost. Only the external IP is reachable.</b>

![SSH 2]( https://i.imgur.com/FKxe1nn.jpg)


## Part 4: Configuring VPC Network Peering and Testing Communication

In this phase, a secure network connection is established between the two networks via VPC peering. Despite linking the networks in the previous phase, VPC peering still needs to be enabled in order for secure communication to take place internally. 

Some of the configurations used to accomplish this include: 

-	Configured VPC Peering
o	Note: Peering must be configured on both networks sides to be successful
-	Testing Communication via SSH

<b>VPC Peering</b>

![Peer 1]( https://i.imgur.com/331P3ZV.jpg)

<b>Peering VPC #1 to #2</b>
![Peer 2]( https://i.imgur.com/ZPsbYFd.jpg)

<b>Peering VPC #2 to VPC #1</b>
![Peer 3]( https://i.imgur.com/tpBzuSJ.jpg)

![Peer 4](https://i.imgur.com/0N5mcoM.jpg)

## Confirming the Secure Connection is Working

<b>VPC #1 communicates with VPC #2</b>
![SSH 3](https://i.imgur.com/LaJJ5zl.jpg)

<b>VPC #2 communicates with VPC #1</b>
![SSH 4](https://i.imgur.com/KHloil7.jpg)

## Conclusion

This project showcased the importance of establishing a secure tunnel for communication with different networks. Many network and data breaches occur as a result of communication being intercepted in the form of On-path (Man-in-the-Middle) attacks. VPC peering is one of the ways to prevent network communication from being hijacked.


