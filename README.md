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
