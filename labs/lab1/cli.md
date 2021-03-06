## Lab 1: Using the CLI to launch a website

### Step 1: Locate the Terminal
- On the Cloud9 environment locate your **bash terminal**
- Make sure you are in the **do-bc** directory by entering the command
```
cd ~/environment/do-bc
```

### Step 2: Retrieve *KeyPairName* and *VpcId*
- **KeyPairName** is the Key Pair you created in the **Configuration** section. If you do not remember it use the following terminal command to obtain
```
aws ec2 describe-key-pairs
```
- **VpcId** can be obtained with the following terminal command
```
aws ec2 describe-vpcs --query 'Vpcs[?IsDefault==`true`].VpcId' --output text
```

### Step 3: Update and run command
- Copy the following command to your terminal (Yep, it's a long one)
- Update the **\<placeholders\>** with the values you retrieved in **Step 3**. Make sure ther "<" and ">" are removed too.
- Hit **Enter** to run
```
aws cloudformation create-stack --stack-name Infrastructure --template-body file://./lab1.yaml --parameters ParameterKey=KeyPairName,ParameterValue=<KeyPairName> ParameterKey=VpcId,ParameterValue=<VpcId>
```
- Did you get an error? Something like *"An error occured (InsufficientCapabilitiesException)..."* It's important to note that, like on the dashboard, we need to acknowledge that we are going to be updating permissions. This requires the **--capabilities** flag. Try the following.
- In the terminal, hit the **Up Arrow**, this will take you back to the last command you did. Add the following at the end. Make sure there is a space.
```
--capabilities CAPABILITY_NAMED_IAM
```

### Step 4: Check for Completion
Run the following command in your terminal to check the status of your stack.
```
aws cloudformation describe-stacks --stack-name Infrastructure
```
You will eventually see a *StackStatus* of *CREATE_COMPLETE*.

In the **Outputs** area you will also see the **Url**. Copy and paste that to your browser.

**Do you see your website?**

[Lab1](README.md) | [Home](../../README.md)