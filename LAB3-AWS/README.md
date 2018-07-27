# AWS HANDS ON 

LAB3-AWS |
[LAB1-GIT](../LAB1-GIT/README.md) |
[LAB2-JENKINS](../LAB2-JENKINS/README.md) |
[Home](../README.md) 


This folder contains all the stuff you need to get started with AWS


# LESSON 1 Store and Retrieve a File

1. Enter amazon console 
2. Then type S3 in the search bar and select S3 to open the console.
3. In the S3 dashboard, click Create Bucket.
![s3](../images/bucket.png "s3")

4. Enter a bucket name. Bucket names must be unique across all existing bucket names in Amazon S3.
5. You have many useful options for your S3 bucket including Versioning, Server Access Logging, Tags, Object-level Logging and Default Encryption. We won't enable them for this tutorial. Select Next.
6. You have the ability to set permission settings for your S3 bucket. Leave the default values and select Next.
7. Review your configuration settings and select Create bucket.

## SUMMARY

I wont explain the obvious, but adding and retreiving files are straight forward and will leave you to find that out. 
__WHY__ is this so useful? Because not only can you hold files here, but you can also host your website in an S3 bucket and server critical components - there is truly a lot of functionality you can do with S3. 


# LESSON 3 Launch a Linux Virtual Machine

Amazon Elastic Compute Cloud (EC2) is the Amazon Web Service you use to create and run virtual machines in the cloud. These are referred to as instances in AWS and are useful because you can run multiple and loadbalance them, so effectivley you can host a companies entire infrastructure and apps on EC2. 
 Spinning up as demand peaks and contracting down when it's quite to save server costs. 

 1. Search for EC2 and open 
 2. click Launch Instance to create and configure your virtual machine.

 ![launch](../images/launch.png "launch")

3. In this screen, you are shown options to choose an Amazon Machine Image (AMI). AMIs are preconfigured server templates you can use to launch an instance. Each AMI includes an operating system, and can also include applications and application servers. but we will find Amazon Linux AMI and click Select.

![linux](../images/linux.png "linux")


4. The default option of t2.micro should already be checked and it is free. 
5. Stick with default values on this screen below. 

![default](../images/default.png "default")

6. On the next screen you will be asked to choose an existing key pair or create a new key pair. A key pair is used to securely access your Linux instance using SSH. AWS stores the public part of the key pair which is just like a house lock. You download and use the private part of the key pair which is just like a house key. Select __Create a new key pair__ and give it the name __MyKeyPair__. Next click the __Download Key Pair__ button.
