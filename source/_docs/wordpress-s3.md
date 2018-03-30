---
title: AWS S3 Setup for WordPress
description: Add the ability to integrate with AWS S3 to a WordPress site on Pantheon
tags: [siteintegrations]
categories: [wordpress]
contributors:
  - sarahg
date: 3/27/2018
---

Amazon Web Services (AWS) offers Simple Storage Service (S3) for scalable storage and content distribution, which can be integrated with sites running on Pantheon.

## Before You Begin

Be sure that you have:

- An existing site or [create](https://dashboard.pantheon.io/sites/create){.external} one
- Set up an account with [Amazon Web Services (AWS)](https://aws.amazon.com/s3/){.external}. Amazon offers [free access](https://aws.amazon.com/free/){.external} to most of their services for the first year.

<div class="alert alert-info" role="alert">
<h4 class="info">Note</h4>
<p>When creating an AWS account, you will have to enter credit card information. This is required, but you will not be charged unless you exceed the usage limits of their free tier.</p></div>

## Configure S3 within the AWS Console
Before integrating S3 with your site, you'll need to configure the service within your [AWS Management Console](https://console.aws.amazon.com){.external}.

### Create a New AWS S3 Bucket
If you do not have an existing bucket for your site, create one:

1. From your [AWS Console](https://console.aws.amazon.com){.external}, click **S3**.
2. Click **Create Bucket**.
<ol start="3"><li>Enter a bucket name. The bucket name you choose must be unique across all existing bucket names in Amazon S3.

 <div class="alert alert-info" role="alert">
 <h4 class="info">Note</h4>
 <p>After you create a bucket, you cannot change its name. The bucket name is visible in the URL that points to the objects stored in the bucket. Ensure that the bucket name you choose is appropriate.</p>
 </div></li></ol>

4. Select a region and click **Create**.
5. Select **Permissions** within the bucket properties and click **Add more permissions**.
6. Choose a user and tick the boxes for **Read** and **Write** access for both **Objects** and **Permissions**, then click **Save**.

### Create an Identity and Access Management Policy
[Identity and Access Management (IAM)](https://aws.amazon.com/iam/){.external} allows you to manage all user access to AWS resources and services. Creating a policy allows you to explicitly set limited privileges on your specific bucket. This strategy offers long-term flexibility for organizing and managing users and their privileges.

1. From your [AWS Console](https://console.aws.amazon.com){.external}, click the **IAM** link.
2. Go to **Policies** and click **Create Policy**.
3. Select **Create your Own Policy**.
4. Give it a name and use the code example code provided in Amazon's [Policy Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_examples.html#iam-policy-example-s3){.external}.
5. Choose **Amazon S3** for the AWS Service and select **All Actions**. Provide the [Amazon Resource Name](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html#arn-syntax-s3){.external} for your bucket, and click **Next Step**.
6. Edit the policy name and description (optional).
7. Click **Create Policy**.

For details, see [Example Policies for Administering AWS Resources](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_examples.html#iam-policy-example-s3){.external}.

### Create an Identity and Access Management Group
We recommend that you do not access an S3 bucket using your AWS root user credentials. Instead, create an IAM group and user:

1. From your [AWS Console](https://console.aws.amazon.com){.external}, click **Identity & Access Management**.
2. Click **Groups**, then **Create New Group**.
3. Enter a descriptive group name and click **Next Step**.
4. Filter policies by **Customer Managed Policies** and select your recently created policy.
5. Click **Next Step**, then **Create Group**.
6. Go to **Users** and click **Create New Users**.
<ol start="7"><li>Provide a user name and click <strong>Create</strong>, then view the new user security credentials by clicking <strong>Show User Security Credentials</strong>.

<div class="alert alert-info" role="alert">
<h4 class="info">Note</h4>
<p>You can only view or download a user's secret access key immediately after the user has been created. This information cannot be accessed at a later point in time. You will need the access keys when configuring the S3 File System module</p></div></li></ol>

8. Click **Download Credentials**. Make sure you save the credentials in a secure location before leaving this page.
9. Go to the group created in step 5 and select **Add Users to Group**.
10. Select your newly created user and click **Add Users**.

## Integrate S3 with WordPress 
You will need to install a plugin such as [S3 Uploads](https://github.com/humanmade/S3-Uploads){.external} or [WP Offload S3](https://deliciousbrains.com/wp-offload-s3/){.external}.

WP Offload S3 requires a paid license but is configurable in the WordPress admin UI and offers a number of options and features. S3 Uploads is open-source but does not include an admin UI and requires [WP-CLI](/docs/wp-cli) for setup and migration.

### Install and Deploy WP Offload S3
@todo

### Install and Deploy S3 Uploads
@todo
https://deliciousbrains.com/wp-offload-s3/doc/quick-start-guide/
