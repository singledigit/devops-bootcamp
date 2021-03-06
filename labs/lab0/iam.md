# Creating an IAM user
For security reasons, we want to create an IAM user.

1. From the home dashboard type **IAM** into the search box at the top.
2. Choose **IAM Services** from the dropdown.
3. Choose **Users** on the left menu.
4. Click the blue "Add User" button at the top.

### Step 1: User Details
1. Fill in a **User name** of your choice
2. Check the box for **AWS Management Console Access**.
3. Choose the **Custom Password** option for **Console Password**.
4. Fill in your **Password**.
5. Uncheck **Require Password Reset**.
6. Be sure and save your **Username** and **Password** somewhere where you can get it

### Step 2: Set permissions
1. Click the **Create Group** button.
2. Use **Admin** for the **Group Name**.
3. Click the checkbox next to **AdministratorAccess**.
4. Click the **Create Group** button in the bottom right corner. (You might already have groups if this is an account you are using. You are welcome tyo use another group just make sure it has the *AdministratorAccess* policy attached).
5. When you are returned to the **Set Permissions** window, the group **Admin** should already be checked in the **Add User to Group** section. If not, than please check it.
6. Click the **Next: Review** button on the bottom right.
7. On the the **Review** page, click **Create User** on the bottom right.
8. DO NOT CLICK **Close** ON THE NEXT PAGE.

### Step 3: Get Login Link
1. Choose **Dashboard** on the left menu
2. Find your **IAM users sign-in link:** and copy it to your computer

### Step 4: Change Users
1. From the user dropdown on the top right corner choose **Sign Out**
2. In the URL box of your browser, paste the **IAM users sign-in link** from **Step 4**
3. You should now see the AWS login page with the **Account ID or Alias** pre-populated
4. Enter you **IAM User Name** and **Password**
5. Click the **Sign In** button

[Next Step: Cloud9 Environment](cloud9.md) | [Configuration](README.md) | [Home](../../README.md)