# Create a Network Access Control List (NACL)

![Lab - Setting up AWS NACL - Moole Muralidhara Reddy - Tech World With Murali](https://github.com/techworldwithmurali/AWS-Networking-From-Zero-to-Hero/blob/main/AWS%20VPC/images/Setting%20up%20AWS%20NACL-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)


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
#### Step 11: Create and Add the Infra-Nat-Gateway-us-east-1a NAT Gateway route to the Infra-Private-RouteTable-us-east-1a route table.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : NAT Gateway ID
```

#### Step 12: Create and Add the Infra-Nat-Gateway-us-east-1b NAT Gateway route to the Infra-Private-RouteTable-us-east-1b route table.

```xml
Route Entry

Destination : 0.0.0.0/0
Target : NAT Gateway ID
```
#### Step 13: Create the Public NACL
```xml
Name: Infra-Public-NACL
```
####  Step 14: Attach the Public Subnets to the Public NACL
####  Step 15: Create the Public NACL
```xml
Name: Infra-Private-NACL
```
####  Step 16: Attach the private , app and  data  Subnets to the Private  NACL

#### Step 17: Add the Inbound rules and test them
####  Congratulations! You have successfully set up and tested the AWS NACL.
