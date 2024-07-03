# Follow the steps below to set up Inter region TGW peering with the same account.
![Lab - Setting up Inter region TGW peering with the same account in telugu - Moole Muralidhara Reddy - Telugu Devops Guru](https://github.com/telugudevopsguru/AWS-Networking-5-Days-Practical-Live-Workshop/blob/2e31adb9119fc19c09f8f6dbd282c1b6b4cbb1e1/Day%203%20-%20AWS%20Transit%20Gateway/Images/Lab%20-%20Setting%20up%20Inter%20region%20TGW%20peering%20with%20the%20same%20account%20in%20telugu%20-%20Moole%20Muralidhara%20Reddy%20-%20Telugu%20Devops%20Guru.png)

## Step 1: Create the AWS VPC
```xml
Name: VPC-A in US East (N. Virginia) us-east-1
CIDR : 10.0.0.0/16
```
## Step 2: Create a public subnet with
```xml
CIDR 10.0.1.0/24
Name: VPC-A-Public-subnet-1a.
```
## Step 3: Create an internet gateway and attach to VPC-A
```xml
Name: VPC-A-IGW.
```
## Step 4: Create a route table and name it VPC-A-RouteTable and attach the public subnet to this RouteTable.

## Step 5: Create the AWS VPC
```xml
Name: VPC-B in US West (Oregon) us-west-2
CIDR : 192.168.0.0/16
```
## Step 6: Create a public subnet with
```xml
CIDR 192.168.1.0/24
Name: VPC-B-Public-subnet-1a
```
## Step 7: Create an internet gateway and attach to VPC-B
```xml
Name: VPC-B-IGW.
```
## Step 8: Create a route table and name it VPC-B-RouteTable and attach the public subnet to this RouteTable.

## Step 9: Create the TGW for both regions
```xml
Name: TGW-VPC-A
Name: TGW-VPC-B
```
## Step 10: Create the TGW attachments for both VPC's.
```xml
Name: TGW-VPC-A-Attachment
Name: TGW-VPC-B-Attachment
```
## Step 11: Create the TGW route table and associate it with the TGW attachments.
```xml
Name: TGW-VPC-A-RouteTable
Name: TGW-VPC-B-RouteTable
```
## Step 12: Creation the TGW peering connection from VPC-A to VPC-B
```xml
Name: TGW-VPC-A-to-VPC-B-Peering
```
## Step 13: Accept the TGW peering connection in the destination region.
## Step 14: Create the static route VPC-B's CIDR block to the TGW peering connection of VPC-A account in TGW RouteTable.
```xml
VPC-B CIDR : 192.168.0.0/16
```
## Step 15: Create the static route VPC-A's CIDR block to the TGW peering connection of VPC-B account in TGW RouteTable.
```xml
VPC-A CIDR : 10.0.0.0/16
```
## Step 16: Update the route tables in both VPCs to allow traffic to the other VPC.

+ In VPC-A route table, add a route for VPC-B's CIDR block to the TGW connection.
```xml
VPC-B CIDR : 192.168.0.0/16
```
+ In VPC-B route table, add a route for VPC-A's CIDR block to the TGW connection.
```xml
VPC-A CIDR : 10.0.0.0/16
```
## Step 17: Launch an EC2 instance in both VPC's public subnets.

## Step 18: Update the Security Group Inbound rules for both instances to allow ICMP traffic.

## Step 19: Test the connectivity between the instances using the ping command.

####  Congratulations, you have successfully set up Inter region TGW peering with same account and tested connectivity between instances in the public subnets of each VPC.

####  Happy Learning
