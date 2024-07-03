### Network Access Control List (NACL) in AWS VPC

**Network Access Control Lists (NACLs)** are an optional layer of security for your VPC that acts as a stateless firewall for controlling traffic in and out of one or more subnets. You can set up inbound and outbound rules to allow or deny traffic to and from individual subnets.

**Key Features of NACL:**
- **Stateless:** Responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).
- **Subnet-level Security:** Operates at the subnet level.
- **Rule Order:** Rules are evaluated in order, starting with the lowest numbered rule.

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

### Security Group in AWS VPC

**Security Groups** act as a virtual firewall for your EC2 instances to control inbound and outbound traffic. Security groups operate at the instance level and are stateful.

**Key Features of Security Groups:**
- **Stateful:** If you allow an inbound request from an IP, the response is automatically allowed.
- **Instance-level Security:** Operates at the instance level.
- **Rules:** Rules can be added or removed without restarting the instance.

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

### Differences between NACL and Security Group in AWS VPC

| Feature             | NACL                                    | Security Group                         |
|---------------------|-----------------------------------------|----------------------------------------|
| **Level of Operation** | Subnet level                            | Instance level                         |
| **Stateless vs Stateful** | Stateless                                | Stateful                               |
| **Rule Evaluation** | Rules evaluated in order of priority    | All rules evaluated together           |
| **Default Behavior** | Allows all inbound and outbound traffic | Denies all inbound traffic by default; allows all outbound traffic by default |
| **Association**     | Can be associated with multiple subnets | Can be associated with multiple instances |

### VPC Flow Logs and How to Create Them

**VPC Flow Logs** capture information about the IP traffic going to and from network interfaces in your VPC. Flow logs can help you with monitoring and troubleshooting network connectivity.

**Key Features of VPC Flow Logs:**
- **Capture Network Traffic:** Logs all traffic going in and out of your VPC.
- **Integration:** Can be sent to CloudWatch Logs, S3, or a partner service.
- **Filtering:** You can filter logs based on traffic type.

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

### Summary

**Network Access Control Lists (NACLs)** and **Security Groups** provide security at different levels in your VPC. NACLs operate at the subnet level and are stateless, while security groups operate at the instance level and are stateful. **VPC Flow Logs** capture and log traffic information for monitoring and troubleshooting purposes. The lab sessions guide you through the creation and management of these security features and logs in AWS.
