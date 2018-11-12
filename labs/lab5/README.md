## Lab Five: Delayed Deployments
Code deploy offers us the ability to launch delayed deployments through the use of 
traffic shifting. This means you can present new code to only a part of your traffic.
Here's an example of shifting 10% of your traffic for 5 minutes. After this, the rest of
the traffic will be routed to the new codebase.

## Step 1: Opening our new CodeStar Cloud9 Instance
- On the AWS Dashboard choose the **CodeStar** service
- Choose the **Dashboard** for the **BootCamp** project
- Scroll down a bit and on the right side you will see **AWS Cloud9 Environments**. Click the **See my environments** button.
- You will be taken to the Cloud9 service. On the **BootCamp** environment click **Open IDE**

## Step 2: Working in the new Cloud9 Environments
Now that the environment is set up, there are several things you should note.
- Note that you do not have to enable credentials, it has already been done for you
- Note that the **BootCampRepo** has already been copied locally to your environment

## Step 3: Updating git with your inforrmation
- Using the terminal: Set your username in GIT (be sure and update to your name)
```
git config --global user.name "Your Name"
```
- Using the terminal: Set your email in GIT using YOUR email (be sure and update to your email)
```
git config --global user.email your.email@example.com
```

## Step 4: Updating the Template
- In the **BootCampRepo** folder open the file named **template.yaml**
- Uncomment lines 14-19 (Remove the **#** and one space from each line)
- Save the file

## Step 5: Updating permissions
In the template file there is a [link to instructions](https://docs.aws.amazon.com/codestar/latest/userguide/how-to-modify-serverless-project.html?icmpid=docs_acs_rm_tr) on the proper permissions.

## Step 6: Commit the changes
- In the terminal make sure you are in the **BootCampRepo** directory
```
cd ~/environment/BootCampRepo
```
- Type the following to commit the changes.
```
git commit -am "Updating release to a canary release"
```
- The following command will push and start the update.
```
git push
```

Once you commit the changes your application will be redeployed but using a delayed deployment according to
the deployment options we uncommented in the template file.

## Step 7: See it in action
- Make a change to the **index.html** in the **public** folder under the **BootCampRepo** directory. (For instance: change the text **Example App** to **BootCamp App**)
- In the terminal make sure you are in the **BootCampRepo** directory
```
cd ~/environment/BootCampRepo
```
- Type the following to commit the changes.
```
git commit -am "First deployment"
```
- The following command will push and start the update.
```
git push
```

## Step 8: View the results
- On the **CodeStar** Dashboard choose **Deploy** from the menu on the left, this opens a new window.
- On your aplication page, choose the **Deployments** tab or from the left menu.
- Click on the **Deployment Id**

You should now see your deployment in action.

| [Home](../../README.md) |