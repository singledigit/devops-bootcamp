# Lab 1: Launching Your First Website - Dashboard

## Step 1: Download template to local machine
In the environment pain under the `do-bc` folder, right click on the **lab1.yaml** file and choose **Download**.

## Step 2: Open CloudFormation
From the AWS Dashboard home page choose **CloudFormation**. You Can use the filter to help you locate the service.

## Step 3:  Ensure the Correct Region
In the top right corner, ensure that you are set to *Ireland*. If not, click the drop down and choose **Ireland**.

## Step 4: Click *Create Stack* Button
In the top left corner choose **Create Stack**.

## Step 5: Select Template
- Under **Choose a Template** choose the option to **Upload a template to Amazon S3**
- Click the **Choose File** button and browse to `/path/to/lab1.yaml`
- Click **Next**

## Step 6: Specify Details
- In the **Stack name** field enter *Infrastructure*
- In the **KeyPairName** field, choose the key you created in the configuration section.
- In the **VpcId** there should only be one choice. If you have more than one choice, its a good chance you created it so choose the default if you know it. Any of them will work.
- Click **Next**

## Step 7: Options
Leave all defaults and click *Next* (it might be out of view at the bottom of the page)

## Step 8: Review
Verify all your data and click *Create*.

## Step 8: Wait
- Patiently wait for you stack to be created. When the stack is through building give the instance about 2 more minutes before the website is up.

## Step 9: Retrieve Website URL
- Click checkbox next to the stack name, *Infrastructure* to select it.
- Click the *Outputs* tab.
- Copy or click on the *Url* value.

**Do you see your website?**


[Lab1](README.md) | [Home](../../README.md)