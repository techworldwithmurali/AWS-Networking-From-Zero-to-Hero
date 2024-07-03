# Setting up Inter region VPC peering with different account
![Lab - Setting up Inter region VPC peering with a different account in telugu - Moole Muralidhara Reddy - Telugu Devops Guru](https://github.com/telugudevopsguru/AWS-Networking-5-Days-Practical-Live-Workshop/blob/b16bda887c7c506c15f7dad8d4d68dc49a679a62/Day%202%20-%20AWS%20VPC%20Peering/Images/Lab%20-%20Setting%20up%20Inter%20region%20VPC%20peering%20with%20a%20different%20account%20in%20telugu%20-%20Moole%20Muralidhara%20Reddy%20-%20Telugu%20Devops%20Guru.png)

## Step 1: Create the AWS VPC
```xml
Name: VPC-A in US East (N. Virginia) us-east-1
CIDR : 10.0.0.0/16
```
## Step 2: Create a public subnet with
```xml
CIDR 10.0.1.0/24
Name: VPC-A-Public-subnet-1a
```
## Step 3: Create an internet gateway and attach to VPC-A
```xml
Name: VPC-A-IGW.
```
## Step 4: Create a route table and name it VPC-A-RouteTable and attach the public subnet to this RouteTable.
```xml
Name : VPC-A-RouteTable
Subnet Name: VPC-A-Public-subnet-1a
```
## Step 5: Create the AWS VPC in different account
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
```xml
Name : VPC-B-RouteTable
Subnet Name: VPC-A-Public-subnet-1a
```
## Step 9: Create the VPC peering
```xml
Name: VPC-A-to-VPC-B-Peering
```
## Step 10: Accept the Peering connection in both VPCs.

## Step 11: Update the route tables in both VPCs to allow traffic to the other VPC.
+ In VPC-A route table, add a route for VPC-B's CIDR block to the VPC-A-to-VPC-B-Peering connection.
```xml
VPC-B CIDR : 192.168.0.0/16
```
+ In VPC-B route table, add a route for VPC-A's CIDR block to the VPC-A-to-VPC-B-Peering connection.
```xml
VPC-A CIDR : 10.0.0.0/16
```
## Step 12: Launch an EC2 instance in both VPC's public subnets.

## Step 13: Update the Security Group Inbound rules for both instances to allow ICMP traffic.

## Step 14: Test the connectivity between the instances using the ping command.

####  Congratulations, you have successfully set up VPC peering between two VPCs and tested connectivity between instances in the public subnets of each VPC.

####  Happy Learning
