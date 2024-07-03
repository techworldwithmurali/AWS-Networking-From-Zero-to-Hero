# Follow the steps below to set up Intra region TGW peering with the different AWS account.
![Lab - Setting up Intra region TGW peering with a different account in telugu - Moole Muralidhara Reddy - Telugu Devops Guru](https://github.com/telugudevopsguru/AWS-Networking-5-Days-Practical-Live-Workshop/blob/5d84d7b6a6fa6efa50664498a3844c9fee1d218a/Day%203%20-%20AWS%20Transit%20Gateway/Images/Lab%20-%20Setting%20up%20Intra%20region%20TGW%20peering%20with%20a%20different%20account%20in%20telugu%20-%20Moole%20Muralidhara%20Reddy%20-%20Telugu%20Devops%20Guru.png)

## Step 1: Create the AWS VPC
Name: VPC-A in US East (N. Virginia) us-east-1
CIDR : 10.0.0.0/16

## Step 2: Create a public subnet with
CIDR 10.0.1.0/24
Name: VPC-A-Public-subnet-1a.

## Step 3: Create an internet gateway and attach to VPC-A
Name: VPC-A-IGW.

## Step 4: Create a route table and name it VPC-A-RouteTable and attach the public subnet to this RouteTable.

## Step 5: Create the AWS VPC different account
Name: VPC-B in US East (N. Virginia) us-east-1
CIDR : 192.168.0.0/16

## Step 6: Create a public subnet with
CIDR 192.168.1.0/24
Name: VPC-B-Public-subnet-1a

## Step 7: Create an internet gateway and attach to VPC-B
Name: VPC-B-IGW

## Step 8: Create a route table and name it VPC-B-RouteTable and attach the public subnet to this RouteTable.

## Step 9: Create the TGW
```xml
Name: TGW-VPC
```
## Step 10: Create the TGW attachments for VPC-A.
```xml
Name: TGW-VPC-A-Attachment
```
## Step 11: Create the TGW route table and associate it with the TGW attachments of VPC-A.
```xml
Name: TGW-VPC-RouteTable
Associate with the TGW-VPC-A-Attachment.
```
## Step 12: Create the propagation for TGW-VPC-A-Attachment in the TGW route table.
## Step 13: Share the TGW with destination account using AWS RAM.
```xml
Name: TGW-VPC
```
## Step 14: Accept the TGW in the AWS RAM destination account.

## Step 15: Create the TGW attachments for VPC-B and accept the request in source account
```xml
Name: TGW-VPC-B-Attachment
```
## Step 16: In TGW RouteTable associate it with the TGW attachments of VPC-B in source account.
```xml
Name: TGW-VPC-RouteTable
Associate with the TGW-VPC-B-Attachment.
```
## Step 17: Create the propagation for TGW-VPC-B-Attachment in the TGW route table.
## Step 18: Update the route tables in both VPCs to allow traffic to the other VPC.

+ In VPC-A route table, add a route for VPC-B's CIDR block to the TGW connection.
```xml
VPC-B CIDR : 192.168.0.0/16
```
+ In VPC-B route table, add a route for VPC-A's CIDR block to the TGW connection.
```xml
VPC-A CIDR : 10.0.0.0/16
```
## Step 19: Launch an EC2 instance in both VPC's public subnets.

## Step 20: Update the Security Group Inbound rules for both instances to allow ICMP traffic.

## Step 21: Test the connectivity between the instances using the ping command.

####  Congratulations, you have successfully set up Intra-region VPC peering with different accounts and tested connectivity between instances in the public subnets of each VPC..

### # Happy Learning
