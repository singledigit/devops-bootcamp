# Lab 1: Launching Your First Website - CLI
## Step 1: Open a Terminal
Open the terminal and change to the directory of the downloaded project.

    cd /path/to/project/root/lab1
## Step 2: Specify Details
Use the following info to fill in the form.
 - Stack Name: **Lab1Stack**
 - DBName: **LabOneDB**
 - DBPassword: **LabOnePassword**
 - DBRootPassword: **LabOneRootPassword**
 - DBUser: **admin**
 - KeyName: **[use key created earlier]**
## Step 3: Create Stack
From within the *Lab1* folder run the following command.
```
aws cloudformation create-stack --stack-name Lab1Stack --template-body file://./template.json --parameters file://./template-params.json
```
## Step 4: Check for Completion
Run the following command in your terminal to check the status of your stack.
```
aws cloudformation --describe-stacks
```
You will eventually see a *StackStatus* of *CREATE_COMPLETE*.

In the *Outputs* area you will also see the *WebsiteUrl*. Copy and paste that to your browser.

**Do you see your website?**

## Step 5: Cleanup
Run the following command in your terminal.
```
aws cloudformation delete-stack --stack-name Lab1Stack
```
Run the following to verify
```
aws cloudformation --describe-stacks
```

[Lab1](README.md) | [Home](https://github.com/singledigit/devops-bootcamp)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDkyMDE3NjU2LC0xMzA4MjQ5ODksMTM2OD
Y4NTczMiwyMDE0MDMwOTQwLDMyMTk4NDg0OCwtMTc5MDQ0OTAy
Miw3MzA5OTgxMTZdfQ==
-->