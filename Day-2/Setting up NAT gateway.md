
# Setting up NAT Gateway
![Lab - Setting up NAT Gateway in telugu - Moole Muralidhara Reddy - Telugu Devops Guru](https://github.com/telugudevopsguru/AWS-Networking-5-Days-Practical-Live-Workshop/blob/7a8eeaf036f98059df8ead4c9559204aa30d4eee/Day%201-%20%20AWS%20VPC%20Overview/Images/Lab%20-%20Setting%20up%20NAT%20Gateway%20in%20telugu%20-%20Moole%20Muralidhara%20Reddy%20-%20Telugu%20Devops%20Guru.png)
## Step 1: Create the AWS VPC
```xml
Name: Murali-VPC in US East (N. Virginia) us-east-1
CIDR : 10.100.0.0/16
```
## Step 2: Create a 2 public subnets with
```xml
CIDR :10.100.8.0/21
Name: murali-public-subnet-1a

CIDR :10.100.16.0/21
Name: murali-public-subnet-1b

```
## Step 3: Create a 2 private subnets with
```xml
CIDR :10.100.80.0/21
Name: murali-private-subnet-1a

CIDR :10.100.88.0/21
Name: murali-private-subnet-1b

```

## Step 4: Create a 2 app subnets with
```xml
CIDR :10.100.144.0/21
Name: murali-app-subnet-1a

CIDR :10.100.162.0/21
Name: murali-app-subnet-1b

```
## Step 4: Create a 2 data subnets with
```xml
CIDR :10.100.168.0/21
Name: murali-data-subnet-1a

CIDR :10.100.176.0/21
Name: murali-data-subnet-1b

```

## Step 5: Create an internet gateway and attach to Murali-VPC
```xml
Name: Murali-VPC-IGW
```
## Step 6: Create a route table and name it Murali-VPC-Public-RouteTable and attach the public subnets to this RouteTable.
```xml
Name: Murali-VPC-Public-RouteTable
```

## Step 7: Create a route table and name it Murali-VPC-Private-RouteTable and attach the private,app,data subnets to this RouteTable.

```xml
Name: Murali-VPC-Private-RouteTable
```

## Step 8: Add the Internet Gateway route to the Public RouteTable.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : Internet Gateway ID
```
## Step 9: Create the NAT Gateway in the public subnet
```xml
Murali-VPC-Nat-Gateway
```
## Step 10: Add the Nat Gateway route to the Private RouteTable.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : NAT Gateway ID
```

## Step 11: Launch a Linux EC2 instance in the private subnet.
## Step 12: SSH into the Linux EC2 instance using the private IP address from the public instance (Bastion Host).
+ Note: Once connected to the instance, try to ping an external IP address (e.g., 8.8.8.8) or access the internet by using commands like "ping," "curl," or "wget." If the NAT Gateway is configured correctly, you should be able to access the internet from the private EC2 instance.

#### Congratulations! You have successfully set up the NAT Gateway.
