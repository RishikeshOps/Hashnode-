---
title: "Create an Application Load Balancer - Elastic Load Balancing  Using AWS EC2 Instance"
seoTitle: "Create an Application Load Balancer Between Two EC2 Instance"
seoDescription: "Create an Application Load Balancer - Elastic Load Balancing  Using AWS EC2 Instance"
datePublished: Wed Nov 16 2022 07:03:21 GMT+0000 (Coordinated Universal Time)
cuid: clajaresz000508jqbub84tx5
slug: create-an-application-load-balancer-elastic-load-balancing-using-aws-ec2-instance
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1668495435176/80V0mqQfb.png
tags: cloud, ec2, aws, load-balancing, ineuron

---

# **What is load balancing?**
Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses, in one or more Availability Zones. It monitors the health of its registered targets, and routes traffic only to the healthy targets.

- For More about Load Balancing must visit [link](https://aws.amazon.com/what-is/load-balancing/)


# **How to create a load balancer using AWS **
- ## Create EC2 And Host A Server
1) You Have To Create Two EC2 Instance For Balancing the load between them. Create An Instance And Host Apache Server. If You don't Know How to do that Read  [My Previous Blog](https://rushikesh-mashidkar.hashnode.dev/create-an-basic-html-web-page-on-apache2-server-in-ec-2-instance-using-ubuntu-os) on That .


![Screenshot_20221116_092616.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668571053066/K_CjPYqO4.png align="left")

2) Edit That servers Index file in two different Lines For Understanding.

![Blank 2 Grids Collage.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668570729531/LHZDnUpDg.png align="left")
So here we have to server called DC And Marvel now we do Load Balancing Between them.

- ## Create Load Balancing Application
1) Go down in left tab to **Load balancing** And Click on **Load Balancers** 
![Screenshot_20221115_125223.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668571281639/DYxJMZ1b-.png align="left")
After that Click on Create Load Balancer. In that click on **Application load Balancer** after clicking that you have page that you have to write your **load balancer name** select mapping zones in your region as you wanted to create.
![Screenshot_20221116_094443.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668572542985/JWGEQb4vA.png align="left")
![Screenshot_20221116_094509.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668572551605/yqeqYoZJk.png align="left")

2) Now You have to **create security Group **for load balancer. Bydefault AWS provides you a group But it Good practice to create new one so click on **Create New Security Group in Security Group Section.** It will take you to the new tab on browser. Fill your group name as you want & give Description. Set Inbound Rule to **HTTP** port 80 And keep rest all by default and click on create group.
![Screenshot_20221116_100305.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668574316469/oSJ8-YbsQ.png align="left")
![Screenshot_20221116_102100.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668574270475/Qqk5uy63t.png align="left")

3) Now go to the **security group** section in previous tab and refresh the list and you have to search the group that you created now.  
![Screenshot_20221116_102720.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668574662302/yzSh1rI_-.png align="left")

4) Now in **Listeners and routing** Section there  you find the select target group but we don't have the Target group So we click on **Create Target Group** and it will take you to a new browser. Now you have to Select **Target Type** as a Instance Because we use our ec2 instance for load balancing. If you want to set with ip select that. There is 4 Target types. Now enter the Target group name.
![Screenshot_20221116_103608.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668575334982/gDLc6C8mM.png align="left")
![Screenshot_20221116_103959.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668575410876/yrnF0Ppwk.png align="left")

5) Scroll Down to bottom and click on **Next**. Now you see There is your all running instance so you have to select instance for load balancing And click on **Include as pending below** 
![Screenshot_20221116_104156.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668575751726/92IRr7XQR.png align="left")
now you have a option to **review targets ** review and click on **create Target Group**.

![Screenshot_20221116_104542.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668575874486/jznl3aLjo.png align="left")

6) Back go to the browsers Load Balancer tab and refresh the target group section and there you will find your target group that you created now select that.
![Screenshot_20221116_105328.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668576213938/vGFIfuxX2.png align="left")

7) Scroll down and there you will see the summary about load balancer review it and click on **create load balancer.**
![Screenshot_20221116_105635.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668576604341/K-7b25odc.png align="left")
Now you Successfully Created Load balancer for EC2 instance. click on **view load balancer** and see the all things about your Load balancer.

8) Now Its Time to test your Load Balancer. Copy the DNS name from Load balancer Description and paste in new browser tab.
![Screenshot_20221116_110053.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668577081649/zFx1Xidq3.png align="left")
And refresh it again and again you will see your two difference sentence in your servers file. If you didn't see that please wait for 2 min load balancer take time to active.  ![Screenshot_20221116_110915.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668577236060/4tTgg3zPN.png align="left")
![Screenshot_20221116_110938.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668577246488/gqPNBdON0.png align="left")

If You Find Any Doubt Please visit the  [video](https://youtu.be/CSe39PPnF3k) . Here i provide a video with all these steps clearly.




-Thank You For Reading :) 

Rushikesh Mashidkar
