---
title: "Migrating from AWS EC2 to GCP VM Sharing A DevOps Engineer's Journey"
seoTitle: "Migrating from AWS EC2 to GCP VM"
seoDescription: "Discover a Seamless Migration Process: Migrating from AWS EC2 to GCP VM 🚀 | In-Depth Guide"
datePublished: Sun Jul 23 2023 18:46:22 GMT+0000 (Coordinated Universal Time)
cuid: clkfsilzd000f0amm10256v8z
slug: migrating-from-aws-ec2-to-gcp-vm-sharing-a-devops-engineers-journey
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690128393347/f1b0846a-c128-44dc-a804-0459a0c1fd7d.png
tags: aws, migration, devops, gcp, cloud-migration-services

---

In the ever-evolving world of cloud computing, migration projects have become an integral part of many organizations' digital transformation strategies. As a DevOps engineer involved in a migration project from AWS to GCP, I had the opportunity to play a crucial role in the project's success. specifically focusing on migrating RDS instances while minimizing downtime and ensuring data integrity, and migrating AWS EC2 instances to GCP VMs. This blog post will provide insights into the challenges faced, the strategies employed, and the lessons learned during the migration process. It was not an easy task, and it required me to deeply understand the database infrastructure as well as the complexities of migration.

The migration process was carefully planned, and we used various tools and technologies. Working closely with the application teams, I ensured that they were aware of any changes to the database structure and that their applications were compatible with the new environment.

Despite encountering various challenges, such as incompatible data types, data corruption, and performance issues, my knowledge of database migration and DevOps practices allowed me to overcome these challenges and ensure a successful migration. Collaborating with the development teams and understanding the complexities of the database infrastructure allowed the project to be completed smoothly and efficiently.

The role of a DevOps engineer in a migration project cannot be overstated. Our knowledge and experience in database migration, cloud infrastructure, and DevOps practices are essential to the project's success. We play a vital role in ensuring the smooth functioning of the infrastructure and applications in the cloud environment.

# Step-by-Step Guide: Migrating AWS EC2 to GCP VM

Now, I will guide you through the process of migrating AWS EC2 instances to GCP VMs. By following these steps, you'll be able to successfully transition your infrastructure, ensuring minimal downtime and maintaining data integrity throughout the migration.

**Migrate to Virtual Machines** is a cloud migration service provided by Google Cloud Platform that helps you migrate your virtual machines from another cloud provider, such as AWS to GCP. This service automates the migration process and reduces the risk of data loss or downtime.

To migrate an AWS EC2 instance to GCP, you'll need the following pre-requisites :

* IAM user credentials of AWS Account i.e Secret Key & Secret Access Key (with valid permissions)
    
* Familiarity with AWS EC2 and GCP VMs
    

# Step 1: Determine your AWS environment

The first step is to take a look at the AWS environment and identify the virtual machines that you want to migrate to GCP. You need to analyze the applications, databases, and data stored on the virtual machines and determine if they are suitable for migration.

In this tutorial, we will walk through a practical example of migrating an AWS EC2 instance named "**portfolio**" to the Google Cloud Platform (GCP). By following this step-by-step guide, you will gain hands-on experience migrating an EC2 instance, which includes data and a running application within a Docker container to GCP.

# Step 2: Prepare the GCP environment

Before starting the migration, you need to prepare the GCP environment. This involves creating a new project and configuring the necessary services, such as the compute engine, storage, and networking. This is for new accounts. You can skip this step if you're utilizing GCP and its computing service.

Log in to the Google Cloud Platform (GCP) Console:

* Access the GCP Console using your Google account credentials.
    
* Navigate to the Compute Engine section.
    
* Search for "**Compute Engine API**" and click on it.
    
* Enable the **Compute Engine API** for your project and also enable "  
    **VM Migration API**" for VM Migration.
    

# Step 3: Let's configure the Migrate for Compute Engine

1. In the GCP Console, go to the "**Migrate to Virtual Machines**" page. You can access this page by navigating to the Compute Engine section and selecting "**Migrate to Virtual Machines**" from the sidebar.
    
2. Go to [SOURCES](https://console.cloud.google.com/compute/mfce/sources?project=boxwood-coil-365716) –&gt; **Add Source** –&gt; **Add AWS Source** –&gt; Add Name, select and enter all the credentials as shown below, and click Create.
    
    * **GCP Region**: **asia-south1 (Select the region where you want to migrate instance)**
        
    * **AWS Region**: us-east-1 (Select the region where your AWS Instance is Running)
        
    * **Access Key**: \*\*\*\*\*\*\*\*\*\*\*\*\* (Add Credentials of AWS IAM user)
        
    * **Secret Access Key**: \*\*\*\*\*\*\*\*\*\*\*\*\*
        
        After you add a source, it will display a list of all instances in your AWS account.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690034527893/b2d274bb-1c44-45c5-8642-dc07189710b3.png align="center")
    
3. Select the VM that you wish to migrate and then click "**ADD MIGRATIONS**" and "**OK**."
    
4. Go to the **MIGRATIONS** tab, select the VM you just added, and then click on the **Edit Target Details** button.
    
5. **Configure the target environment in GCP:**
    
    a. Enter a name for the migrated instance.
    
    b. Select the GCP project where you want to create the migrated instance.
    
    c. Choose the target region in GCP where you want the instance to be located.
    
6. **Customize the migration settings:**
    
    a. Review the suggested machine type and adjust it if needed.
    
    b. Specify the boot disk size and disk type for the migrated instance.
    
    c. Choose the network settings, such as subnetwork, IP address, and firewall rules.
    
    Configure all parameters according to you and then save it.
    
7. **Start the migration:**
    
    a. Click on the "Start Replication" button to begin the migration process.
    
    b. Monitor the progress of the migration from the console.
    
    c. The replication procedure may take some time depending on the size of the instance and the amount of data. So get a cup of coffee and relax.😉😉
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690046553733/6606590e-da8d-447c-8349-5c08d9dc6c03.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690047858985/9ad90122-96aa-4ed7-a296-eeaec89c1bed.png align="center")

> Note:- Check Target details after replication status is Active

# Step 4: Test the migration

1. Once the replication is complete, you need to clone the replication in the GCP environment. So select the migration job and click on the "**Test-Clone**" Button in the "**CUT-OVER AND TEST-CLONE**" tab and confirm.
    
2. It will launch a copy of the AWS VM in GCP, complete with all files and applications running on it.
    
3. Once the migration is complete, validate the migrated instance in GCP.
    
4. Ensure that the migrated instance is functioning as expected.
    

Before completing the migration, you need to test the GCP environment to ensure that it is functioning correctly. This involves testing the applications, databases, and data stored on the migrated instance.

You also need to test the performance of the GCP environment to ensure that it meets your requirements. This includes testing the network speed, latency, and bandwidth.

> Note:- You can directly use Cut-Over Process instead of **Test-Clone.**

# Step 5: Complete the migration

Once you have tested the GCP environment and are satisfied with its performance, you can complete the migration. This involves shutting down the virtual machine on AWS and starting the migrated virtual machine on GCP.

**Cut-Over migration:** Cut-Over operation will shut down your source VM. And Launch VM in GCP.

1. Firstly Go to VM Instances & Delete the test clone VM on GCP.
    
2. Now back to the Migrate to Virtual Machines and select migration job click on "**CUT-OVER AND TEST-CLONE**" and then "**Cut-Over**" and confirm it.
    

It will terminate your AWS instance and start a new virtual machine on GCP.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690054383069/245ecb92-ce50-4ecf-b616-31645b715bae.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690055639917/0eb1c260-2e22-4e8e-ba41-3770db349e16.png align="center")

> Congratulations🎊 You have moved an AWS EC2 instance to GCP ***:)***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690055918523/bcba20b7-34e5-4d70-b6fd-da4813ff809e.png align="center")

# Conclusion:

Migrating your virtual machines from AWS to GCP using Migrate to Virtual Machines is a streamlined and efficient process that can help you achieve your cloud goals. By assessing your AWS environment, preparing the GCP environment, configuring the Migrate for Compute Engine, testing the migration, and completing the migration, you can ensure a seamless transition to GCP.

In conclusion, the migration project was a significant success, and I am proud to have played a crucial role in it. The experience has taught me valuable lessons, and I am now better equipped to handle similar projects in the future. The success of the project was due to careful planning, preparation, and execution, as well as the collaboration between the various teams involved. I look forward to contributing to many more successful migration projects in the future.

---

If you'd like to learn more about the DevOps & Cloud projects I've built, please visit my [**Blog page**](https://blog.rushikesh.me) and [GitHub](https://github.com/RishikeshOps).

---

**Thanks for reading to the end; I hope you gained some knowledge. ❤️🙌**

**\- Rushikesh Mashidkar💕**