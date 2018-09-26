# Lab 1: Launching Your First Website - CLI
### Step 1: Open a Terminal
Open the terminal and change to the directory of the downloaded project.

    cd /path/to/project/root/lab1
### Step 2: Specify Details
Use the following info to fill in the form.
 - Stack Name: **Lab1Stack**
 - DBName: **LabOneDB**
 - DBPassword: **LabOnePassword**
 - DBRootPassword: **LabOneRootPassword**
 - DBUser: **admin**
 - KeyName: **[use key created earlier]**
### Step 3: Create Stack
From within the *Lab1* folder run the following command.
```
aws cloudformation create-stack --stack-name Lab1Stack --template-body file://./template.json --parameters file://./template-params.json
```
### Step 4: Check for Completion
Run the following command to check the status of your stack.
```
aws cloudformation --describe-stacks
```
You will eventually see a status of
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkyMDMyNjc3MSwzMjE5ODQ4NDgsLTE3OT
A0NDkwMjIsNzMwOTk4MTE2XX0=
-->