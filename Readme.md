<h1 align="center">
Whizlabs Challenge League
</h1>

<h2 align="center">
Challenge Lab Four
</h2>

<h2 align="center">
NAT Gateway
</h2>

---

WhizLabs is running a cloud challenge between May and July 2022.  The challenge is to complete various tasks in either AWS, GCP, or Azure to test cloud skills.  Following is my solution to challenge lab four.

---
<h3>From Whizlabs</h3>

[Cloud Challenge Details](inst.jpg)

>In this lab challenge, your Amazon VPC and Amazon EC2 skills are put to the test. You'll be given a requirement and you have to reach it using your knowledge of Amazon VPC and other AWS services. The Lab Challenge helps you understand the real-time scenarios.
    A company ABC launches two EC2 Instances, one to deploy a web application in Public subnet and the other to host another application in Private subnet. As a part of the infrastructure, they need internet access to Private Instance but secured. Now your are an Security Engineer and your challenge is to build the entire Infracture from scratch so, that the dev team can host their application in both EC2 Instances.<br><br>
>Follow the below instructions to complete this challenge. 
>1.	Create an Amazon VPC named MyVPC with IPv4 CIDR: 10.0.0.0/16 and No IPv6 CIDR.
>2.	Create Public and Private Subnets in MyVPC with IPv4 CIDR 10.0.0.0/24 and 10.0.1.0/24 Respectively.
>3.	Enable auto-assign public IPv4 address to Public subnet.
>4.	Create an Internet gateway named MyIGW and attach it to MyVPC 
>5.	Create a Public Route table in MyVPC and add Internet Gateway public route in it. 
>6.	Associate the Public Subnet to the Public route Table.
>7.	Launch an MyPublicEC2Server Instance in Public Subnet with the following configuration:
>     1.	Select Amazon Linux 2 AMI 
>     1.	Select t2.micro instance type
>     2.	Create 8GB gp2 EBS Volume.
>     3.	Select MyVPC and MYPublicSubnet and Enable Auto-assign Public IP
>     4.	Create a new security group MyEC2Server_SG and add SSH port with source Anywhere.
>     5.	Create a new Key Pair for the Public EC2 Instance.
>8.	Launch an MyPrivateEC2Server Instance in Private Subnet with the following configuration:
>     1.	Select Amazon Linux 2 AMI 
>     1.	Select t2.micro instance type
>     2.	Create 8GB gp2 EBS Volume.
>     3.	Select MyVPC and MYPrivateSubnet and Disable Auto-assign Public IP
>     4.	Select the Security Group created for first instance.
>     5.	Create a new Key Pair for the Private EC2 Instance.
>9.	SSH into Public EC2 Instance and test Internet Connectivity.
>10.	To Perform SSH operation
>           1.	Windows Users use Putty Software.   
>         2.	Linux/Mac Users use Terminal.
>11.	First SSH into Public EC2 Instance.
>12.	Next SSH into Private EC2 Instance from Public EC2 Instance  and run the following Linux commands in Private EC2 Instance. (Since no internet access is provided for Private EC2 instances, you will not be able to run the bellow)
>           1.	yum -y update
>           1.	yum install httpd -y
>13.	Create a MyNATGateway  in Public Subnet of VPC MyVPC to provide Internet access to the private instance. 
>14.	Update the Main Route table (which is different from one created by you) and Add NAT Gateway public Route.
>15.	Now again SSH into Public EC2 Instance and then SSH into Private EC2 instance from Public EC2 instance.
>16.	MyNATGatewayRun the below Linux commands in the Private EC2 Instance.
>           1.	yum -y update
>           1.	yum install httpd -y
>17.	If You are able to install httpd in Private Instance, You have completed this Challenge.

---



Login into AWS and search/choose *VPC*.

Click *Launch VPC Wizard*.

<p align="center">
  <img width="1000" src="launch vpc wizard.jpg">
</p>

Select *VPC only*. Name the VPC ```MyVPC```.  Check *IPv4 CIDR manual input*.

Enter ```10.0.0.0/16``` for **IPv4 CIDR**.  Check *No IPv6 CIDR block*.

Click *Create VPC*.

<p align="center">
  <img src="create vpc.jpg">
</p>

Select *Subnets* under **Virtual Private Cloud**.  Click *Create subnet*.

<p align="center">
  <img width="1000" src="create subnets.jpg">
</p>

Select *MyVPC* for **VPC ID**.  Click *Add a new subnet*.  Create and input names for both the public and private subnets.

For the public subnet, enter ```10.0.0.0/24``` for **IPv4 CIDR Block**.

For the private subnet, enter ```10.0.1.0/24``` for **IPv4 CIDR Block**.

Click *Create subnet*.

<p align="center">
  <img src="create subnets 2.jpg">
</p>

Back in **Subnets**, select the public subnet.  Under **Actions**, click *Edit subnet settings*.

<p align="center">
  <img width="1000" src="enable autoassign IPv4.jpg">
</p>

Check *Enable auto-assign public IPv4 address*.

<p align="center">
  <img src="enable autoassign IPv4 2.jpg">
</p>

Navigate to **Internet Gateways**, and click *Create internet gateway*.

<p align="center">
  <img width="1000" src="create igw.jpg">
</p>

Name the internet gateway and click *Create internet gateway*.

<p align="center">
  <img  src="create igw 2.jpg">
</p>

Click *Attach to a VPC*.

<p align="center">
  <img width="1000" src="attach igw to vpc.jpg">
</p>

Select *MyVPC* and click *Attach internet gateway*.

<p align="center">
  <img src="attach igw to vpc 2.jpg">
</p>

Switch to **Route Tables** and click *Create route table*.

<p align="center">
  <img width="1000" src="create route table.jpg">
</p>

Input a name for the route table and click *Create route table*.

<p align="center">
  <img src="create route table 2.jpg">
</p>

Click *Edit routes*.

<p align="center">
  <img width="1000" src="edit routes.jpg">
</p>

Click *Add route*. Select *0.0.0.0/0* and the internet gateway.  Click *Save changes*.

<p align="center">
  <img width="1000" src="edit routes 2.jpg">
</p>

Click to *Subnet associations*.

<p align="center">
  <img width="1000" src="subnet assoc.jpg">
</p>

Click *Edit subnet associations*.

<p align="center">
  <img width="1000" src="subnet assoc 2.jpg">
</p>

Check the public subnet and click *Save associations*.

<p align="center">
  <img width="1000" src="subnet assoc 3.jpg">
</p>

<p align="center">
  <img width="1000" src="launch ec2.jpg">
</p>

Lab is complete.

<p align="center">
  <img width="1000" src="validation.jpg">
</p>

<h1>Video Example</h1>

[![Video Example](vid.jpg)](https://youtu.be/mga-aM83SJA)
