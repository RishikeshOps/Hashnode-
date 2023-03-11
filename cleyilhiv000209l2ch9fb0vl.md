---
title: "Create an AWS Code Pipeline with AWS Code Commit, Code Build & Code Deploy Tutorial"
seoTitle: "Learn how to create an AWS Code Pipeline with AWS DevOps"
seoDescription: "Designed and implemented an AWS Code Pipeline that automates the build, testing, and deployment of code changes for an application. Utilized AWS CodeCommit."
datePublished: Tue Mar 07 2023 17:18:04 GMT+0000 (Coordinated Universal Time)
cuid: cleyilhiv000209l2ch9fb0vl
slug: create-an-aws-code-pipeline-with-aws-code-commit-code-build-code-deploy-tutorial
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677866500460/f3aa1500-dfb3-4b02-b625-4305db4187a3.png
tags: aws, projects, devops, cicd, devops-articles

---

**Prerequisite:** First You have to install some Prerequisites for this deployment. [Click here to set up the prerequisite.](https://rushikesh-mashidkar.hashnode.dev/prerequisite-for-aws-devops-projects)

# Introduction

We have a sample HTML code that we want to use in a scenario where multiple developers work on the same code. As soon as a developer commits the code a new build should be created, tested, and deployed automatically.

First, we Manually deploy sample HTML code on the Nginx web server then we automate this manual deployment to continuous integration/continuous deployment (CI/CD) using AWS Code Pipeline For this sample code.

# What is AWS CodeCommit?

AWS CodeCommit is a version control service hosted by Amazon Web Services that you can use to privately store and manage assets (such as documents, source code, and binary files) in the cloud.

Below are the steps to create an AWS Code pipeline using all the native AWS tools:

## **Step 1: Create an AWS CodeCommit repository**

1. Go to the AWS CodeCommit console and click "**Create repository**".
    
2. Give your repository a name and description, and choose whether to make it public or private.
    
3. Click "**Create**" to create the repository.
    
4. Once the repository is created, click the "**Clone URL**" button to get the URL for cloning the repository to your local machine.
    
5. Clone the repository to your local machine using Git.
    
6. Create a sample index.html, buildspec.yml, appspec file & scripts to run during codedeploy.
    

### Write buildspec.yml file for code build & store artifacts in s3 Bucket.

```yaml
version: 0.2

phases:
  install:
    commands:
      - echo Installing NGINX
      - sudo apt-get update
      - sudo apt-get install nginx -y
  build:
    commands:
      - echo Build started on `date`
      - cp index.html /var/www/html/
  post_build:
    commands:
      - echo Configuring NGINX

artifacts:
  files:
    - '**/*'
```

This is a build specification file written in YAML format, which is used by the AWS CodeBuild service to automate the build, test, and deployment process for your application.

The `version: 0.2` at the top specifies the version of the buildspec file format being used.

The `phases` section contains three phases: `install`, `build`, and `post_build`. These phases are executed in order during the build process:

* The `install` phase installs the NGINX web server on the build server by running the specified commands. First, it echoes a message indicating that NGINX is being installed. Then, it updates the package list and installs NGINX using the `apt-get` package manager with the `-y` flag, which answers "yes" to any prompts.
    
* The `build` phase starts by echoing a message indicating that the build has started and prints the current date. It then copies the `index.html` file to the `/var/www/html/` directory on the build server, which is the default location for serving web content for NGINX.
    
* The `post_build` phase runs after the `build` phase is completed. It simply echoes a message indicating that NGINX is being configured.
    

The `artifacts` section specifies the files that should be included in the output artifact produced by the build process. In this case, the `files` section specifies that all files and directories in the build output should be included in the artifact. The `**/*` pattern matches any file or directory recursively in the build output directory.

### Add Script for installing & starting NGINX Webserver:

1. Create a folder named **scripts** & Write **install\_nginx.sh** to install **Nginx**
    
    ```bash
    #!/bin/bash
    
    sudo apt-get update
    sudo apt-get install -y nginx
    ```
    
    This is a simple Bash script that updates the package list of your Ubuntu-based system using the `apt-get` command and installs the Nginx web server using the same command.
    
    The first command, `sudo apt-get update` updates the package list on your system by downloading the package information from the Ubuntu repositories. This ensures that you have access to the latest software packages and security updates.
    
    The second command, `sudo apt-get install -y nginx`, installs the Nginx web server on your system. The `-y` option automatically confirms any prompts that may appear during the installation process.
    
2. write **start\_nginx.sh** un scripts folder to start the **Nginx** webserver
    
    ```bash
    #!/bin/bash
    
    sudo service nginx start
    ```
    
    The command `sudo service nginx start` starts the Nginx web server by running the `start` command on the `nginx` service. This command tells the system to launch the Nginx process and start serving web pages.
    

### Write appspec.yml file for codedeploy

```yaml
version: 0.0
os: linux
files:
  - source: /
    destination: /var/www/html
hooks:
  AfterInstall:
    - location: scripts/install_nginx.sh
      timeout: 300
      runas: root
  ApplicationStart:
    - location: scripts/start_nginx.sh
      timeout: 300
      runas: root
```

The file specifies the deployment steps and actions that CodeDeploy should take when deploying an application to a Linux instance.

The `version` and `os` keys specify the version of the deployment specification file and the operating system of the target instance, respectively.

The `files` section specifies the files that should be copied to the instance during the deployment process. In this case, it specifies that all files in the root directory of the application source should be copied to the `/var/www/html` directory on the target instance. This is a common location for serving web content on Linux instances.

The `hooks` section specifies the lifecycle events that should trigger scripts to run on the target instance during the deployment process. In this case, there are two hooks:

* The `AfterInstall` hook specifies that the `install_nginx.sh` script should be run on the target instance after the application files have been copied. This script installs the NGINX web server.
    
* The `ApplicationStart` hook specifies that the `start_nginx.sh` script should be run on the target instance after the NGINX server has been installed. This script starts the NGINX server.
    

Both of these scripts are executed with root privileges (`runas: root`) and have a timeout of 300 seconds (`timeout: 300`). This ensures that the scripts have enough time to complete before the deployment process times out.

**save all the files and push them to the code commits repository. Use git commands to add, commit, & push code to a repository.**

* ( Note: You have a Prompt Id & Password when you push to CodeCommit)
    

# What is AWS CodeBuild?

AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers. It provides prepackaged build environments for popular programming languages and builds tools such as Apache Maven, Gradle, and more. You can also customize build environments in CodeBuild to use your own build tools. CodeBuild scales automatically to meet peak build requests.

CodeBuild provides these benefits:

* **Fully managed** – CodeBuild eliminates the need to set up, patch, update, and manage your own build servers.
    
* **On-demand** – CodeBuild scales on demand to meet your build needs. You pay only for the number of build minutes you consume.
    
* **Out of the box** – CodeBuild provides preconfigured build environments for the most popular programming languages. All you need to do is point to your build script to start your first build.
    

## **Step 2: Create a CodeBuild project**

1. Go to the AWS CodeBuild console and click "**Create build project**".
    
2. Give your build project a name and description.
    
3. In the "**Source**" section, choose "**AWS CodeCommit**" as the source provider and select the repository you created in Step 1. And select the Branch of your repository.
    
4. In the "**Environment**" section, choose a build environment that meets your requirements, such as "**Ubuntu**". Choose runtime as "**Standard:6.0**"
    
5. In the "**Buildspec**" section, Choose "**Use a buildspec file**".
    
6. In the "**Artifacts**" section, choose "**Amazon S3**" as the type and specify the S3 bucket and key prefix where build artifacts should be stored.
    
7. Select the "**Artifacts packaging**" as a "**Zip**".
    
8. In the Logs Section, Untick the Checkbox of "CloudWatch logs"
    
9. Click "Create build project" to create the CodeBuild project.
    

Click on **Start Build**. Once all the Stages are finished, the Build File will be generated in the S3 Bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677875555928/ae226533-5be6-4b80-a8a2-3d949377535f.png align="center")

Check S3 Bucket for the Files

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677875701947/bd858f09-08b7-4c06-8ea7-c2a31b030855.png align="center")

# What is CodeDeploy?

CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.

You can deploy a nearly unlimited variety of application content, including:

* Code
    
* Serverless AWS Lambda functions
    
* Web and configuration files
    
* Executables
    
* Packages
    
* Scripts
    
* Multimedia files
    

CodeDeploy can deploy application content that runs on a server and is stored in Amazon S3 buckets, GitHub repositories, or Bitbucket repositories. CodeDeploy can also deploy a serverless Lambda function. You do not need to make changes to your existing code before you can use CodeDeploy.

# What is AWS CodePipeline?

AWS CodePipeline is a continuous delivery service you can use to model, visualize, and automate the steps required to release your software. You can quickly model and configure the different stages of a software release process. CodePipeline automates the steps required to release your software changes continuously.

## **Benefits:**

* Automation of Build, Test, and Release Processes.
    
* Pipeline History Reports and Pipeline Status Visualizations
    
* Establish a consistent release process.
    
* Speed up delivery while improving quality.
    
* Supports external tools integration for source, build, and deployment.
    

## **Step 3: Create a CodeDeploy application and deployment group**

1. Go to the AWS CodeDeploy console and click "**Create application**".
    
2. Give your application a **name**, Select "**Compute platform**" As "**EC2/On-premises**" and click "**Create application**".
    
3. Once the application is created, click "**Create deployment group**" to create a new deployment group for the application.
    
4. Give your deployment group a **name**, Select the **service role**, and **choose the Amazon EC2 instances** where we will deploy the application
    
5. In "**Environment configuration"** Select **"Amazon EC2 instances"** and then select "**key**" as a "**Name**" & "**Value**" as "**InstanceName**". (*Note:- Select the instance that you created in the prerequisites section and which has already installed CodeDeploy Agent)*
    
6. Select "**Never**" in "**Install AWS CodeDeploy Agent**" & "Unselect Enable load balancing"
    
7. Click "**Create deployment group**" to create the deployment group.
    

***Congratulations! Your application is now running on an EC2 IP address. But, wait, it's not over yet. We have automated this deployment through AWS CodePipeline.***

## **Step 4: Create a CodePipeline**

1. Go to the AWS CodePipeline console and click "**Create pipeline**".
    
2. Give your pipeline a name and click "**Next**".
    
3. In the "**Source**" section, choose "**AWS CodeCommit**" as the source provider and select the **repository** & **branch** you created in Step 1.
    
4. Select "**Change detection options**" as "**AWS CodePipeline**" and then "**Next**".
    
5. In the "**Build**" section, choose "**AWS CodeBuild**" as the build provider and select the **CodeBuild project** you created in **Step 2** and click "**Next**".
    
6. In the "**Deploy**" section, choose "**AWS CodeDeploy**" as the deployment provider and select the application and deployment that you created in **Step 3** and click "**Next**".
    
7. Review once & click "**Create pipeline**". It will take time to complete all the steps.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678132397476/9a03a88e-7999-4cbd-9661-67c6d30cc512.png align="center")
    

***Congratulations🎊 Your application is now running on an EC2 IP address We have automated this deployment through AWS Code Pipeline with AWS Code Commit, Code Build & Code Deploy.***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678132633357/4e384bfa-b3bc-439f-9034-84fee4fb00a7.png align="center")

You have the ability to modify your HTML page and upload it to codecommit. Once uploaded, the pipeline will initiate automatically and deploy the updated application. You have the option to set up an alarm for this specific pipeline and receive a notification when it is activated.

---

The source code for everything is hosted here: [https://github.com/RishikeshOps/AWS-DevOps-Project](https://github.com/RishikeshOps/AWS-DevOps-Project)

If you’re interested in reading about other CI/CDs I’ve built up, please visit my [Blog page](https://rushikesh-mashidkar.hashnode.dev/).

---

***Thanks for reading to the end; I hope you gained some knowledge. ❤️🙌***

*\-* ***Rushikesh Mashidkar***💕