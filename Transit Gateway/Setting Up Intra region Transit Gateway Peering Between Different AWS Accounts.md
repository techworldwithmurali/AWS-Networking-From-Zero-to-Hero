# Follow the steps below to Setting Up Intra region Transit Gateway Peering Between Different AWS Accounts.
![Lab - Setting up Intra region TGW peering with a different account - Moole Muralidhara Reddy - Tech World with Murali](https://github.com/techworldwithmurali/AWS-Networking-From-Zero-to-Hero/blob/main/Transit%20Gateway/images/Setting%20Up%20Intra%20region%20Transit%20Gateway%20Peering%20Between%20Different%20AWS%20Accounts%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)

#### Step 1: Create the Infra VPC
```xml
Name: Infra-VPC in US East (N. Virginia) us-east-1
CIDR : 10.70.0.0/16
```
#### Step 2: Create a 2 public subnets with
```xml
CIDR :10.70.8.0/21
Name: Infra-public-subnet-1a

CIDR :10.70.16.0/21
Name: Infra-public-subnet-1b

```
#### Step 3: Create a 2 private subnets with
```xml
CIDR :10.70.80.0/21
Name: Infra-private-subnet-1a

CIDR :10.70.88.0/21
Name: Infra-private-subnet-1b

```

#### Step 4: Create a 2 app subnets with
```xml
CIDR :10.70.144.0/21
Name: Infra-app-subnet-1a

CIDR :10.70.162.0/21
Name: Infra-app-subnet-1b

```
#### Step 5: Create a 2 data subnets with
```xml
CIDR :10.70.168.0/21
Name: Infra-data-subnet-1a

CIDR :10.70.176.0/21
Name: Infra-data-subnet-1b

```

#### Step 6: Create an internet gateway and attach to Infra VPC
```xml
Name: Infra-VPC-IGW
```
#### Step 7: Create a route table and name it Infra-VPC-Public-RouteTable and attach the public subnets to this RouteTable.
```xml
Name: Infra-Public-RouteTable
```

#### Step 8: Create a route table and name it Infra-Private-RouteTable-us-east-1a, then attach the private, app, and data subnets in Availability Zone us-east-1a to this route table.

```xml
Name: Infra-Private-RouteTable-us-east-1a
```

#### Step 9: Create a route table and name it Infra-Private-RouteTable-us-east-1b, then attach the private, app, and data subnets in Availability Zone us-east-1b to this route table.

```xml
Name: Infra-Private-RouteTable-us-east-1b
```

#### Step 10: Add the Internet Gateway route to the Infra-Public-RouteTable

```xml
Route Entry

Destination : 0.0.0.0/0
Target : Internet Gateway ID
```

#### Step 11: Create the NAT Gateway in the public subnet us-east-1a Availability Zone and name it:
```xml
Infra-Nat-Gateway-us-east-1a
```

#### Step 12: Create the NAT Gateway in the public subnet us-east-1b Availability Zone and name it:
```xml
Infra-Nat-Gateway-us-east-1b
```

#### Step 13: Add the Infra-Nat-Gateway-us-east-1a NAT Gateway route to the Infra-Private-RouteTable-us-east-1a route table.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : NAT Gateway ID
```

#### Step 14: Add the Infra-Nat-Gateway-us-east-1b NAT Gateway route to the Infra-Private-RouteTable-us-east-1b route table.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : NAT Gateway ID
```

#### Step 15: Create the Prod VPC in different AWS account
```xml
Name: Prod-VPC in US East (N. Virginia) us-east-1
CIDR : 10.60.0.0/16
```
#### Step 16: Create a 2 public subnets with
```xml
CIDR :10.60.8.0/21
Name: Prod-public-subnet-1a

CIDR :10.60.16.0/21
Name: Prod-public-subnet-1b

```
#### Step 17: Create a 2 private subnets with
```xml
CIDR :10.60.80.0/21
Name: Prod-private-subnet-1a

CIDR :10.60.88.0/21
Name: Prod-private-subnet-1b

```

#### Step 18: Create a 2 app subnets with
```xml
CIDR :10.60.144.0/21
Name: Prod-app-subnet-1a

CIDR :10.60.162.0/21
Name: Prod-app-subnet-1b

```
#### Step 19: Create a 2 data subnets with
```xml
CIDR :10.60.168.0/21
Name: Prod-data-subnet-1a

CIDR :10.60.176.0/21
Name: Prod-data-subnet-1b

```

#### Step 20: Create an internet gateway and attach to Prod-VPC
```xml
Name: Prod-VPC-IGW
```
#### Step 21: Create a route table and name it Prod-VPC-Public-RouteTable and attach the public subnets to this RouteTable.
```xml
Name: Prod-Public-RouteTable
```

#### Step 22: Create a route table and name it Prod-Private-RouteTable-us-east-1a, then attach the private, app, and data subnets in Availability Zone us-east-1a to this route table.

```xml
Name: Prod-Private-RouteTable-us-east-1a
```

#### Step 23: Create a route table and name it Prod-Private-RouteTable-us-east-1b, then attach the private, app, and data subnets in Availability Zone us-east-1b to this route table.

```xml
Name: Prod-Private-RouteTable-us-east-1b
```

#### Step 24: Add the Internet Gateway route to the Prod-Public-RouteTable

```xml
Route Entry

Destination : 0.0.0.0/0
Target : Internet Gateway ID
```

#### Step 25: Create the NAT Gateway in the public subnet us-east-1a Availability Zone and name it:
```xml
Prod-Nat-Gateway-us-east-1a
```

#### Step 26: Create the NAT Gateway in the public subnet us-east-1b Availability Zone and name it:
```xml
Prod-Nat-Gateway-us-east-1b
```

#### Step 27: Add the Prod-Nat-Gateway-us-east-1a NAT Gateway route to the Prod-Private-RouteTable-us-east-1a route table.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : NAT Gateway ID
```

#### Step 28: Add the Prod-Nat-Gateway-us-east-1b NAT Gateway route to the Prod-Private-RouteTable-us-east-1b route table.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : NAT Gateway ID
```

### Step 29: Create the TGW
```xml
Name: infra-vpc-to-prod-vpc-tgw
```
#### Step 30: Create the TGW attachments for Infra VPC and select the subnets for the TGW
```xml
Name: Infra-VPC-TGW-Attachment
```
#### Step 31: Create the TGW route table and associate it with the TGW attachments of Infra VPC.

```xml
Name: infra-vpc-to-prod-vpc-tgw-routetable
Infra-VPC-TGW-Attachment
```
#### Step 32: Create the propagation for Infra-VPC-TGW-Attachment in the TGW route table.

#### Step 33: Share the TGW with destination account using AWS RAM.

```xml
infra-vpc-to-prod-vpc-tgw
```

#### Step 34: Accept the TGW in the AWS RAM destination account.

Create the TGW attachments for Prod and accept the request in source account

```xml
Name: Prod-VPC-TGW-Attachment
```

#### Step 35: In TGW RouteTable associate it with the TGW attachments of Prod VPC in source account.

```xml
Name: TGW-VPC-RouteTable
Associate with the TGW-VPC-B-Attachment.
```

#### Step 35: Create the propagation for Prod-VPC-TGW-Attachment in the TGW route table.

#### Step 36: Update the route tables in both VPCs to allow traffic to the other VPC.

+ Below the route tables, add a route for the PROD CIDR block to the **Infra-VPC-TGW-Attachment** connection:

```xml
Route Tables:
Infra-Public-RouteTable
Infra-Private-RouteTable-us-east-1a
Infra-Private-RouteTable-us-east-1b

```
```xml
Prod CIDR : 10.60.0.0/16
```

+ Below the route tables, add a route for the Infra CIDR block to the **Prod-VPC-TGW-Attachment** connection:

```xml
Route Tables:
Prod-Public-RouteTable
Prod-Private-RouteTable-us-east-1a
Prod-Private-RouteTable-us-east-1b

```
```xml
Infra CIDR : 10.70.0.0/16
```

#### Step 37: Launch an EC2 instance in both VPC's public subnets.

#### Step 38: Update the Security Group Inbound rules for both instances to allow ICMP traffic.

#### Step 39: Test the connectivity between the instances using the ping command.

####  Congratulations, you have successfully set up Intra region TGW peering with different accounts and tested connectivity between instances in the public subnets of each VPC.

#####  Happy Learning
