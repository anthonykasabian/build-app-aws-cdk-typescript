# Intro and Welcome

**[📹 Video](https://codecentric.de/lessons/build-app-aws-cdk)**

**[💻 Code](https://github.com/the-friendly-coach/egghead-aws-cdk-workshop)**

Hi and welcome! This document contains some of the things that I had to lookup while I was going through this course. I hope you find them useful too!

## What is a lambda function?

* `lambda` means function as a service, where you, the developer, don't have to worry about managing servers, just the functions that need to be executed.

* The function can be triggered by multiple sources like **API Gateway** (`http` requests), as well as changes to the **Dynamo DB** database or `s3` storage bucket.

* `lambda` functions can be written in a variety of different languages.
TODO: coming soon
If you prefer a video tutorial, follow this [one](https://codecentric.de/lessons/aws-whatsup-aws-lambda).

## Create an admin user with IAM and configure AWS CLI to enable programmatic access to AWS

Go to [AWS Management Account](https://aws.amazon.com/console/) and either create a new account or log in.

* In the **Find Services** section look for **IAM**

* Once you are in **Identity and Access Management** select **Users** from the sidebar.

* Click on **Add user** and create a new **admin-user** and select both **Programmatic access** AND **AWS Management Console access**

* Under **Permissions** create a new **admin** group and create an **admin-user** for this group.

* Create a group called **AdminUsers** and check **AdministratorAccess** under Policy Name then click **Create Group**.

* You can skip the **tag** section and click on **Create user**.

* Make sure to save your **access key** and **password** (Secret Access Key) as this is the only time that they will be displayed (👍 you can download them as a `.csv` file)

Here for the [📹 video tutorial](https://codecentric.de/lessons/configure-aws-cdk-iam).

## Avoid aws charges by setting up a billing alarm

* Log into your `aws` console as a `root` user then search for **Billing**.

* Scroll down and check your usage in **Top Free Tier Services by Usage**

* Under **Services** search for **CloudWatch**, click on **Billing** and then **Create alarm**.

* Leave the default configuration then add a threshold value, for example: $5 (meaning you'll get a notification whenever you spend more than $5).

* On the next page, choose: **Create new topic**, for example: `PayingTooMuchAWSAlarm` and add your email address.

* You'll have to confirm the subscription link sent to your email before the alarm is activated.

* Next, add an alarm name, for example `PayingTooMuchToTheCloud`

[📹 Video](https://codecentric.de/lessons/aws-review-billing-dashboard-setup) tutorial.

## Installing AWS CLI

There are several ways of installing the `aws CLI`. I'm on a macOS computer and installed it using the graphical interface.

🤔 [Source](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

Verify that `aws` CLI has been installed:

* `aws --version`

Now let's start configuring it (have your `.cvs` file with your access keys ready), run:

* `aws configure`

* For the region I chose: `eu-central-1` (Frankfurt) since I'm based in Europe.

👍 You can check the list of available regions back in your IAM Management Console, by clicking **Global** in your top right corner.

* For the output format, I left it at default.

To verify that your settings have been configured successfully run:

* `aws s3 ls`

Even if you have no visible output (because you currently don't have any active `s3` buckets), no errors means happy aws!

To see your credentials run:

* `cat ~/.aws/credentials`
