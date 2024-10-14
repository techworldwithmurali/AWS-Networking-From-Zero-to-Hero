# Setting Up AWS Site-to-Site VPN Connection:
![Lab - Setting up a Site-to-Site VPN Connection in telugu - Moole Muralidhara Reddy - Telugu Devops Guru](https://github.com/telugudevopsguru/AWS-Networking-5-Days-Practical-Live-Workshop/blob/9731d7265f8f80acc7702f8ddebdfda9639ced46/Day%204%20-%20%20Site%20to%20Site%20VPN/Images/Lab%20-%20Setting%20up%20a%20Site-to-Site%20VPN%20Connection%20in%20telugu%20-%20Moole%20Muralidhara%20Reddy%20-%20Telugu%20Devops%20Guru.png)

You can follow the steps below to set up the AWS Site-to-Site VPN Connection.
#### CIDR details for AWS and On-Premises.
```xml
AWS VPC CIDR : - 10.70.0.0/16
On-Premises VPC CIDR : - 192.168.0.0/16
```
####  Step 1: Launch the AWS EC2 instance for installing OpenSwan in On-Premises VPC.
```xml
Name: OpenSwan-Server
```
##### Install the openswan in AWs EC2 instance using below command
```xml
yum install openswan -y
ipsec --version
```
#### Step 2: Create the AWS Customer Gateway in AWS Side.
```xml
Name: techworldwithmurali-CGW
```
#### Step 3: Create the Virtual Private Gateway and attach it to the VPC in AWS Side.
```xml
Name: techworldwithmurali-VPG
```
#### Step 4: Create the Site-to-Site VPN Connection in AWS Side.
```xml
Name: techworldwithmurali-site-to-site
```
##### Static IP prefixes:
```xml
AWS CIDR - 10.70.0.0/16
On-Premises - 192.168.0.0/16
```
```xml
Local IPv4 network CIDR - 192.168.0.0/16 (On-Premises)
Remote IPv4 network CIDR - 10.70.0.0/16 (AWS CIDR)
```
#### Step 5: Add the route table preparation for the Virtual Private Gateway in AWs Side.

#### Step 6: Download the Configuration of the Site-to-Site VPN Connection and configure it in OpenSwan Server.
#### Step 7: Add the OpenSwan instance id  route to the Public RouteTable.
```xml
Route Entry

Destination : 10.70.0.0/16
Target : OpenSwan instance ID
```
#### Step 8: Launch AWS EC2 instances in both VPCs(AWS VPC and the On-Premises VPC.).

#### Step 9: Test the connection between the AWS VPC and the On-Premises VPC.

##### Congratulations! You have successfully set up the AWS Site-to-Site VPN Connection.
