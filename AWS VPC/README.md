### What is AWS VPC (Virtual Private Cloud)?

- AWS Virtual Private Cloud (VPC) is a virtual network that you create in AWS. It allows you to launch AWS resources, such as EC2 instances, into a virtual network that you define.
- This gives you control over your network environment, including IP address range selection, subnets, route tables, and network gateways.

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
  
  ---
  ### NAT Gateway and NAT Instance in AWS VPC

**NAT (Network Address Translation) Gateway** and **NAT Instance** are used to enable instances in a private subnet to connect to the internet or other AWS services, but prevent the internet from initiating connections with those instances.

#### NAT Gateway

**NAT Gateway** is a managed service provided by AWS that enables instances in a private subnet to connect to the internet. It is highly available and scalable, automatically managed by AWS.

**Key Features of NAT Gateway:**
- **Managed Service:** AWS manages the NAT Gateway, ensuring high availability and scalability.
- **Automatic Scaling:** It automatically scales up to meet bandwidth requirements.
- **Ease of Use:** Simple to set up and requires minimal maintenance.
- **High Availability:** Deployed in a specific availability zone but can be set up with multiple NAT Gateways across different zones for redundancy.

#### NAT Instance

**NAT Instance** is an EC2 instance configured to perform network address translation (NAT) for instances in a private subnet.

**Key Features of NAT Instance:**
- **Customizable:** You can customize the instance to meet specific requirements.
- **Scalability:** Requires manual intervention to scale.
- **Management:** Requires management of instance lifecycle, including updates and monitoring.
- **High Availability:** High availability must be manually configured using scripts or services like Auto Scaling.

### Differences between NAT Gateway and NAT Instance

| Feature                | NAT Gateway                   | NAT Instance                  |
|------------------------|-------------------------------|-------------------------------|
| **Management**         | Managed by AWS                | Managed by the user           |
| **Scalability**        | Automatic scaling             | Manual scaling required       |
| **High Availability**  | Built-in high availability    | User must configure           |
| **Ease of Setup**      | Simple, managed setup         | Complex, user-managed setup   |
| **Cost**               | Pay per hour and data transfer| Pay per instance hour         |
| **Customizability**    | Limited customization         | Highly customizable           |

### Lab Session - Create a NAT Instance in AWS VPC

1. **Launch an EC2 Instance:**
   - Open the EC2 dashboard in the AWS Management Console.
   - Launch a new EC2 instance and select an Amazon Linux 2 AMI.
   - Choose an instance type, such as t2.micro.
   - In the Configure Instance Details section, place the instance in a public subnet.
   - Enable auto-assign public IP.
   - Add a new tag with a key of "Name" and a value of "NAT Instance".
   - Choose an appropriate security group (ensure SSH and HTTP/HTTPS are allowed).
   - Review and launch the instance.

2. **Enable IP Forwarding:**
   - Connect to the instance via SSH.
   - Enable IP forwarding by running:
     ```bash
     sudo sysctl -w net.ipv4.ip_forward=1
     ```
   - Add the following to `/etc/sysctl.conf` to make this change permanent:
     ```bash
     net.ipv4.ip_forward = 1
     ```

3. **Configure NAT:**
   - Configure iptables for NAT by running:
     ```bash
     sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
     sudo iptables-save > /etc/sysconfig/iptables
     ```

4. **Update Route Tables:**
   - Navigate to the VPC dashboard.
   - Select the route table associated with the private subnet.
   - Add a new route with `0.0.0.0/0` as the destination and the NAT instance ID as the target.

### Lab Session - Create a NAT Gateway in AWS VPC

1. **Create a NAT Gateway:**
   - Navigate to the VPC dashboard.
   - In the left pane, choose "NAT Gateways".
   - Click on "Create NAT Gateway".
   - Select the public subnet in which the NAT Gateway will be created.
   - Allocate a new Elastic IP for the NAT Gateway.
   - Click on "Create NAT Gateway".

2. **Update Route Tables:**
   - Navigate to the Route Tables section in the VPC dashboard.
   - Select the route table associated with the private subnet.
   - Add a new route with `0.0.0.0/0` as the destination and the NAT Gateway ID as the target.

### Lab Session - Delete a NAT Gateway in AWS VPC

1. **Delete the NAT Gateway:**
   - Navigate to the VPC dashboard.
   - In the left pane, choose "NAT Gateways".
   - Select the NAT Gateway you wish to delete.
   - Click on "Actions" and choose "Delete NAT Gateway".
   - Confirm the deletion.

2. **Release the Elastic IP Address:**
   - Navigate to the Elastic IPs section in the EC2 dashboard.
   - Select the Elastic IP address associated with the deleted NAT Gateway.
   - Click on "Actions" and choose "Release Elastic IP address".
   - Confirm the release.

---

### Network Access Control List (NACL) in AWS VPC

**Network Access Control Lists (NACLs)** are an optional layer of security for your VPC that acts as a stateless firewall for controlling traffic in and out of one or more subnets. You can set up inbound and outbound rules to allow or deny traffic to and from individual subnets.

**Key Features of NACL:**
- **Stateless:** Responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).
- **Subnet-level Security:** Operates at the subnet level.
- **Rule Order:** Rules are evaluated in order, starting with the lowest numbered rule.
----
### Lab Session - Create a Network Access Control List (NACL) in AWS VPC

1. **Open the Amazon VPC Console:**
   - Navigate to the VPC Dashboard in the AWS Management Console.

2. **Create a NACL:**
   - In the left-hand navigation pane, choose **Network ACLs**.
   - Click on **Create Network ACL**.
   - Provide a name for your NACL and select the VPC where it will be created.
   - Click **Create**.

3. **Add Inbound and Outbound Rules:**
   - Select the newly created NACL.
   - Choose the **Inbound Rules** tab and click **Edit Inbound Rules**.
   - Add rules for inbound traffic, specifying rule number, type, protocol, port range, source, and whether to allow or deny traffic.
   - Repeat the process for the **Outbound Rules** tab to control outbound traffic.

4. **Associate Subnets:**
   - Choose the **Subnet Associations** tab.
   - Click **Edit Subnet Associations**.
   - Select the subnets to associate with the NACL and click **Save**.
----
### Security Group in AWS VPC

**Security Groups** act as a virtual firewall for your EC2 instances to control inbound and outbound traffic. Security groups operate at the instance level and are stateful.

**Key Features of Security Groups:**
- **Stateful:** If you allow an inbound request from an IP, the response is automatically allowed.
- **Instance-level Security:** Operates at the instance level.
- **Rules:** Rules can be added or removed without restarting the instance.
  
In AWS, you can attach security groups to a variety of services. Here’s a list of some key AWS services where security groups can be used:

1. **Amazon EC2** (Elastic Compute Cloud)
2. **Amazon RDS** (Relational Database Service)
3. **Amazon Redshift**
4. **Amazon ElastiCache**
5. **Amazon EMR** (Elastic MapReduce)
6. **Amazon ECS** (Elastic Container Service)
7. **Amazon EKS** (Elastic Kubernetes Service)
8. **AWS Lambda** (for VPC-enabled functions)
9. **Amazon Aurora**
10. **Amazon CloudMap**
11. **Amazon Neptune**
12. **Amazon Elastic File System (EFS)** (for mount targets)
13. **Amazon Lightsail**
14. **AWS App Runner**
15. **AWS Batch** (for jobs running in VPC)

Security groups are primarily associated with resources that operate within a Virtual Private Cloud (VPC). Always refer to the AWS documentation for the most up-to-date information regarding services and security group compatibility.
----
### Lab Session - Create a Security Group in AWS VPC

1. **Open the Amazon EC2 Console:**
   - Navigate to the EC2 Dashboard in the AWS Management Console.

2. **Create a Security Group:**
   - In the left-hand navigation pane, choose **Security Groups**.
   - Click on **Create Security Group**.
   - Provide a name and description for the security group.
   - Select the VPC where the security group will be created.
   - Click **Create**.

3. **Add Inbound and Outbound Rules:**
   - Select the newly created security group.
   - Choose the **Inbound Rules** tab and click **Edit Inbound Rules**.
   - Add rules for inbound traffic, specifying type, protocol, port range, and source.
   - Repeat the process for the **Outbound Rules** tab to control outbound traffic.
----
### Differences between NACL and Security Group in AWS VPC

| Feature             | NACL                                    | Security Group                         |
|---------------------|-----------------------------------------|----------------------------------------|
| **Level of Operation** | Subnet level                            | Instance level                         |
| **Stateless vs Stateful** | Stateless                                | Stateful                               |
| **Rule Evaluation** | Rules evaluated in order of priority    | All rules evaluated together           |
| **Default Behavior** | Allows all inbound and outbound traffic | Denies all inbound traffic by default; allows all outbound traffic by default |
| **Association**     | Can be associated with multiple subnets | Can be associated with multiple instances |

----
### VPC Flow Logs and How to Create Them

**VPC Flow Logs** capture information about the IP traffic going to and from network interfaces in your VPC. Flow logs can help you with monitoring and troubleshooting network connectivity.

**Key Features of VPC Flow Logs:**
- **Capture Network Traffic:** Logs all traffic going in and out of your VPC.
- **Integration:** Can be sent to CloudWatch Logs, S3, or a partner service.
- **Filtering:** You can filter logs based on traffic type.
----
### Lab Session - Enable VPC Flow Logs

1. **Open the Amazon VPC Console:**
   - Navigate to the VPC Dashboard in the AWS Management Console.

2. **Create a VPC Flow Log:**
   - In the left-hand navigation pane, choose **Your VPCs**.
   - Select the VPC for which you want to create a flow log.
   - Click on **Actions** and select **Create Flow Log**.

3. **Configure Flow Log Settings:**
   - Provide a name and select the destination (CloudWatch Logs or S3).
   - For CloudWatch Logs, select or create a new log group and IAM role.
   - For S3, provide the S3 bucket ARN.
   - Choose the filter (All, Accept, or Reject) and the maximum aggregation interval.

4. **Create Flow Log:**
   - Click **Create** to enable the flow log.
----
### Options for Configuring an AWS VPC

Configuring an AWS Virtual Private Cloud (VPC) involves several options and features to tailor your networking environment to your specific needs. Key options include:

- **CIDR Block**: Define the IP address range for your VPC.
- **Subnets**: Divide your VPC's CIDR block into smaller subnets.
- **Route Tables**: Control the routing of traffic within your VPC.
- **Internet Gateway**: Enable internet access for your VPC.
- **NAT Gateway/NAT Instance**: Allow instances in private subnets to access the internet.
- **Security Groups**: Define firewall rules at the instance level.
- **Network ACLs**: Define firewall rules at the subnet level.
- **DHCP Option Sets**: Configure DNS and other options.
- **VPC Peering**: Connect two VPCs together.
- **VPC Endpoints**: Provide private access to AWS services without using an internet gateway.
----
### DHCP Option Set in AWS VPC

**DHCP Option Sets** allow you to configure DHCP (Dynamic Host Configuration Protocol) options for your VPC. These options define domain name servers, domain names, and other DHCP options.

**Key Features of DHCP Option Sets:**
- **Domain Name Servers**: Specify DNS servers for instances in your VPC.
- **Domain Name**: Specify the domain name for your VPC.
- **NTP Servers**: Define Network Time Protocol servers.
- **NetBIOS**: Configure NetBIOS name servers and node types.

### DNS Hostnames and DNS Resolution in AWS VPC

- **DNS Hostnames**: Enable DNS hostnames to assign a DNS name to EC2 instances.
- **DNS Resolution**: Allow or disable DNS resolution within your VPC. If enabled, instances can use AWS provided DNS servers.
----
### VPC Endpoints in AWS and Types Available

**VPC Endpoints** allow you to privately connect your VPC to supported AWS services without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect.

**Types of VPC Endpoints:**
- **Gateway Endpoints**: For S3 and DynamoDB.
- **Interface Endpoints**: Use AWS PrivateLink to connect to services.
----
### Lab Session - Create a Gateway VPC Endpoint for S3 in AWS

1. **Open the Amazon VPC Console:**
   - Navigate to the VPC Dashboard in the AWS Management Console.

2. **Create a VPC Endpoint:**
   - In the left-hand navigation pane, choose **Endpoints**.
   - Click on **Create Endpoint**.

3. **Configure Endpoint Settings:**
   - Select **AWS services** for the service category.
   - Choose **com.amazonaws.<region>.s3** for the service name.
   - Select your VPC and route table.
   - Click **Create Endpoint**.

4. **Update Route Table:**
   - Ensure the route table associated with your subnets includes a route to the VPC endpoint.
----
### Prefix Lists in AWS VPC

- Prefix Lists in AWS VPC are collections of CIDR blocks that you can use to simplify the management of large sets of IP addresses in security groups, route tables, and other resources that require CIDR blocks.
- By using prefix lists, you can manage and reference multiple CIDR blocks as a single entity, reducing complexity and the potential for errors.

### Key Benefits of Prefix Lists
- **Simplification**: Manage multiple CIDR blocks as a single entity, making it easier to maintain and update.
- **Consistency**: Ensure consistent CIDR block usage across multiple resources.
- **Scalability**: Easily update the list of CIDR blocks without having to update each individual resource.

### Creating and Using Prefix Lists

#### Step 1: Create a Prefix List
1. **Navigate to the VPC Dashboard** in the AWS Management Console.
2. Select **"Prefix Lists"** from the left-hand menu.
3. Click **"Create prefix list"**.
4. Provide the following details:
   - **Name**: A descriptive name for the prefix list.
   - **Description**: An optional description for the prefix list.
   - **Max entries**: The maximum number of CIDR blocks that the prefix list can contain.
   - **CIDR blocks**: Add the CIDR blocks that you want to include in the prefix list.

5. Click **"Create prefix list"**.

#### Example
```plaintext
Name: MyPrefixList
Description: List of allowed IP ranges
Max entries: 10
CIDR blocks:
  - 192.168.1.0/24
  - 10.0.0.0/16
  - 172.16.0.0/12
```

#### Step 2: Update Route Tables to Use the Prefix List
1. **Navigate to Route Tables** in the VPC Dashboard.
2. Select the route table you want to update.
3. Click on the **"Routes"** tab, then click **"Edit routes"**.
4. Add a new route or update an existing route:
   - **Destination**: Select **"Prefix list"** and choose your created prefix list from the dropdown.
   - **Target**: Specify the target for the traffic (e.g., an internet gateway, NAT gateway, or VPC peering connection).

5. Click **"Save routes"**.

#### Example
```plaintext
Route Table ID: rtb-12345678
Routes:
- Destination: MyPrefixList (pl-12345678)
  Target: igw-12345678
```

#### Step 3: Update Security Groups to Use the Prefix List
1. **Navigate to Security Groups** in the EC2 Dashboard.
2. Select the security group you want to update.
3. Click on the **"Inbound rules"** or **"Outbound rules"** tab, then click **"Edit rules"**.
4. Add a new rule or update an existing rule:
   - **Type**: Select the type of traffic (e.g., HTTP, HTTPS, SSH).
   - **Protocol**: Choose the protocol (e.g., TCP, UDP, ICMP).
   - **Port range**: Specify the port range.
   - **Source**: Select **"Prefix list"** and choose your created prefix list from the dropdown.

5. Click **"Save rules"**.

#### Example
```plaintext
Security Group ID: sg-12345678
Inbound Rules:
- Type: SSH
  Protocol: TCP
  Port range: 22
  Source: MyPrefixList (pl-12345678)
```

### Managing Prefix Lists

#### Updating a Prefix List
1. Navigate to **"Prefix Lists"** in the VPC Dashboard.
2. Select the prefix list you want to update.
3. Click **"Edit"**.
4. Add, remove, or modify CIDR blocks as needed.
5. Click **"Save changes"**.

#### Deleting a Prefix List
1. Navigate to **"Prefix Lists"** in the VPC Dashboard.
2. Select the prefix list you want to delete.
3. Click **"Delete"**.
4. Confirm the deletion.

### Example Scenario

Suppose you have multiple VPCs and you want to allow specific IP ranges to access resources in these VPCs. Instead of manually adding these IP ranges to each security group or route table, you create a prefix list:

1. **Create a Prefix List**:
   - Name: `TrustedIPRanges`
   - CIDR blocks: `203.0.113.0/24`, `198.51.100.0/24`

2. **Update Security Groups**:
   - Add an inbound rule to allow SSH access from `TrustedIPRanges`.

3. **Update Route Tables**:
   - Add a route to allow traffic from `TrustedIPRanges` to a specific target.

By using prefix lists, you simplify the management of CIDR blocks and ensure consistent access controls across your AWS environment.

----
### Elastic Network Interface (ENI) in AWS

**Elastic Network Interfaces (ENIs)** are virtual network interfaces that can be attached to EC2 instances. They are used to manage network traffic, IP addresses, and security group rules.

**Key Features of ENIs:**
- **Flexible Attachment**: Can be attached or detached from instances without stopping them.
- **Multiple IP Addresses**: Can have one or more private IP addresses.
- **Security Groups**: Can be associated with multiple security groups.
----
### Lab Session - Create an ENI in AWS

1. **Open the Amazon EC2 Console:**
   - Navigate to the EC2 Dashboard in the AWS Management Console.

2. **Create an ENI:**
   - In the left-hand navigation pane, choose **Network Interfaces**.
   - Click on **Create Network Interface**.
   - Specify the subnet, description, and security group.
   - Click **Create**.

3. **Attach ENI to an Instance:**
   - Select the newly created ENI.
   - Click **Actions** and choose **Attach**.
   - Select the instance to attach the ENI to and click **Attach**.
----
### Lab Session - Delete an AWS VPC

1. **Open the Amazon VPC Console:**
   - Navigate to the VPC Dashboard in the AWS Management Console.

2. **Delete Subnets:**
   - In the left-hand navigation pane, choose **Subnets**.
   - Select the subnets within the VPC and click **Delete Subnet**.

3. **Delete Route Tables:**
   - In the left-hand navigation pane, choose **Route Tables**.
   - Select the route tables within the VPC and click **Delete Route Table**.

4. **Delete Security Groups:**
   - In the left-hand navigation pane, choose **Security Groups**.
   - Select the security groups within the VPC and click **Delete Security Group**.

5. **Delete Internet Gateway:**
   - In the left-hand navigation pane, choose **Internet Gateways**.
   - Select the internet gateway and click **Detach from VPC**.
   - Then, select the detached internet gateway and click **Delete**.

6. **Delete the VPC:**
   - In the left-hand navigation pane, choose **Your VPCs**.
   - Select the VPC you want to delete and click **Actions** > **Delete VPC**.

