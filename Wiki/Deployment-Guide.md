# Deployment Guide

**Prerequisites**

To begin, you will need:
- App Service
- App Service plan
- Bot Channels Registration
- Azure Storage account
- Application Insights

A copy of the New Employee Onboarding app GitHub repo ([https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding))

- Estimated deployment time: This depends on you getting the MSIT approval. Installation itself will take about 30 to 45 mins.
- User roles needed to perform the deployment: IT admin.

### Step 1: Register Azure AD application:

Register one Azure AD application in your commercial Azure subscription: for the bot and tab app authentication

1. Log in to the Azure Portal for your subscription, and go to the **App registrations** blade [here](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
2. Click on **New registration**, and create an Azure AD application.
	- **Name**: The name of your Teams app. If you are following the template for a default deployment, we recommend "NewEmployeeOnboarding".
	-  **Supported account types**: Select **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**
	- For **Redirect URL**
		- Select **Web**
		- Set the URL to [https://token.botframework.com/.auth/web/redirect](https://token.botframework.com/.auth/web/redirect)

![multitenant_creation](/Wiki/images/multitenant_app_creation.png)

3. Select **Register**.
4. When the app is registered, you'll be taken to the app's **Overview** page. Copy the **Application (client) ID** and **Directory (tenant) ID**. We recommend that you save these ID's  in a text file, using an application like Notepad, so you can easily retrieve them as instructed at a later point in the process.
5. Verify that the **Supported account types** is set to **Multiple organizations**.


![Overview](/Wiki/images/multitenant_app_overview.png)

6. In the navigation pane, click **Certificates & secrets** to create a secret for your application. 
	- Under **Client secrets** section, click on **+ New client secret**.
	- Add a description (Name of the secret) for the secret and select an expiry time (as per the requirement). 
	- Click **Add**
	- Before leaving this page, copy the secret and save it in the text file you created earlier..

![Secret overview](/Wiki/images/multitenant_app_secret.png)

At this point you have 3 values saved to be used later:
- **Application (client) ID** which will be later used during ARM deployment as Bot Client Id and in manifest files as <<botId>>
- **Client secret** for the bot which will be later used during ARM deployment as Bot Client secret
- **Directory (tenant) ID**  

### Step 2: Create a Security Group

If you already have a security group registered in Azure AD, then skip first 4 steps below

1. Log in to the Azure Portal for your subscription, and go to the **Groups** blade [here(https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups).
2. Click on **New Group**.

![New Security Group](/Wiki/images/NewSecurityGroup.png)

3. Add members (new hires) to security group.

![Security Group Members](/Wiki/images/SecurityGroupAddMembers.png)

4. Click on **Create**.

![Create Security Group](/Wiki/images/CreateSecurityGroup.png)

5. Search for security group by group name.

![Search Security Group](/Wiki/images/SearchSecurityGroup.png)

6. Go to Security Group Overview and copy **Object ID** and save it in your text file.

![Security Group Overview](/Wiki/images/SecurityGroupOverview.png)

### Step 3: Configure SharePoint Hub

  If your SharePoint hub is already configured, you can skip the steps below, but we recommend saving the values mentioned below. You’ll use them during ARM deployment. Otherwise, get started by clicking [SharePoint configuration](TODO)

1) SharePoint site name.
2) SharePoint site new hire check list name.
3) SharePoint site tenant name.
4) Complete learning plan URL from SharePoint.
5) New hire question list name from SharePoint.
  
### Step 4: Deploy Bot and Application Insights to your Commerical Azure subscription

1.  Click on the "Deploy to Azure" button below.

[![Deploy to Azure](https://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FOfficeDev%2Fmicrosoft-teams-apps-newemployeeonboarding%2Fmaster%2FDeployment%2Fazuredeploy.json)

2. When prompted, log in to your commercial Azure subscription.
3. Azure will create a **Custom deployment** based on the ARM template and ask you to fill in the template parameters.
4. Select a Subscription and Resource group.(We recommend creating a new resource group.)
5. The resource group location MUST be in a datacenter that supports **Application Insights** and **Storage Account**. For an up-to-date list, click [here](https://azure.microsoft.com/en-us/global-infrastructure/services/?products=logic-apps,cognitive-services,search,monitor), and select a region where the following services are available:
	- Application Insights
	- Storage Account
6. Enter a **Base Resource Name**, which the template uses to generate names for the other resources.
	-	The app service names **(Base Resource Name)** must be Available (not Taken). Otherwise, the deployment will fail with a **Conflict** error.
	-	Save your selected **Base Resource Name** in your text file to be used later 
7. Fill in the following IDs in the template:
	- **Bot Client ID**: The application (client) ID of the Microsoft Teams Bot app.
	-  **Bot Client Secret**: The client secret of the Microsoft Teams Bot app.
	-  **Tenant Id**: The tenant ID of your application.

Make sure that you’ve pasted the values exactly as-is, with no extra spaces. The template checks that GUIDs are exactly 36 characters.

8.	If you wish to change the app name, description, and icon from the defaults, modify the corresponding template parameters.
9.	Click on "Review+Create" to start the deployment. It will validate the parameters provided in the template .Once the validation is passed, click on create to start the deployment.
10.	Wait for the deployment to finish. You can check the progress of the deployment from the "Notifications" pane of the Azure Portal. It can take up to 5 minutes for the deployment to finish.

### Step 5: Deploy remaining resources to your Azure Government subscription


1.  Click on the "Deploy to Azure" button below.

[![Deploy to Azure](https://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FOfficeDev%2Fmicrosoft-teams-apps-newemployeeonboarding%2Fmaster%2FDeployment%2Fazuredeploy.json)

2. When prompted, log in to your Azure Government subscription.
3. Azure will create a **Custom deployment** based on the ARM template and ask you to fill in the template parameters.
4. Select a Subscription and Resource group.(We recommend creating a new resource group.)
5. The resource group location MUST be in a datacenter that supports **Application Insights** and **Storage Account**. For an up-to-date list, click [here](https://azure.microsoft.com/en-us/global-infrastructure/services/?products=logic-apps,cognitive-services,search,monitor), and select a region where the following services are available:
	- Application Insights
	- Storage Account
6. Enter the same Base Resource Name, that you gave while bots deployment in your Azure commercial.
	-	The app service names **(Base Resource Name)** must be Available (not Taken). Otherwise, the deployment will fail with a **Conflict** error.
	-	Save your selected **Base Resource Name** in your text file to be used later 
7. Fill in the following IDs in the template:
	- **Bot Client ID**: The application (client) ID of the Microsoft Teams Bot app.
	-  **Bot Client Secret**: The client secret of the Microsoft Teams Bot app.
	-  **Tenant Id**: The tenant ID of your application.
	-  **Manifest Id** : This needs to be same as manifest ID provided in manifest.json file inside Manifest folder.
	-  **Human Resource Team Link**: The url for the Microsot Teams team your Human Rresources department uses (where you want the app to send employee feedback notifications). This URL starts with https://teams.microsoft.com/l/team/. 
	-  **Site Name**: New employee onboarding site name.
	-  **New Hire Check List Name**: New hire onboarding checklist name.
	-  **Site Tenant Name**: SharePoint tenant name.
	-  **Share Feedback Form Url**: The URL for the survey new employees will take to share feedback. Go to [here](https://forms.office.com/) to create survey MS Forms and copy the link by clicking on **Share** button if not created before.
	-  **Complete Learning Plan Url**: Complete learning plan list URL.
	-  **New Hire Question List Name**: New hire question list name from SharePoint Hub.
	-  **Security Group Object Id**: Security group ID (Required for user role).
	-  **delayInPairUpNotificationInDays**: Number of days to delay in pair up notification.
	-  **newHireRetentionPeriodInDays**: Number of days for new hire retention period.

Make sure that you’ve pasted the values exactly as-is, with no extra spaces. The template checks that GUIDs are exactly 36 characters.

8.	If you wish to change the app name, description, and icon from the defaults, modify the corresponding template parameters.
9.	Click on "Review+Create" to start the deployment. It will validate the parameters provided in the template .Once the validation is passed, click on create to start the deployment.
10.	Wait for the deployment to finish. You can check the progress of the deployment from the "Notifications" pane of the Azure Portal. It can take up to 5 minutes for the deployment to finish.


### Step 6: Set up authentication for the app

1. Go back to the **App Registrations** page [here](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps)
2. Enter the **BotId** created in Step 1 under **Owned applications** search box.
3. Click on the application (this should be the same application registered in step 1)
4. From the left menu under **Manage**, select **Authentication** .
5. Select **Accounts in any organizational directory (Any Azure AD directory - Multitenant)** under Supported account types and click **+Add a platform**.
6. On the flyout menu, select **Web**

![Set up authentication for the app](/Wiki/Images/RedirectUrlMenu.png)

7. Add `https://[baseresourcename].azurewebsites.us/signin-simple-end` under Redirect URLs and select the check boxes **Access tokens** and **ID tokens** and then click **Configure**.

8. From the left menu under **Manage**, select **Expose an API**.

![Set up authentication for the app](/Wiki/Images/ExposeAnApiMenu.png)

9. Select the **Set** link to generate the Application ID URI in the form of `api://{BotID}`. Insert your app Domain (with a forward slash "/" appended to the end) between the double forward slashes and the GUID. The entire ID should have the form of: `api://app Domain/{BotID}`
- for e.g.: `api://newhireonboarding.azurewebsites.us/c6c1f32b-5e55-4997-881a-753cc1d563b7`.
10. Select the **Add a scope** button. In the panel that opens, enter `access_as_user` as the **Scope name**.
11. Set Who can consent? to "Admins and users"
12. Fill in the fields for configuring the admin and user consent prompts with values that are appropriate for the `access_as_user` scope. Suggestions:
	- **Admin consent display name**: New Employee Onboarding
	- **Admin consent description**: Allows Teams to call the app’s web APIs as the current user.
	-  **User consent display name**: Teams can access your user profile and make requests on your behalf
	-  **User consent description:** Enable Teams to call this app’s APIs with the same rights that you have
	-  Ensure that **State** is set to **Enabled**
	-  Select **Add scope**

Note: The domain part of the **Scope name** displayed just below the text field should automatically match the **Application ID** URI set in the previous step, with `/access_as_user` appended to the end; for example:
- `api://newhireonboarding.azurewebsites.us/c6c1f32b-5e55-4997-881a-753cc1d563b7/access_as_user`

13. In the same page in below section **Authorized client applications**, you identify the applications that you want to authorize to your app’s web application. Each of the following IDs needs to be entered. Click "+Add a client application" and copy-paste the below id and select checkbox "Authorized scopes". Repeat the step for second GUID.

- `1fec8e78-bce4-4aaf-ab1b-5451cc387264` (Teams mobile/desktop application)
- `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` (Teams web application)

14. From the left menu, select **API Permissions**, and  add the follow permissions of Microsoft Graph API :

**Delegated Permissions**:
- User.ReadBasic.All
- User.Read.All
- Directory.Read.All
- Directory.AccessAsUser.All
- Team.ReadBasic.All
- TeamSettings.Read.All
- openid
- profile
- User.ManageIdentities.All

**Application Permission**:
- User.Read.All
- Sites.Read.All
- GroupMember.Read.All
- Group.Read.All
- TeamsAppInstallation.ReadWriteSelfForUser.All

**Note:** The detailed guidelines for registering an application for SSO Microsoft Teams tab can be found [here](https://docs.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/authentication/auth-aad-sso)


### Step 7: Set up authentication for bot

1. Note the name of the bot that you deployed, which is [BaseResourceName].
2. Go to azure portal [here](https://portal.azure.com/) and search for your bot.
3. Click on the bot in the application list. Under **Settings**, click on **Add Setting**.
4. Fill in the form as follows:

	a. For **Name**, enter **NewHireOnboardingAuth**. You'll use it in your bot code.

	b. For **Service Provider**, select **Azure Active Directory**. Once you select this, the Azure AD-specific fields will be displayed.

	c. For Client ID, enter the application (client) ID that you recorded earlier.

	d. For **Client secret**, enter the secret that you created to grant the bot access to the Azure AD app.

	e. For **Grant type** , enter **authorization_code**.

	f. For Login URL , enter "https://login.microsoftonline.com". Insert your login URL (without a forward slash "/" appended to the end)

	g. For **Tenant ID**, enter the directory (tenant) ID that you saved earlier for your AAD app. This is the tenant associated with the users who can be authenticated.

	h. For **Resource URL** , enter "https://graph.microsoft.com/".

	i. For **Scopes**, keep it blank.

	j. Click **Save**.

### Step 8: Create the Teams app packages

This step covers the Teams application package creation for teams scope and make it ready to install in Teams.

1. Open the `Manifest\manifest.json` file in a text editor.
2. Change the placeholder fields in the manifest to values appropriate for your organization.
* `developer.name` ([What's this?](https://docs.microsoft.com/en-us/microsoftteams/platform/resources/schema/manifest-schema#developer))
* `developer.websiteUrl`
* `developer.privacyUrl`
* `developer.termsOfUseUrl`
3.	Change the <<botId>> placeholder to your **Azure AD application's ID ** from above. This is the same GUID that you entered in the template under Bot Client ID.
4.	Change <<SharePointNewHireCheckListUrl>> placeholder with Complete learning plan URL which you have recorded before and also make sure replace << azurefdurl >> with 'https://[baseresourcename].azurewebsites.us'.
5.	In the validDomains section, replace the <<appDomain>> with your Bot App Service's domain. This will be [BaseResourceName].azurewebsites.us. For example if you chose "newhireonboarding " as the base name, change the placeholder to newhireonboarding.azurewebsites.us.
6.	Note : please make sure to not add https:// in valid domains. Also make sure to add "token.botframework.com" and SharePoint tenant name that you have recorded before in "validDomains" section.
7.	In the webApplicationInfo section, replace the <<botId>> with Bot Client ID of the app created in Step 1. Also replace <<ApplicationIdURI>> with following Application URI appended with bot client id. This will be as follows for example api:// newhireonboarding.azurewebsites.us/19c1102a-fffe-46c4-9a85-016bec13e0ab where newhireonboarding is the base resource URL and 19c1102a-fffe-46c4-9a85-016bec13e0ab is the bot client id.
8.	Create a ZIP package with the manifest.json,color.png, and outline.png. The two image files are the icons for your app in Teams.
9.	Make sure that the 3 files are the top level of the ZIP package, with no nested folders.


![Create the Teams app packages](/Wiki/Images/ManifestUI.PNG)

## Step 9: Run the apps in Microsoft Teams

1. If your tenant has side loading apps enabled, you can install your app by following the instructions
[here](https://docs.microsoft.com/en-us/microsoftteams/platform/concepts/apps/apps-upload#load-your-package-into-teams)
2. You can also upload it to your tenant's app catalog, so that it can be available for everyone in your tenant to install. See [here](https://docs.microsoft.com/en-us/microsoftteams/tenant-apps-catalog-teams)
3. We recommend using [app permission policies](https://docs.microsoft.com/en-us/microsoftteams/teams-app-permission-policies) to restrict access to this app to the members of the experts team.
4. Install the app (the `NewHireOnboarding.zip` package) to your team.

## Step 10: Update Teams app Id in configuration

1. Go to the Teams admin portal, [here](https://admin.teams.microsoft.com/dashboard)
2. Go to **Manage app** section from side menu bar

![Manage app dashboard](/Wiki/images/ManageDashboard.png)

3. Search for **New Employee Onboarding** 

![Search app](/Wiki/images/SearchApp.png)

4. Copy the **App ID**

![Copy app id](/Wiki/images/CopyAppId.png)

5. Go back to Azure Portal [here](https://portal.azure.com/) and search app service by [Base Resource Name] which you have provided during deployment.

![Search service](/Wiki/images/SearchAppService.png)

6. Go to Configuration from the side menu bar and double click on **App:TeamsAppId**, Update its value with app Id and make sure to save the changes after updating.

![Update catalog](/Wiki/images/UpdateCatalogId.png)

6. Restart the app service

![Restart service](/Wiki/images/RestartAppService.png)

### Troubleshooting

Please see our [Troubleshooting](Troubleshooting) page.