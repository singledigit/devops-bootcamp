# Lab 1: Launching Your First Website - Dashboard

### Step 1: Open CloudFormation
From the AWS Dashboard home page choose CloudFormation. You Can use the filter to help you locate the service.
### Step 2:  Ensure the Correct Region
In the top right corner, ensure that you are set to *Ireland*. If not, click the drop down and choose *Ireland*.
### Step 3: Click *Create Stack* Button
In the top left corner choose *Create Stack*.
### Step 4: Select Template
On the next screen, on the Choose Template dropdown, choose LAMP Stack. Click *Next*.
### Step 5: Specify Details
Use the following info to fill in the form.
 - Stack Name: **Lab1Stack**
 - DBName: **LabOneDB**
 - DBPassword: **LabOnePassword**
 - DBRootPassword: **LabOneRootPassword**
 - DBUser: **admin**
 - KeyName: **[use key created earlier]**

Leaving the rest of the fields to their default value, click *Next*.
### Step 6: Options
Leave all defaults and click *Next*.
### Step 7: Review
Verify all your data and click *Create*.
### Step 8: Waaaaiiiiiiiitttttt
Patiently wait for you stack to be created.
### Step 9: Retrieve Website URL
- Click checkbox next to the stack name, *Lab1Stack*.
- Click the *Outputs* tab.
- Copy or click on the *WebsiteUrl* value.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTczODE2OTYzOSwxNzc3MjEzNjM4XX0=
-->