---
title: "Create  An Basic HTML WEB Page On Apache2 Server in EC-2  Instance Using Ubuntu OS"
seoTitle: "Create your own HTML Web Server In Just 10 Steps."
seoDescription: "Create  An Basic HTML WEB Page On Apache2 Server in EC-2  Instance Using Ubuntu OS|CENTOS|LINUX"
datePublished: Sun Nov 13 2022 16:07:35 GMT+0000 (Coordinated Universal Time)
cuid: clafjvq70000108mhg7nr9q16
slug: create-an-basic-html-web-page-on-apache2-server-in-ec-2-instance-using-ubuntu-os
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1668354844555/QMXMtaIBm.png
tags: aws, html, cloud-computing, apache, linux-for-beginners

---

First of All you have to Login to AWS Console with root or admin policy user. And from Console Search EC2 Service.
![Screenshot_20221113_202848.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668353201837/ajv0VSFtb.png align="left")
1.	To create an EC-2 instance Click on Launch instance tab . Then type Name of your Server (ex-HTML_WebPage).
2.	Select Amezon Machine Image (AMI) to Ubuntu or Anything You Want. In this program I will select ubuntu. Select Instance Type You Want And give Key Pair. If you don’t have key pair simply Create new one save on your computer. 
![Screenshot_20221113_203002.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668353250735/oBgnQ-rG_.png align="left")
3.	Create Security Group & Allow HTTPS & HTTP Traffic From the internet with Default one . And If you want to increase storage configure it . 
![Screenshot_20221113_203151.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668353268728/DEylYz9GG.png align="left")
4.	 And jump hit on Launch Instance. 
![Screenshot_20221113_203102.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668355236341/dzfy65vBR.png align="left")
Then Go to instance And Select the Instance which we created now and Connect via EC2 Instance Connect  click on Connect. Now You have Successfully Connected EC2 instance with Basic Configuration.
![Screenshot_20221113_203323.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668355352027/OorcpO-U_.png align="left")
5.	Then You have New Tab open as a Terminal[CLI]  In Browser login with username by default. So you have to Switch To Root for that type ```
sudo -s
``` and hit Enter. Now You are root so you have to Update ang upgrade your instance by using 
       ```
apt-get update && apt-get upgrade
```
 command. And update it.
6.	When your machine is upgraded you have to install a apache2 server. Apache is a popular open-source, cross-platform web server that is, by the numbers, the most popular web server in existence. For Installing apache2 just type       
         ```
apt-get install apache2
```
 and hit enter and then it prompt you to install yes or no. Just you have to type ```
Y
``` and enter.
7. Now your apache2 is install but not started. We have to start apache2 by typing the command ```
service apache2 start
```
8.	Now we have Default server so you have edit the HTTP servers index file. The file is stored in /var/www/html/ so you have go to that directory by using ```
cd
```command. And then check the index file is there or not by using ```
ls -a
``` command. 
9.	For welcome landing page we edit the index.html file by nano command i.e ```
nano index.html
``` and then edit your welcome landing page ```
(ex - Hello, Welcome to My New Web Server! 😊) .
``` And save it. 
![Screenshot_20221113_205331.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668353792217/TPTx0h3Rc.png align="left")

10.	Hey Congratulations We Have Created a Welcome Web Server using apache2. For checking your landing page type **public-ip** of instance (server) you created and paste on google and see the magic we created.     
![Screenshot_20221113_205351.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668353736863/tQD5p0JyU.png align="left")

```
Note- You can Replace this index file with your code file and upload on server.

```
