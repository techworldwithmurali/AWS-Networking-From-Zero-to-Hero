# Follow the steps below to set up Inter region TGW peering with the same account.
![Lab - Setting up Inter region TGW peering with the same account in telugu - Moole Muralidhara Reddy - Telugu Devops Guru](https://github.com/telugudevopsguru/AWS-Networking-5-Days-Practical-Live-Workshop/blob/2e31adb9119fc19c09f8f6dbd282c1b6b4cbb1e1/Day%203%20-%20AWS%20Transit%20Gateway/Images/Lab%20-%20Setting%20up%20Inter%20region%20TGW%20peering%20with%20the%20same%20account%20in%20telugu%20-%20Moole%20Muralidhara%20Reddy%20-%20Telugu%20Devops%20Guru.png)

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

#### Step 9: Create a route table and name it Infra-Private-RouteTable-us-east-1b, then attach the private, app, and data subnets in Availability Zone us-east-1a to this route table.

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

#### Step 15: Create the Prod VPC in same aws account
```xml
Name: Prod-VPC in US East (Oregon) us-west-2
CIDR : 10.60.0.0/16
```
#### Step 16: Create a 2 public subnets with
```xml
CIDR :10.60.8.0/21
Name: Prod-public-subnet-2a

CIDR :10.60.16.0/21
Name: Prod-public-subnet-2b

```
#### Step 17: Create a 2 private subnets with
```xml
CIDR :10.60.80.0/21
Name: Prod-private-subnet-2a

CIDR :10.60.88.0/21
Name: Prod-private-subnet-2b

```

#### Step 18: Create a 2 app subnets with
```xml
CIDR :10.60.144.0/21
Name: Prod-app-subnet-2a

CIDR :10.60.162.0/21
Name: Prod-app-subnet-2b

```
#### Step 19: Create a 2 data subnets with
```xml
CIDR :10.60.168.0/21
Name: Prod-data-subnet-2a

CIDR :10.60.176.0/21
Name: Prod-data-subnet-2b

```

#### Step 20: Create an internet gateway and attach to Prod-VPC
```xml
Name: Prod-VPC-IGW
```
#### Step 21: Create a route table and name it Prod-VPC-Public-RouteTable and attach the public subnets to this RouteTable.
```xml
Name: Prod-Public-RouteTable
```

#### Step 22: Create a route table and name it Prod-Private-RouteTable-us-west-2a, then attach the private, app, and data subnets in Availability Zone us-west-2a to this route table.

```xml
Name: Prod-Private-RouteTable-us-west-2a
```

#### Step 23: Create a route table and name it Prod-Private-RouteTable-us-west-2b, then attach the private, app, and data subnets in Availability Zone us-west-2a to this route table.

```xml
Name: Prod-Private-RouteTable-us-west-2b
```

#### Step 24: Add the Internet Gateway route to the Prod-Public-RouteTable

```xml
Route Entry

Destination : 0.0.0.0/0
Target : Internet Gateway ID
```

#### Step 25: Create the NAT Gateway in the public subnet us-west-2a Availability Zone and name it:
```xml
Prod-Nat-Gateway-us-west-2a
```

#### Step 26: Create the NAT Gateway in the public subnet us-west-2b Availability Zone and name it:
```xml
Prod-Nat-Gateway-us-west-2b
```

#### Step 27: Add the Prod-Nat-Gateway-us-west-2a NAT Gateway route to the Prod-Private-RouteTable-us-west-2a route table.

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

#### Step 29: Create the TGW for both regions
```xml
For us-east-1 - Name: Infra-VPC-TGW
For us-west-2 - Name: Prod-VPC-TGW
```
#### Step 30: Create the TGW attachments for both VPC's.
```xml
For us-east-1 - Name: Infra-VPC-TGW-Attachment
For us-west-2 - Name: Prod-VPC-TGW-Attachment
```
#### Step 31: Create the TGW route table and associate it with the TGW attachments.
```xml
For us-east-1 - Name: Infra-VPC-TGW-RouteTable
For us-east-1 - Name: Prod-VPC-TGW-RouteTable
```
#### Step 32: Create the TGW peering connection from Infra TGW to Prod TGW
```xml
Name: infra-vpc-to-prod-vpc-tgw-peering
```
#### Step 33: Accept the TGW peering connection in the destination region(us-west-2).
#### Step 34: Create the static route Prod VPC CIDR block to the TGW peering connection of Infra VPC account in TGW RouteTable.
```xml
Route Table name - Infra-VPC-TGW-RouteTable
Prod VPC CIDR : 10.60.0.0/16
```
#### Step 35: Create the static route Infra CIDR block to the TGW peering connection of Prod account in TGW RouteTable.
```xml
Infra VPC CIDR : 10.70.0.0/16
```
##### Step 36: Update the route tables in both VPCs to allow traffic to the other VPC.

+ Below the route tables, add a route for the PROD CIDR block to the **Infra-VPC-TGW-Attachment** connection:

```xml
Route Tables:
Infra-Public-RouteTable
Infra-Private-RouteTable-us-east-1a
Infra-Private-RouteTable-us-east-1b

```
```xml
Prod VPC CIDR : 10.60.0.0/16
```

+ Below the route tables, add a route for the Infra CIDR block to the **Prod-VPC-TGW-Attachment** connection:

```xml
Route Tables:
Prod-Public-RouteTable
Prod-Private-RouteTable-us-east-1a
Prod-Private-RouteTable-us-east-1b

```
```xml
Infra VPC CIDR : 10.70.0.0/16
```

#### Step 37: Launch an EC2 instance in both VPC's public subnets.

#### Step 38: Update the Security Group Inbound rules for both instances to allow ICMP traffic.

#### Step 39: Test the connectivity between the instances using the ping command.

###### Congratulations, you have successfully set up Inter region TGW peering with same account and tested connectivity between instances in the public subnets of each VPC.

###### Happy Learning
