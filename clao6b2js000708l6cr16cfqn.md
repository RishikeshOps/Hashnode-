---
title: "AWS Compute Services"
seoTitle: "What are the different types of AWS compute services? Features of  AWS"
datePublished: Sat Nov 19 2022 16:57:31 GMT+0000 (Coordinated Universal Time)
cuid: clao6b2js000708l6cr16cfqn
slug: aws-compute-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1668876752265/_jNXuqzXm.jpg
tags: cloud-computing, aws-lambda, elastic-beanstalk, aws-ec2, ineuron

---

# **Amazon EC2**
Amazon Elastic Compute Cloud (Amazon EC2) provides scalable computing capacity in the Amazon Web Services (AWS) Cloud. Using Amazon EC2 eliminates your need to invest in hardware up front, so you can develop and deploy applications faster. You can use Amazon EC2 to launch as many or as few virtual servers as you need, configure security and networking, and manage storage. Amazon EC2 enables you to scale up or down to handle changes in requirements or spikes in popularity, reducing your need to forecast traffic.

**Features of Amazon EC2**
- Virtual computing environments, known as instances

- Preconfigured templates for your instances, known as Amazon Machine Images (AMIs), that package the bits you need for your server (including the operating system and additional software)

- Various configurations of CPU, memory, storage, and networking capacity for your instances, known as instance types

- Secure login information for your instances using key pairs (AWS stores the public key, and you store the private key in a secure place)

- Storage volumes for temporary data that's deleted when you stop, hibernate, or terminate your instance, known as instance store volumes

- Persistent storage volumes for your data using Amazon Elastic Block Store (Amazon EBS), known as Amazon EBS volumes

- Multiple physical locations for your resources, such as instances and Amazon EBS volumes, known as Regions and Availability Zones

- A firewall that enables you to specify the protocols, ports, and source IP ranges that can reach your instances using security groups

- Static IPv4 addresses for dynamic cloud computing, known as Elastic IP addresses

- Metadata, known as tags, that you can create and assign to your Amazon EC2 resources

- Virtual networks you can create that are logically isolated from the rest of the AWS Cloud, and that you can optionally connect to your own network, known as virtual private clouds (VPCs)

# **Elastic Beanstalk**
AWS Elastic Beanstalk is an orchestration service offered by Amazon Web Services for deploying applications which orchestrates various AWS services, including EC2, S3,  CloudWatch, autoscaling, and Elastic Load Balancers. It is a simplest way to deploy & scale your web application.
-  It is an example of PAAS(Platform As A Service). And it is a region base service.
- It Supported Java, .Net , Node.Js, PHP, Ruby, Python, Tomcat, Go & Docker Applications and Software. 
- There is no additional charge for AWS Elastic Beanstalk. You pay for AWS resources (e.g. EC2 instances or S3 buckets) you create to store and run your application.

**Features **
- Automatic Load Balancing 
- Auto Scaling 
- Manage Platform Update 
- Manage Health Monitoring


# **Lambda**
Lambda is a compute service that lets you run code without provisioning or managing servers(Serverless). Lambda runs your code on a high-availability compute infrastructure and performs all of the administration of the compute resources, including server and operating system maintenance, capacity provisioning and automatic scaling, and logging. With Lambda, you can run code for virtually any type of application or backend service. All you need to do is supply your code in one of the languages that Lambda supports.

*Serverless is :- 
1) You don't worry about Infrastructure.
2) Flexible Scaling
3) Pay For Use
4) You Focus More on Code.*

- Lambda supported languages are Java, GO, Power shell, C#, Node.Js, Python, Ruby and many more.
- There is no additional charge for creating Lambda functions. There are charges for running a function and for data transfer between Lambda and other AWS services.

**Features**
- Concurrency and scaling controls
- Functions defined as container images
- Code signing
- Database access
- File systems access
- Lambda extensions
- Function blueprints

# **Lightsail **
Amazon Lightsail is the easiest way to get started with Amazon Web Services (AWS) for developers who need to build websites or web applications. It includes everything you need to launch your project quickly - instances (virtual private servers), container services, managed databases, content delivery network (CDN) distributions, load balancers, SSD-based block storage, static IP addresses, DNS management of registered domains, and resource snapshots (backups) - for a low, predictable monthly price.

**Use Cases :-**
- Launch simple web applications :
*Use pre-configured develop*ment stacks like LAMP, Nginx, MEAN, and Node.js. to get online quickly and easily.
- Create custom websites :
*Build and personalize your blog, ecommerce, or personal website in just a few clicks, with pre-configured applications like WordPress, Magento, Prestashop, and Joomla.*
- Build small business applications :
*Launch line-of-business software such as file storage and sharing, backups, financial and accounting software, and more.*
- Spin up test environments :
*Easily create and delete development sandboxes and test environments where you can try out new ideas, risk free.*