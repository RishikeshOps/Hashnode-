---
title: "Getting Started With Aws"
seoTitle: "Everything About AWS IAM"
seoDescription: "All in one AWS IAM quick guide.

AWS IAM

IAM,MFA,Access key ID,

Devops

Cloud Computing"
datePublished: Sun Nov 06 2022 16:08:38 GMT+0000 (Coordinated Universal Time)
cuid: cla5ju46t000008jn9i6laj9x
slug: getting-started-with-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1667746031358/W1M5W67lB.webp
tags: aws, cloud-computing, devops, aws-iam, iammfaaccess-key-idsecret-access-key

---

# **WHAT IS AWS?**

Amazon Web Services (AWS) is the world’s most comprehensive and broadly adopted cloud platform, offering over 200 fully featured services from data centers globally. Millions of customers—including the fastest-growing startups, largest enterprises, and leading government agencies—are using AWS to lower costs, become more agile, and innovate faster.

# ** AWS — IAM Overview**
**What is AWS Identity and Access Management (IAM)?
**


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667746433258/js8Qf1ezp.png align="left")
##  **Introduction to AWS IAM:**
AWS Identity and Access Management (IAM) provides fine-grained access control across AWS accounts. With IAM, you can specify who can access which services and resources, and under which conditions. IAM is a pillar of security and provides you with easy ways to secure AWS accounts and resources.

# **IAM Key Points**
- IAM controls access to AWS services and resources.
- IAM enables access between AWS services (e.g. EC2 to RDS).
- The main feature of IAM is that it allows you to create separate usernames and passwords for individual users or resources and delegate access.
- IAM supports identity federation. If the user is already authenticated, such as through a Facebook or Google account, IAM can be made to trust that authentication method and then allow access based on it.
- IAM is a free service. There is no additional charge for IAM security. There is no additional charge for creating additional users, groups, or policies.
- IAM is PCI DSS compliance.
- IAM supports MFA.

It provides two essential functions that work together:

**Authentication:**

- Validates the identity of a user or a service.
- Create and manage IAM identities.
- Federate corporate identities.

**Authorization:**

- Defines the permissions and limits access to only specific resources for the permitted user.
- Assign permissions to IAM identities.
- Assign permissions to corporate identities.

# **IAM Key Terms**

IAM provides three primary types of identity: ```
users, groups, roles.
``` They serve different purposes, and each has an associated set of permissions using ```
policies.
```

# **IAM User**
- Users represent people (For example, members of the Development and DevOps team).
- Users are used to giving individuals the ability to manage AWS resources via AWS Console or programmatically (e.g. CLI).
- User is an identity with an associated credential and permissions attached to it. i.e. IAM User is an account for a single individual to access AWS resources.
- Users are granted permissions, either by attaching a permissions policy or by adding them to a group. Access appropriate resources through assigned permissions.
- User can be a Person or a Service.
- IAM User can belong to a max of 10 Groups.
- When an AWS account is first created, it has a single user. This is the root user, which has complete access to all resources.

# **IAM Account Root User Overview**
## **IAM User Group**
- Group is a collection of users and makes it easy to grant permissions to a class of users.
- You can logically group users in the AWS account and manage the privilege level for all users in that group.
- You set permissions for the group, and those permissions are automatically applied to all the users in the group.
- For example, Group for developers, Group for System administrators. Both of them will have different levels of access to AWS services.
- Group is not a true identity. You can leverage groups for easier administration.
- IAM users can be added to multiple groups.
- IAM policies can be attached to a group. Each group can have up to 10 policies attached.
- IAM users within an IAM Group inherit all policies attached to a group.
## **IAM Role**
- Roles have many of the same properties as users. However, roles are not linked to a single individual.
- You can create roles to give permission to use AWS service by another AWS service.
- Role enables a user or AWS service to assume permissions for a task. Roles are assumed by IAM Users (People or Applications) and external (federated) users.
- Roles do not have log-in credentials. Instead, roles are temporarily assumed by users who need a specific set of permissions to complete a task. It delegate access to a trusted entity.
- For example, you can create S3Admin role and assign it to your EC2 instance. This will enable that EC2 instance to manage S3 resources.
- You can leverage roles for easier administration.
- Policies can be attached to Roles.
- Roles rely on the AWS STS service.
## **IAM Policy**
- Policies are JSON document that defines permission and controls access AWS resources. Permissions specify who has access to the resources and what actions they can perform.
- Policies are an authorization mechanism. You can create IAM policies to define granular access to resources.
- For example, a policy could allow an IAM user to access one of the buckets in Amazon S3.
- Policy can be attached to IAM identities (Users, Roles, Groups).
- Single policy can include multiple permissions (or statements).
- Policies can be either customer managed or managed by AWS.
- There are multiple policies provided by AWS like Administrator, S3FullAccess, etc.
- You can also create your own policy and use it to manage privilege levels to your AWS resources.

Policy contains the following information:

- Who can access it.
- What actions that user can take.
- Which AWS resources that user can access.
- When they can be accessed.
### **Types of policies:**

**Managed policies:** It is a default policy that you attach to multiple entities (users, groups, and roles) in the AWS account. Managed policies, whether they are AWS-managed or customer-managed, are stand-alone identity-based policies attached to multiple users and/or groups.

**Inline policies**: It is a policy that you create that is embedded directly into a single entity (user, group, or role).

# **Summary**
IAM is one of the major building blocks of AWS. IAM lets you control who can use your resources (authentication) and in which ways (authorization). AWS IAM follows an incredibly granular approach in providing permissions and access control within your AWS environments.
**Want to more information about AWS-IAM [visit here](https://spacelift.io/blog/iam-policy)
**


*Thanks For Reading! :)
*

*-Rushikesh Mashidkar*



