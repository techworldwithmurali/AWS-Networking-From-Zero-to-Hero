### What is AWS VPC (Virtual Private Cloud)?

AWS Virtual Private Cloud (VPC) is a virtual network that you create in AWS. It allows you to launch AWS resources, such as EC2 instances, into a virtual network that you define. This gives you control over your network environment, including IP address range selection, subnets, route tables, and network gateways.

### Key Features of AWS VPC

1. **Isolation:** Logical isolation of your resources.
2. **Control:** Complete control over your virtual networking environment.
3. **Scalability:** Easily scale your VPC as your AWS resources grow.
4. **Security:** Secure your resources using security groups and network access control lists (ACLs).
5. **Connectivity:** Connect your VPC to other networks using VPN or AWS Direct Connect.

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

### Subnets in AWS VPC

**Subnets:** Divisions of IP address ranges within a VPC. Each subnet resides in a specific Availability Zone (AZ).

### Types of Subnets in AWS VPC

1. **Public Subnets:** Directly accessible from the internet. Typically used for resources that need public access.
2. **Private Subnets:** Not accessible directly from the internet. Used for resources that require additional security.

### Subnet Sizing for IPv4

- Choose a subnet mask (e.g., /24) that accommodates the number of IP addresses needed for resources in the subnet.
- Consider future growth and the number of resources that will reside in each subnet.

### Subnet Routing in AWS VPC

- Each subnet has a route table that defines how traffic is routed within the VPC and to external networks.
- Route tables specify which subnets traffic should be routed to based on the destination IP address.

### Route Table in AWS VPC

**Route Table:** Controls the routing for the subnet. It contains a set of rules (routes) that determine where network traffic from the subnet is directed.

### Components of a Route Table

1. **Routes:** Define where traffic should go based on the destination IP address.
2. **Association:** Associates subnets with the route table to control their routing behavior.

### Internet Gateway (IGW) in AWS VPC

**Internet Gateway (IGW):** Allows communication between instances in your VPC and the internet. It serves as a gateway that translates network traffic between the internet and your VPC.

### Lab Session - Overview of the Default VPC in AWS

1. **Sign in to AWS Management Console:**
   - Navigate to the VPC Dashboard at [AWS Management Console](https://console.aws.amazon.com/vpc/).

2. **Overview of Default VPC:**
   - Explore the default VPC provided by AWS, which includes default subnets, route tables, and security groups.
   - Review the CIDR block allocated to the default VPC and its components.
   - Understand the default networking settings and how resources are configured in the default VPC.
