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

## Integrate S3 with WordPress 
You will need to install a plugin such as [S3 Uploads](https://github.com/humanmade/S3-Uploads){.external} or [WP Offload S3](https://deliciousbrains.com/wp-offload-s3/){.external}.

WP Offload S3 requires a paid license but is configurable in the WordPress admin UI and offers a number of options and features. S3 Uploads is open-source but does not include an admin UI and requires [Terminus](/docs/terminus) and [WP-CLI](/docs/wp-cli) for setup and migration.

### Install and Deploy WP Offload S3

@todo note: plugin conflicts with Solr-Power, like this: https://github.com/humanmade/S3-Uploads/issues/80

1. Download the latest plugin release from [Github]((https://github.com/humanmade/S3-Uploads/releases) and add it to your codebase. Note that our documentation has been tested for version 2.0.0.

Do not add the plugin as a Git submodule. Git submodules are not supported on the platform ([more info]((https://pantheon.io/docs/git-faq/#does-pantheon-support-git-submodules)).

2. Copy your S3 uploads key and secret from the "My security credentials" section of your AWS account.

3. Add credentials to wp-config.php. For security reasons, it is recommended to use a service like [Lockr](https://pantheon.io/docs/guides/lockr/) or the [Terminus Secrets plugin](https://github.com/pantheon-systems/terminus-secrets-plugin) to store and retrieve these credentials securely.

4. Deploy the new plugin and your wp-config.php to the Dev environment, then activate the plugin.

[terminus wp <site>.<env> plugin activate S3-Uploads]

5. Use WP-CLI to verify your AWS setup.

[terminus wp <site>.<env> s3-uploads verify]

6. Optional: Use WP-CLI to create a new AWS user. This is recommended so you are not using admin-level access keys on your site.

[terminus wp <site>.<env> -- s3-uploads create-iam-user --admin-key=<key> --admin-secret=<secret>]

Note: Currently this command will only work if you patch the plugin, per this issue on [Github](https://github.com/humanmade/S3-Uploads/issues/95#issuecomment-393989259).

Replace the keys you set previously in wp-config.php with the keys returned from the above command.

#### Migrate existing media using WP Offload S3
You can migrate existing media files to S3 with the following command:

[terminus wp sg-s3.dev -- s3-uploads migrate-attachments]

Optionally, add the `--delete-local` flag to remove the local copies of the media files.

Upon succesful migration, this command will also run a search/replace on your database to update references to the newly-migrated files. Note that you will need to run this on all Pantheon environments (dev/test/live).

#### Use WP-CLI to list and upload files
@todo test/adapt https://github.com/humanmade/S3-Uploads#listing-files-on-s3
@todo test/adapt https://github.com/humanmade/S3-Uploads#uploading-files-to-s3



#### Cache control
@todo test/adapt https://github.com/humanmade/S3-Uploads#cache-control

### Install and Deploy S3 Uploads
Follow documentation from [DeliciousBrains](https://deliciousbrains.com/wp-offload-s3/doc/quick-start-guide).
@todo test this one too

