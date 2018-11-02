## Lab Two: Building the Pipeline
Welcome to your second lab of the AWS DevOps Bootcamp!! In the previous lab you 
launched your first stack you launched a media rich website called "hello world".
But If you want to update the code for the website, wou would have to change the 
Cloudformation stack and run it all again... manually.

In this Lab we are going to start building the beginnings of a Continuous Integration/Continuous Deployment
process. Lets get started.

## Launching the Pipeline Stack

### Step 1: Retrieve *KeyPairName* and *VpcId*
- **KeyPairName** is the Key Pair you created in the *Configuration* section. If you do not remember it use the following terminal command to obtain
```
aws ec2 describe-key-pairs
```
- **VpcId** can be obtained with the following terminal command
```
aws ec2 describe-vpcs --query 'Vpcs[?IsDefault==`true`].VpcId' --output text
```

### Step 2: Update and run command
- Copy the following command to your terminal (Yep, it's a long one)
- Update the <placeholders> with the values you retrieved in *Step 1*. Make sure ther "<" and ">" are removed too.
- Hit **Enter** to run
```
aws cloudformation create-stack --stack-name Pipeline --template-body file://./lab2.yaml --parameters ParameterKey=KeyPairName,ParameterValue=<KeyPairName> ParameterKey=VpcId,ParameterValue=<VpcId> --capabilities CAPABILITY_NAMED_IAM
```

### Step 3: Check the results
- On the AWS Dashboard choose the CodePipeline service. This will take you to the CodePipeline console which gives you access to the Source, Build, Deploy, and Pipeline resources.
- Click on the **bootcampapp-Pipeline** in the Pipelines list.
- Take a look at the bootcampapp-Pipeline status. You will notice that your Source has failed... don't panic, we are going to fix that.

## Seeding the Repo 

### Step 1: Enabling GIT access to CodeCommit
When using Cloud9 with CodeCommit you are able to take advantage of your AWS credentials
providing extra layers of security. All of these will be executed in the Cloud9 
terminal.

- Set your username in GIT using YOUR name
```
git config --global user.name "Your Name"
```
- Set your email in GIT using YOUR email
```
git config --global user.email your.email@example.com
```
- Enable the AWS credentials helper
```
git config --global credential.helper '!aws codecommit credential-helper $@'
```
- Set HTTP option
```
git config --global credential.UseHttpPath true
```

### Step 2: Connecting to CodeCommit
- Make sure you are in the root directory
```
cd ~/environment
```
- Clone the repo
```
git clone https://git-codecommit.us-west-2.amazonaws.com/v1/repos/BootCampRepo
```
You will probably get an warning: "warning: You appear to have cloned an empty repository." 
You can ignore this.

You will also see a new folder in your file structure called **BootCampRepo**

### Step 3: Populate the local repository folder
In the terminal copy and paste the following command and hit **Enter**
```
cp -R ~/environment/do-bc/site/* ~/environment//BootCampRepo/.
```
You should see your site files copied to the *BootCamp* root directory.

### Step 4: Commit changes to local repository
1. Make sure you are in the *BootCampRepo* directory
```
cd ~/environment/BootCampRepo
```
2. Stage all files for committing
```
git add -A
```
3. Coomit the changes to the local Repository
```
git commit -am "Initial commit"
```
4. Push changes to remote repository
```
git push
```

### Step 4: Check the results
- On the AWS Dashboard choose the CodePipeline service. This will take you to the CodePipeline console which gives you access to the Source, Build, Deploy, and Pipeline resources.
- Click on the **bootcampapp-Pipeline** in the Pipelines list.
- Take a look at the bootcampapp-Pipeline status. The pipeline should now run properly through the build stage.