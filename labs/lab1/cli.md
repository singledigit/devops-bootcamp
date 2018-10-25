## Lab 1: Using the CLI to launch a website

### Step 1: Open a Terminal
- On the Cloud9 environment locate your **bash terminal**
- Make sure you are in the *do-bc* directory by entering the command

```cd ~/environment/do-bc```

### Step 2: Retrieve *KeyPairName* and *VpcId*
- **KeyPairName** is the Key Pair you created in the *Configuration* section. If you do not remember it use the following terminal command to obtain

```aws ec2 describe-key-pairs```

- **VpcId** can be obtained with the following terminal command

```aws ec2 describe-vpcs --query 'Vpcs[?IsDefault==`true`].VpcId' --output text```

## Step 3: Update and run command
- Copy the following command to your terminal
- Update the <placeholders> with the values you retrieved in _Step 3_
- Hit **Enter** to run

```
aws cloudformation create-stack --stack-name Infrastructure --template-body file://./lab1.yaml \
    ParameterKey=KeyPairName,ParameterValue=<KeyPairName> \
    ParameterKey=VpcId,ParameterValue=<VpcId>
```
### Step 4: Check for Completion
Run the following command in your terminal to check the status of your stack.
```
aws cloudformation --describe-stacks
```
You will eventually see a *StackStatus* of *CREATE_COMPLETE*.

In the *Outputs* area you will also see the *WebsiteUrl*. Copy and paste that to your browser.

**Do you see your website?**

### Step 5: Cleanup
Run the following command in your terminal.
```
aws cloudformation delete-stack --stack-name Lab1Stack
```
Run the following to verify
```
aws cloudformation --describe-stacks
```

[Lab1](README.md) | [Home](../../README.md)