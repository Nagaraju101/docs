---
title: "Working with Katalon TestOps OnPremise" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-analytics/docs/ktop-usage.html
description: 
---

## Create an Organization

One member of the team can complete these steps to invite all the others to an Organization for working on projects.

1. Open Katalon TestOps OnPremise server URL, for example, http://192.168.37.109:8080 and log into your account.

2. On the home page, click **Create Organization** at the bottom and confirm your action.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/create-org.png" width="" height="">

   You have just created an Organization in which you are the Owner.
3. In the **Organization** View, give a name to your Organization. Here is you can also view your Organization ID.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/org.png" width="" height=""> 

### Invite Organization Members

**Organization Owner/Admin**

1. In the **Organization** view, select **Users**.
2. In the **Users** view, select **Invitations**.
3. Invite your members one by one by entering their email addresses. The newly created invitation link is added to the **Pending Activations** table.
4. Copy and send the invitation link to that person.

   > An email with an invitation link attached is sent to the invited email if you have configured [Mail Server](https://docs.katalon.com/katalon-analytics/docs/ktop.html#configure-mail-server).

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/invitation-link.png" width="" height="">

Users are only added to the Organization once they sign in with the newly created account. You can track the invited persons' actions by observing their activation links. For example:

* The activation link of email *longbui@kms-technology.com* requires this user to update password for the account registered with the email.
* The activation link of email *quile@kms-technology.com* indicates the account associated with this email has not accepted the invitation yet.

**Invited person**

1. Click on the invitation link sent to you
2. You are navigated to a Katalon TestOps view where you need to create and confirm a new password for the account registered with your email.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/update-pw.png" width="" height="">

3. Click **Update password**, and you are done with registering your account with Katalon TestOps OnPremise Server.
4. Sign in with the newly created account to start working on Katalon TestOps.

> Troubleshoot
>
> If you click on the invitation link and encounter this error: "*This link has been used to reset password.*", it means a password is already updated.
>
> If you click on the invitation link and encounter this error: "*Cannot accept the invitation.*", please check and sign out the currently signed in account. Then use the invitation link to sign in with the corresponding account.

You can grant the new members organization roles. [Learn more](https://docs.katalon.com/katalon-analytics/docs/kt-user-role-permission.html).

## Create a Team

In the **Organization** view, select **Teams** > give a name to your team and click **Create**. You're the team Owner by default.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/team.png" width="" height="">

Select the newly created team which is displayed in the **Team** table. In the **Team** view, you can add members to your team and create projects for them to work on.

### Add users to Team

Select the **Users** tab > add your members to the team one by one by selecting the person in the drop-down list. Please be noted only the users you have invited to the Organization above can be added to this team.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/add-user.png" width="" height=""> 

### Create Projects

Select **Projects** > give a name to your project and click **Create**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/project.png" width="" height="">

You have had your organization, team, and project. You can start working with Katalon TestOps now.

## Reset and Forget Password

If you would like to change your password, please go to your **Profile** and click **Change Password** on the upper right corner.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/update-pw-1.png" width="364" height="">

In case a user forgets the password, they can click on **Forgot your password** in the **Sign-in** window and follow the instructions to update a new one. However, this solution is only available for the Organizations that have configured [Mail Server](https://docs.katalon.com/katalon-analytics/docs/ktop.html#configure-mail-server). For those Organizations without Mail Server configured, we suggest a workaround below.

1. Open **PgAdmin4**

* In Windows: go to **C:\Program Files\PostgreSQL\9.6\pgAdmin 4\bin** and double-click on **PgAdmin4**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/open-pgAdmin.png" width="" height="">

2. **PgAdmin4** starts on your browser
3. Log into the Server by entering the required password of **postgres** superuser for authentication. This password was created during the setup of PostgreSQL earlier.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/login-postgre.png" width="" height="">

4. Select the **kit** database, which is owned by the **postgres** superuser.

5. Select **Schemas > public > Tables**

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/table.png" width="" height="">

6. In Tables, locate and right-click on **user_account** > **Scripts** > **UPDATE Script**

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/update-script.png" width="" height="">

7. Copy and paste the following command in the **Query Editor** and replace the password and email of the account.

    ```groovy
    UPDATE public.user_account
        SET password='<_password_>', password_encrypted=false
        WHERE email = '<_email_>'
    ```

8. Click on the **Execute** button on the menu bar.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/execute.png" width="" height="">

   If a message indicating the query returned successfully shows up, it means you have done updating a new password for the account.

## Activate Katalon Studio with KTOP Server

After downloading Katalon Studio, you need to activate it in the **Katalon Studio Activation** dialog.

1. Enter the required information.

* Server URL: the address of your KTOP site that you configured.
* Email and Password: the account you have registered with KTOP Server.

2. Click **Activate** to connect with and retrieve Organizations from the KTOP Server.
3. Select an Organization you would like to work on in the drop-down list. Click **OK**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/activate.png" width="496" height="">

Learn more about [the integration between Katalon TestOps and Katalon Studio](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html)

## Use Katalon Plugins with KTOP Server

Katalon Plugins are to extend Katalon Studio's capabilities and integrate the software with your favorite tools. Together with KTOP and offline features of Katalon Studio Enterprise, using plugins without Internet access is an excellent complimentary feature for you to:

* Install and use all the plugins that are available on Store without the Internet required (Offline Plugins).
* Build your plugins and use them directly in Katalon Studio without publishing on Store ([Private Plugins](https://docs.katalon.com/katalon-studio/docs/private-plugins.html)).

> You need an [active license for Katalon Studio Enterprise](https://docs.katalon.com/katalon-studio/docs/license.html#paid-license) and contact [Katalon Sales team](mailto:business@katalon.com) to get the whole package of Katalon plugins.

Follow the below instructions to install and use those plugins.

### Offline plugins

To use any plugins published on Store without accessing the Internet, follow these steps:

1. Contact [Katalon Sales team](mailto:business@katalon.com) to get the whole package of Katalon plugins.
2. Unzip your downloaded plugin package.
3. Move the plugin package to **<project_name>/plugins**.
4. Open Katalon Studio and activate Katalon Studio with KTOP Sever.
5. Go to **Project > Settings > Plugins** and select the below option:

* **Local**: Katalon Studio will install plugins from the Plugins folder only.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/local.png" width="" height="">

   > Troubleshoot
   >
   > If you encounter this message, click **Cancel** to continue and double-check if you have selected the **Local** plugin repository in **Project > Settings > Plugins**.
   > <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/ktop-setup-org-team-project/reload-plugins.png" width="" height="">

### Private plugins

You can learn more about [Private Plugins](https://docs.katalon.com/katalon-studio/docs/private-plugins.html) and how to build them. After having developed a plugin successfully, move the plugin to your project folder **<project_name>/plugins**.

> Katalon Studio treats all offline and private plugins stored in your project folder **<project_name>/plugins** as local plugins. In **Project > Settings > Plugins**, specify where Katalon Studio will download plugins.

## Configure Mail Server

KTOP is designed exclusively for a restricted network environment. You need to configure a mail server to send and receive email notifications of:

* Managing users at the organization or team level.
* Executing test schedulers.

1. Go to KTOP. Refer to this [document](https://docs.katalon.com/katalon-analytics/docs/testops-op-installation.html) for how to install and set up KTOP.
2. Under an Organization, select **Settings** tab.
3. Provide the information for your mail server.

![](https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/kt-op-mail-server/kt-op-mail-server-config.png)

* **Host:** the domain name of the mail server.
* **Port:** the port to be used for that server.
* **Username & Password:** the account to authenticate with the server.
* **Protocol:** the protocol to communicate with the mail server.

4. Click **Update** to save and apply your configurations.

> Note: You can test the configuration by providing a test recipient and click **Send test email**.
