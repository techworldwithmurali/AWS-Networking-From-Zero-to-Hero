# Follow the steps below to set up Inter region TGW peering with the different AWS account.
![Lab - Setting up Inter region TGW peering with a different account in telugu - Moole Muralidhara Reddy - Telugu Devops Guru](https://github.com/telugudevopsguru/AWS-Networking-5-Days-Practical-Live-Workshop/blob/f0f4f4054c209735de73f1bb199d2dade33b8957/Day%203%20-%20AWS%20Transit%20Gateway/Images/Lab%20-%20Setting%20up%20Inter%20region%20TGW%20peering%20with%20a%20different%20account%20in%20telugu%20-%20Moole%20Muralidhara%20Reddy%20-%20Telugu%20Devops%20Guru.png)

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

## Step 5: Create the AWS VPC different account
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

## Step 9: Create the Transit Gateway in both AWS accounts for both regions.
```xml
Name: TGW-VPC-A
Name: TGW-VPC-B
```
## Step 10: Create the TGW attachments for VPC.
```xml
Name: TGW-VPC-A-Attachment
Name: TGW-VPC-B-Attachment
```
## Step 11: Create the TGW route table and associate it with the TGW attachments both regions.
```xml
Name: TGW-VPC-A-RouteTable
Name: TGW-VPC-B-RouteTable
```
## Step 12: Creation the TGW peering connection from VPC-A to VPC-B
```xml
Name: TGW-VPC-A-to-VPC-B-Peering
```
## Step 13: Accept the TGW peering connection in the destination region(different account).
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

####  Congratulations, you have successfully set up Creation of Inter region TGW peering with different account and tested connectivity between instances in the public subnets of each VPC.

####  Happy Learning
