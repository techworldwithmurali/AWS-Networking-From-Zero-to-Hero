### What is AWS VPC (Virtual Private Cloud)?

AWS Virtual Private Cloud (VPC) is a virtual network that you create in AWS. It allows you to launch AWS resources, such as EC2 instances, into a virtual network that you define. This gives you control over your network environment, including IP address range selection, subnets, route tables, and network gateways.

### Key Features of AWS VPC

1. **Isolation:** Logical isolation of your resources.
2. **Control:** Complete control over your virtual networking environment.
3. **Scalability:** Easily scale your VPC as your AWS resources grow.
4. **Security:** Secure your resources using security groups and network access control lists (ACLs).
5. **Connectivity:** Connect your VPC to other networks using VPN or AWS Direct Connect.
----
### CIDR (Classless Inter-Domain Routing)

**CIDR:** A method for allocating IP addresses and routing Internet Protocol packets. It uses a slash notation (e.g., 10.0.0.0/16) to define the range of IP addresses in a network.

### Lab Session - Choose the Appropriate CIDR Block

1. **Choose CIDR Block:**
   - Decide on the IP address range (CIDR block) for your VPC.
   - Consider the number of resources you plan to deploy and their scalability.
   - Plan for future growth and avoid overlapping with existing networks.

### IPv4 and IPv6

- **IPv4:** Standard IP addressing scheme, limited by the number of available addresses.
- **IPv6:** Next-generation IP addressing scheme, offering a vastly larger number of addresses to accommodate future growth.

### IPv4 VPC CIDR blocks
- When creating a Virtual Private Cloud (VPC) in AWS, you must specify an IPv4 CIDR block for the VPC.
- The CIDR block must have a block size between a /16 netmask (which provides 65,536 IP addresses) and a /28 netmask (which provides 16 IP addresses).
- After creating the VPC, you can associate additional IPv4 CIDR blocks with it as needed. For more details, refer to the AWS documentation on how to [add or remove a CIDR block from your VPC](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html#vpc-resize).

It is recommended to specify a CIDR block from the private IPv4 address ranges defined in RFC 1918 when creating your VPC. The following are the private IPv4 address ranges as specified in RFC 1918 along with example CIDR blocks:

- **10.0.0.0 - 10.255.255.255 (10/8 prefix)**
  - Example CIDR block: `10.0.0.0/16`
- **172.16.0.0 - 172.31.255.255 (172.16/12 prefix)**
  - Example CIDR block: `172.31.0.0/16`
- **192.168.0.0 - 192.168.255.255 (192.168/16 prefix)**
  - Example CIDR block: `192.168.0.0/20`

These private IP address ranges are commonly used for creating VPCs, as they are not routable on the public internet and help ensure network isolation.

----
### Subnets in AWS VPC

**Subnets:** Divisions of IP address ranges within a VPC. Each subnet resides in a specific Availability Zone (AZ).

### Types of Subnets in AWS VPC
In an AWS VPC, subnets are segments of the VPC's IP address range where you can launch AWS resources. Different types of subnets serve different purposes, and they can be categorized as follows:

### 1. Public Subnet
A public subnet is a subnet that has a route to the internet gateway, allowing instances within it to communicate directly with the internet. Typically, these subnets are used for resources that need to be publicly accessible, such as:

- Web servers
- Bastion hosts
- NAT gateways (to provide internet access to private subnets)

### 2. Private Subnet
A private subnet is a subnet that does not have a route to the internet gateway, ensuring that instances within it cannot directly access the internet. These subnets are used for resources that should not be accessible from the public internet, such as:

- Backend servers (e.g., application servers)
- Databases
- Internal services

### 3. Application Subnet
An application subnet (often a type of private subnet) is typically used to host application layer services. These subnets are often isolated to enhance security and reduce exposure to potential threats. Examples of resources that might reside in an application subnet include:

- Application servers
- Middleware services

### 4. Data Subnet
A data subnet (another type of private subnet) is used specifically for data storage and management services. These subnets are designed to host resources that manage data, such as:

- Databases (e.g., Amazon RDS, NoSQL databases)
- Data warehouses
- Storage services (e.g., Amazon EFS)

### Subnet Sizing for IPv4

- Choose a subnet mask (e.g., /24) that accommodates the number of IP addresses needed for resources in the subnet.
- Consider future growth and the number of resources that will reside in each subnet.

### Subnet Routing in AWS VPC

- Each subnet has a route table that defines how traffic is routed within the VPC and to external networks.
- Route tables specify which subnets traffic should be routed to based on the destination IP address.
---
### Route Table in AWS VPC

- A Route Table in AWS VPC is a critical component that controls the routing of traffic within the VPC and between the VPC and other networks.

- It contains a set of rules, called routes, that determine where network traffic is directed.

### Key Concepts

- **Route Table**: A logical object within a VPC that contains routing rules. Each route specifies a destination and a target.
- **Routes**: Rules within the route table that define the path for traffic. Each route consists of a destination CIDR block and a target.
- **Targets**: The target for traffic destined for a specified CIDR block. Examples of targets include internet gateways (IGWs), virtual private gateways (VGWs), instances, network interfaces, and peering connections.
- **Subnet Association**: Each subnet in your VPC must be associated with a route table, which controls the routing for that subnet. If a subnet is not explicitly associated with any route table, it uses the main route table of the VPC.

### Main Route Table and Custom Route Tables

- **Main Route Table**: Each VPC has a default route table, known as the main route table. All subnets not explicitly associated with any custom route table use the main route table.
- **Custom Route Tables**: You can create additional route tables and associate them with specific subnets to provide more granular control over routing.

### Default Routes

When you create a VPC, it includes a default route table with a single route:
- **Local Route**: This route enables communication within the VPC (e.g., instances in the VPC can communicate with each other).
  ```plaintext
  Destination: 10.0.0.0/16 (assuming the VPC CIDR is 10.0.0.0/16)
  Target: local
  ```


### Common Use Cases

- **Public Subnets**: Routes traffic destined for the internet (0.0.0.0/0) to an internet gateway.
- **Private Subnets**: Routes internal traffic within the VPC (using the local route) and internet-bound traffic through a NAT gateway for security.
- **VPN Connections**: Routes traffic to a virtual private gateway for VPN connectivity.
- **Peering Connections**: Routes traffic to a VPC peering connection for communication between VPCs.

### Example Scenario

Consider a VPC with the CIDR block `10.0.0.0/16`, a public subnet `10.0.1.0/24`, and a private subnet `10.0.2.0/24`. You want instances in the public subnet to have direct internet access, and instances in the private subnet to access the internet through a NAT gateway.

1. **Public Route Table**:
   - Route to local VPC: `10.0.0.0/16 -> local`
   - Route to internet: `0.0.0.0/0 -> igw-12345678`

2. **Private Route Table**:
   - Route to local VPC: `10.0.0.0/16 -> local`
   - Route to internet via NAT: `0.0.0.0/0 -> nat-12345678`

By configuring route tables appropriately, you can control the flow of traffic within your VPC and to external networks, ensuring that your resources are accessible as needed while maintaining security and efficiency.

----
### Internet Gateway (IGW) in AWS VPC

**Internet Gateway (IGW):** Allows communication between instances in your VPC and the internet. It serves as a gateway that translates network traffic between the internet and your VPC.
### Key Characteristics

- **Horizontally Scalable and Highly Available**: An IGW is designed to handle a large amount of traffic and is highly available across multiple Availability Zones in the region.
- **No Cost**: There is no additional cost to use an IGW, but you will be charged for data transfer and any other AWS services used.
- **Direct Connectivity**: It allows instances in a public subnet to connect directly to the internet.
----
### Lab Session - Overview of the Default VPC in AWS

1. **Sign in to AWS Management Console:**
   - Navigate to the VPC Dashboard at [AWS Management Console](https://console.aws.amazon.com/vpc/).

2. **Overview of Default VPC:**
   - Explore the default VPC provided by AWS, which includes default subnets, route tables, and security groups.
   - Review the CIDR block allocated to the default VPC and its components.
   - Understand the default networking settings and how resources are configured in the default VPC.
