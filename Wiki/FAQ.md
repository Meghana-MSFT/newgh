## IT requirements

 
1.  Describe the IT resources that are needed for build, deployment, and maintenance and technical support? How much time is expected and how many resources at each stage –
    - Check [Getting started](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding/wiki/Getting-started) guide for more information.
    - Technical support is covered under MSIT license. Issue can be raised directly on github and are monitored
    - Teams IT admin is required to install the app. She/he should also have access to Azure subscription for registering bot
    - Deployment comes with a step-by step guide such as this one so that it is very easy for IT admin to follow the steps and get it running - [Getting started](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding/wiki/Getting-started)
    - New Employee App template is open source and will be published here – https://docs.microsoft.com/en-us/microsoftteams/platform/samples/app-templates on 27th October. It’s free to use off the shelf and does not require building
    - We need Azure subscription for bot  from a resources point of view. We are assuming sharepoint is already available.
2.  Is there an IT team on your end who would do this or would the WWL IT team need to do the above work?
    - Teams Engineering does not deploy the app templates in FY21. They are really easy to deploy and take about 30 mins. We recommend getting one of the Partners to deploy with your IT team
3.  What is the timeline to deploy the App having IT as a dependency?
    - This depends on you getting the MSIT approval. Installation itself will take about 30 mins
4.  How are roles targeted for the share point – where is that information pulled from (Dewey) and is that work that IT would do?
    - IT admin or tenant admin should configure the roles in SharePoint hub.
5.  Who from our organisation we need to start deployment or get approvals for app deployment?
    - IT admin or tenant admin should deploy the app.
6.  In  large tenants, customer’s would like to keep the back-end Azure components (e.g. Storage, App Insights, App Functions etc.) common across app templates; for reasons of easier visibility to incremental costs & avoiding security approvals every time a new app template needs to be rolled-out. How do we do this? 
    - This requires for CSM/CSA to break-down Azure BOQ components to provide clarity on incremental costs components. Part of this exercise also involves providing clarity on forecasting minimum & maximum cost estimates per app template, for IT to provide justifications internally and seek required approval. (PFA FAQ BOT Sizing FYR, in this regard)
 
## Cost
- What are the IT costs involved? 
    - $75 for 1000 users/month using the app

## Support for Issues

- How do we report an issue?
    - Please report the issue [here](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding/issues/new)
- When will it be resolved? Is there an SLA fir support?
    - No SLA defined.

## Technical Bandwidth needed to maintain the app
- What are the expectations to manage the App in terms of set up and support? Does this require a full-time person focus on set up and scale (new roles)? Or more? 
    - Teams app does not require maintenance. We do version updates as well, which can be easily updated if customers come with new requirements. After deployment, our assumption is that only learning content in SharePoint may need refresh occasionally. At the time of deployment, admin will configure a group for new hires. All that needs to happen with time is that new hires get added to that group. App automatically picks up their manager from AAD and installs the app for new hire and manager if not already installed.

## How do we update content for the app?
- Change the text references in the associated resource(Strings.resx) file from NEO to the domain on which it should cater to.
## Cost for maintenance of the app is any?
- Please refer - [Cost estimate](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding/wiki/Cost-estimate)

## Customizations
- What happens when there are taxonomy changes?
    - You can configure this easily. It should be okay. Please share an example so that I can provide more information
    - Refer here [Customization](/wiki/Take-it-further.md)

## Version Updates

- How frequently does Microsoft update the app?
 - If we customise the app, how do we role it out?
 - If Microsoft updated the code. how will our IT team update the app that has already been deployed?

 ## Training for App

 - What kind of training and support is provided to the program team by your team?
    - Teams App comes with help documentation and helpful suggestions in welcome card such as app tour. We can do 1 session for any questions.

## Support for Languages/Localisation

- What are the options to set-up the Teams templates in multiple languages? 
    - App Templates come with localization support and can be used in other languages easily to pick up Teams languages. We are also going to update more language strings in this quarter.
    - When localizing your app there are three major areas you need to consider.
        - Your AppSource listing (if you're publishing to the app store).
        - The end-user facing strings in your app manifest (for example bot commands).
        - Responding to localized text submitted from your users.   
    - All apps are supported and provided with a resource (.resx) file, which will be used based on current user locale.   
    - The resource file contains strings used by application
    - Bot command and messaging extensions tabs are pre-configured values provided in manifest file. Localization of such files will be handled by leveraging the localizationInfo.  
