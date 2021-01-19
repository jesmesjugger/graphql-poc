
This is a simple graphql api building using express,graphql, AWS RDS(Postgresql)
#login to your AWS Account using the management console
#Click on services and search EC2
#select Amazon Linux 2 AMI 
#Click next to select the t2.micro Free tier eligible
$Click next and then proceed to add the following bashscript to install nodejs,postgres client and git
**************************************************

#!/bin/bash
yum -y update
yum install git -y
amazon-linux-extras install postgresql10 vim epel -y
yum install -y postgresql-server postgresql-devel
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
~./.nvm/nvm.sh
nvm install node
systemctl enable postgresql
systemctl start postgresql

***************************************************
#Proceed with the default storage
#Configure your webdmz security group to have the following inbound rules
******************************************
http port 80 source 0.0.0.0/0
https port 443 source 0.0.0.0/0
ssh port 22 source Ipof machine/32
custom tcp 4000 source 0.0.0.0/0

***********************************
#upon creating and downloading your ssh key proceed to launch

# go back to ec2 console and scroll down to Security group
#create a new security group for the RDS (postgresql)
*************************************
postgresql port 5432 source ipEC2instance/32 

***************************************
#headover to AWS RDS console 
Click on dashboard and click on create database
#installation select standard and engine type postgresql freetier
set your preferred password
use the default vpc for network if not configured new vpc
use default subnet group
security group select the one you created

