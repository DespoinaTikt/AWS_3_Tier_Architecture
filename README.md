# AWS_3_Tier_Architecture
For this project I am going to create a 3 tier architecture on AWS, consisting of a user/presentation tier, an application tier and a database tier. 

![Tier3Topology](https://github.com/user-attachments/assets/492ea3d2-9e5d-493f-9a66-fe0b6541830f)

## Create VPC and Components
As a first step, I am going to create a custom VPC and give it a CIDR block. Then, I will create 4 subnets, 1 public and 3 private. I will put the first 2 private subnets in the same Availability Zone as the public subnet. 

![Screenshot (186)](https://github.com/user-attachments/assets/5f7fbac6-dc9c-4a73-9e12-eb60bc6705da)
![Screenshot (187)](https://github.com/user-attachments/assets/b175ad5b-6a80-4d2f-aac9-d543a046b2f7)
![Screenshot (188)](https://github.com/user-attachments/assets/c3a40eb2-7cbc-4d47-ae88-39a4bb85afb0)
![Screenshot (191)](https://github.com/user-attachments/assets/08fb87bd-a599-4835-bb90-6f92d689a816)

After that, I allocate an Elastic IP address.

![Screenshot (193)](https://github.com/user-attachments/assets/8ad65039-3e95-4d68-8593-aff6f48c1eb8)

Then I create an Internet Gateway and attach it to the VPC.

![Screenshot (195)](https://github.com/user-attachments/assets/cc21f6b4-3bca-47c8-a26d-e27d748ce6c1)

In addition, I create a NAT Gateway and assign it to the public subnet.

![Screenshot (197)](https://github.com/user-attachments/assets/aeaa4e00-7400-4b9f-86ba-131db2fd6181)

Finally, I create 2 route tables, one private and one public. I assign them to the respective gateways and subnets.

![Screenshot (200)](https://github.com/user-attachments/assets/b0ba50a2-d3b6-4025-a8ef-4bf4b8e36042)

![Screenshot (201)](https://github.com/user-attachments/assets/70a0c1e3-8752-49f9-81fa-2f68431ec64a)

![Screenshot (202)](https://github.com/user-attachments/assets/11ed05f3-8dc0-43c7-80ff-ec44e65815c6)

## Create security groups and instances

First I create the appropriate security groups for each of my servers, with inbound rules that allow intercommunication between the instances and public access for the bastion host and the web server.

![Screenshot (205)](https://github.com/user-attachments/assets/b7e88bca-eac9-4c95-b009-c9aaa2cc7826)

Then I create my EC2 instances. The first one is the bastion host, in the public subnet.

![Screenshot (206)](https://github.com/user-attachments/assets/d95a34ec-fc90-43c1-a5b1-b3f9842f1ba4)

Then I create the web server, in the public subnet also, and with the appropriate user data.

![Screenshot (207)](https://github.com/user-attachments/assets/642afeb7-34fd-4c7b-b443-258a99354bc9)
![Screenshot (208)](https://github.com/user-attachments/assets/0f297025-f384-403f-a412-3b86e72a32e9)

Then, I create the app server, hosted in the private subnet, with the appropriate user data.

![Screenshot (209)](https://github.com/user-attachments/assets/66c41052-47de-4c74-878a-976e85161172)
![Screenshot (210)](https://github.com/user-attachments/assets/3ef133d8-8355-4a83-9155-a952a42ad1cf)

My instances are ready.

![Screenshot (219)](https://github.com/user-attachments/assets/62624327-6675-4689-b53f-8cd79872db3b)

For the database server, I create an RDS subnet group and database with MariaDB.

![Screenshot (213)](https://github.com/user-attachments/assets/0ae5e9d3-d639-4c5b-8534-8294994bb44d)
![Screenshot (218)](https://github.com/user-attachments/assets/ea3b2b17-f285-4f63-bdc8-6a4132e5cace)

## Test the servers

I SSH into my bastion host with success and from there I ping the other instances to test their connectivity.

![Screenshot (220)](https://github.com/user-attachments/assets/6dcdc81f-dccb-45b5-85af-18ca89b0b52b)
![Screenshot (221)](https://github.com/user-attachments/assets/e7d06812-e1c1-4521-8b65-1ebd1255ddd7)






