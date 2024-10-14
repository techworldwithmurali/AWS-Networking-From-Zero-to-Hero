### Customer Gateway (CGW):

A **Customer Gateway (CGW)** is a physical device or software application at your end of the VPN connection. It represents the customer's side of the VPN connection to AWS. CGW can be a router, firewall, or VPN appliance that you configure to establish a VPN connection between your network and AWS.

### Virtual Private Gateway (VGW):

A **Virtual Private Gateway (VGW)** is an AWS-managed VPN concentrator that enables you to connect your AWS VPC (Virtual Private Cloud) to other networks securely. It acts as the AWS-side endpoint of a VPN connection. VGW allows you to establish VPN connections to your VPC from your on-premises network or another VPC.

### Site-to-Site VPN Connection:

A **Site-to-Site VPN Connection** is a type of VPN connection that connects your on-premises network (Customer Gateway) to your AWS VPC (Virtual Private Gateway) securely over the internet. It establishes an encrypted tunnel between the CGW and VGW, allowing communication between your on-premises resources and AWS resources.

### Lab Sessions:

1. **Installation of Openswan in Amazon Linux**:
   - Install Openswan, an open-source implementation of IPsec for Linux, on an Amazon Linux instance.
   - Configure necessary IPsec settings and ensure Openswan is operational.

2. **Creation of Customer Gateway (CGW)**:
   - Create a Customer Gateway in AWS console or using AWS CLI.
   - Specify the IP address of your CGW (your on-premises device) and other configuration details.

3. **Creation of Virtual Private Gateway**:
   - Create a Virtual Private Gateway in AWS console or using AWS CLI.
   - Attach the VGW to your VPC and configure routing settings if necessary.

4. **Site-to-Site VPN Connection using Openswan**:
   - Configure Openswan on your on-premises device (CGW) to establish a VPN connection with the VGW.
   - Ensure IPsec configurations match between CGW and VGW, including authentication methods and encryption settings.

5. **Test the Connectivity**:
   - Verify connectivity between your on-premises network and AWS resources over the Site-to-Site VPN Connection.
   - Test ping or other network traffic to ensure data can flow securely and reliably between the two networks.
