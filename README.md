### What is AWS Cloud WAN?

AWS Cloud WAN (Wide Area Network) is a managed service that simplifies the setup, management, and operation of a global network connecting your data centers, branch offices, and cloud environments. AWS Cloud WAN uses AWS's global backbone to provide high availability, scalability, and secure connectivity across your network, making it easier to manage network operations and policies through a single console and set of APIs.

### Global and Core Network Key Concepts

**Global Network:**
- A global network is the top-level construct in AWS Cloud WAN that represents the entire network infrastructure. It includes all the regions, VPCs, and other network resources that are part of your organization's network.

**Core Network:**
- A core network is a logical grouping of network segments, regions, and network policies within the global network. It provides the centralized control point for managing the routing and security policies for the entire network.

### Get Started with AWS Cloud WAN

#### Create a Global Network

1. **Open the AWS Cloud WAN Console:**
   - Navigate to the AWS Cloud WAN console in the AWS Management Console.

2. **Create a Global Network:**
   - Click on "Create Global Network."
   - Provide a name and description for your global network.
   - Click "Create Global Network" to complete the process.

#### Create a Core Network and Core Network Policy

1. **Create a Core Network:**
   - In the AWS Cloud WAN console, go to the global network you created.
   - Click on "Create Core Network."
   - Provide a name and description for your core network.
   - Select the regions to include in the core network.
   - Click "Create Core Network" to finalize the setup.

2. **Create a Core Network Policy:**
   - In the core network, click on "Create Core Network Policy."
   - Define the routing policies, segmentation, and security rules for the core network.
   - Use policy templates or create custom policies as needed.
   - Save and apply the core network policy to enforce it across the network.

### Work with Attachments

Attachments in AWS Cloud WAN refer to connecting various network resources such as Transit Gateways, VPCs, and VPNs to the core network.

#### Add a Transit Gateway Route Table Attachment

1. **Open the AWS Cloud WAN Console:**
   - Navigate to the core network where you want to add the attachment.

2. **Add a Transit Gateway Route Table Attachment:**
   - Click on "Add Attachment" and select "Transit Gateway Route Table."
   - Choose the Transit Gateway and the specific route table to attach.
   - Specify any additional configuration settings required.
   - Click "Add Attachment" to complete the process.

#### Add a VPC Attachment

1. **Open the AWS Cloud WAN Console:**
   - Navigate to the core network where you want to add the attachment.

2. **Add a VPC Attachment:**
   - Click on "Add Attachment" and select "VPC."
   - Choose the VPC you want to attach to the core network.
   - Specify the subnets and any additional configuration settings.
   - Click "Add Attachment" to complete the process.

#### Add a Site-to-Site VPN Attachment

1. **Open the AWS Cloud WAN Console:**
   - Navigate to the core network where you want to add the attachment.

2. **Add a Site-to-Site VPN Attachment:**
   - Click on "Add Attachment" and select "Site-to-Site VPN."
   - Configure the VPN settings, including the Customer Gateway and VPN connection options.
   - Specify the routing and security policies for the VPN connection.
   - Click "Add Attachment" to complete the process.

### Summary

AWS Cloud WAN simplifies the management of a global network by providing a unified console and API for network operations. Key concepts include the global network and core network, which represent the overall network infrastructure and logical grouping of network resources, respectively. Getting started involves creating a global network, a core network, and defining core network policies. Attachments such as Transit Gateways, VPCs, and Site-to-Site VPNs can be connected to the core network to extend its reach and functionality.
