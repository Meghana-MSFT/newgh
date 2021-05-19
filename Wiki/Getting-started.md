# Getting started

New Employee Onboarding is an easy app to deploy by IT admins. New Employee Onboarding app uses SharePoint New Employee Checklist as a common point between SharePoint New Employee Onboarding Solution and Teams app. App supports installation for complete SharePoint Site or just Teams component without the complete Site.

In this guide, we will walk you through the actions supported by each persona. We also shed light upon ;setting up the SharePoint list for New Hire Checklist so that HR teams can update resources or trainings for New Hires with an easy to maintain SharePoint list. 

**Actions Per Persona**

NEO enables New Employees to - 

	- Complete a quick introduction
	- View the complete learning plan 
	- View and complete the tasks and learning available in New Employee Checklist
	- Submit a survey
	- Receive weekly notifications to view learnings for current week
	- View and complete the weekly sent learnings 
	- Provide feedback on the onboarding process 
	- Use the icebreaker functionality to get notified of matches with existing team members
	- Pause these matches anytime 

NEO enables Hiring Managers to -

	- Learn mroe about the New Employee Checklist for New hires
	- Review the introductions of all reportees who have newly joined the organisation
	- Share introductions in any channel in Teams where app is available

NEO enables HR/Admin Teams to - 

	- Update the learning content in New Eemployee Checklist for New Hires
	- Configure the questions which are shown to New Employees for sharing quick introduction
	- Configure time period for an employee to be considered new hire
	- Add the Tean to recieve notifications for all feedback from new employees instantly
	- View and Download submitted feedback by new hires
	- Configure the link for pulse survey for new employees

Additionally, there are also customisations that your IT team can do easily. Please check the Taking it further using Customisations page for more information


**Architecture Model** 

![Solution Overview](/wiki/images/ArchitectureDiagram.png)

**Reference Data**

The application can be tailored by an administrator for your organization using the New Employee Onboarding app.

**Settings to be configured by Organization's IT team**

It is important that admin configure key settings for New Employee Onboarding app.

1.SharePoint site configuration

## Go to below URL to do site provisioning:

[https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19)  
* Login with your tenant admin credentials.

![sharepoint_overview](/Wiki/images/Sharepoint_Image1.png)

* Click on “Add to your tenant” button.

![sharepoint_addtenant](/Wiki/images/Sharepoint_Image2.png)

![sharepoint_addtenant](/Wiki/images/Sharepoint_Image3.png)

* Provide above details & click on **Provision** button.

![sharepoint_provision](/Wiki/images/Sharepoint_Image4.png)

![sharepoint_provision](/Wiki/images/Sharepoint_Image5.png)

![sharepoint_provision](/Wiki/images/Sharepoint_Image6.png)

![sharepoint_provision](/Wiki/images/Sharepoint_Image7.png)

We recommend that you copy site name and tenant name from onboarding hub URL.for eg: https://m365x998017.sharepoint.com/sites/NewEmployeeOnboarding sitename refers to "NewEmployeeOnboarding" and tenant name will be "m365x998017.sharepoint.com", using an application like Notepad. We will need these values later for ARM deployment.

![sharepoint_provision](/Wiki/images/Sharepoint_Image8.png)

![sharepoint_provision](/Wiki/images/Sharepoint_Image9.png)

To get introduction question list and new hire checklist name, Go to site contents and copy the list names **New hire checklist** as "New hire check list name" and **NewHireQuestionnaire** as "New hire question list name" into Notepad.

![sharepoint_home](/Wiki/images/Sharepoint_Image13.png)

* Configure new hire introduction questions:

![sharepoint_addquestion](/Wiki/images/Sharepoint_Image16.png)

![sharepoint_addquestion](/Wiki/images/Sharepoint_Image17.png)

* New hire checklist content:

![sharepoint_content](/Wiki/images/Sharepoint_Image18.png)

We recommend that you copy **New hire checklist content URL** as "Complete learning plan URL" value into a text file, using an application like Notepad. We will need these values later for ARM deployment.

![sharepoint_content](/Wiki/images/Sharepoint_Image19.png)

Note: Make sure the site list **New hire checklist** contains below columns &  column names should also be same:  
  
**1) Title  
2) Task name  
3) Complete by  
4) Notes  
5) Resource  
6) Link  
7) Task image**

If not visible any of the column names Go to Add column & **Show/hide columns** section.

![sharepoint_task](/Wiki/images/Sharepoint_Image20.png)

Select columns and click on Apply button to show all the columns.

![sharepoint_task](/Wiki/images/Sharepoint_Image21.png)

Your column will be added to the list like below:

![sharepoint_task](/Wiki/images/Sharepoint_Image22.png)

## Add new content to the list:

* Click on **New** button to add item to the list like below:

![sharepoint_newcolumn](/Wiki/images/Sharepoint_Image23.png)

* Provide the Task image column url:

 a) Go to documents folder & click on any uploaded image.

 ![sharepoint_upload](/Wiki/images/Sharepoint_Image24.png)

 b) Click on View original & copy the content URL & provide it’s value in Task image column while adding the item in list:

![sharepoint_upload](/Wiki/images/Sharepoint_Image25.png)

## Add Resource Link value in "Link" column.

Copy the document link URL like .pdf/.png from Documents folder if not uploaded any file before follow below step to add files to document & put it in **Link** column  
After filling the details, click on “Save” button.

**Upload files:**

![sharepoint_upload](/Wiki/images/Sharepoint_Image26.png)

* Click on upload button to upload the images or documents:

![sharepoint_upload](/Wiki/images/Sharepoint_Image27.png)

* Browse & upload the files:

![sharepoint_upload](/Wiki/images/Sharepoint_Image28.png)

**Application settings description**

1. **Site Name**: New employee onboarding site name.
2. **New Hire Check List Name**: New hire onboarding checklist name.
3. **Site Tenant Name**: SharePoint tenant name.
4. **Share Feedback Form Url**: Go to [here](https://forms.office.com/) to create survey MS Forms and copy the link by clicking on **Share** button if not created before.
5. **Complete Learning Plan Url**: Complete learning plan list URL.
6. **New Hire Question List Name**: New hire question list name from SharePoint Hub.
7. **Security Group Object Id**: Security group ID (Required for user role). 
8. **delayInPairUpNotificationInDays**: Number of days to delay in pair up notification.
9. **newHireRetentionPeriodInDays**: Number of days for new hire retention period.


**User Personas:** Behavior of the application will vary as per the user roles whether it is HR, Hiring Manager or a New hire:

 **New Hire (Employee)**

Desired state:​

	- Need to experience a smooth onboarding process
	- Need to find all the required information in one place
	- Need to build a network to learn from experienced/senior employees

 **Learning Coordinator (HR Team)**

Desired state:​

	- Need to apply a curated and consistent onboarding process across organization​
	- Need to create a sense of place for new employees to meet their unique needs​
	- Need to create and manage learning resources for managers​

 **Hiring Manager**

Desired state:​

	- Need to approve/reject introductions and post them in extend organizational teams​
	- Need to coordinate for equipment, onboarding plan sharing, set up monthly connects and more​
	- Need to avoid overwhelming new employees and support them for long-term retention and enhanced productivity​

**User Flow**

1. **HR/Admin organize information for New Employees​**

	Avoid overwhelming new employees by providing them with curated onboarding journey
![Onboarding Journey Start screen](/wiki/images/Onboarding_Journey_Start.png)
Onboarding check list
![Onboarding Journey Check List screen](/wiki/images/Onboarding_Journey_CheckList.png)

2. **New employees receiving a welcome card as soon as app pre-installs​**

	First Run Experience for the new employee to share a quick introduction
![New hire welcome screen](/wiki/images/NewEmployee-WelcomeCard.png)

	The new hires can describe themselves briefly, share their likes and dislikes about various things in their introduction​
![New hire introduce screen](/wiki/images/NewHireIntro.png)
	
	NEO shares the introduction to the Hiring Manager and posts timely updates on the progress via notifications​
![New hire introduce validation screen](/wiki/images/NewHire_Intro_Posted.png)

	Once the introduction is shared for Manager’s approval, NEO shows an update about the approval as ‘pending’ till the time it is approved by the Manager​
![New hire weekly plan screen](/wiki/images/NewHire_Intro_Validation.png)

3. **Managers review quick introduction**

	Enable managers to review and post introductions to a Teams channel or share feedback
![Hiring Manager approve screen](/wiki/images/HM_Approve.png)

	Hiring Managers can know more about the new hires with the available option in the new employee intro card
![Hiring Manager approve screen](/wiki/images/HiringManager_TellMeMore.png)

	Hiring Managers can leave a feedback if they feel the intro can be improved, NEO shares the comments with the new hire instantaneously
![Hiring Manager approve screen](/wiki/images/HiringManager_TellMeMoreCard_Notification.png)

	Enable new hires to receive notifications to improve introductions right away by working on the comments shared by managers
![Hiring Manager approve screen](/wiki/images/NewHire_TellMeCard.png)

	Hiring Managers can immediately select the team and the channel they want to post this intro into
![Hiring Manager approve screen](/wiki/images/HiringManager_SelctTeamToPost.png)

	Managers can quickly post the introduction to Teams’ channels using Approve button
![Hiring Manager approve screen](/wiki/images/HiringManager_TeamPostNotification.png)

	As soon as Manager’s post an introduction in a channel, NEO notifies everyone in that channel
![Hiring Manager approve screen](/wiki/images/HM_PostIntroInTeam.png)

	Users can view complete for new employees by clicking on ‘See More Details’
![Hiring Manager approve screen](/wiki/images/HiringManager_TeamPostNotification_ReadMore.png)

4. **Review Introductions for all new reportees**: Managers can review and post all introductions in one shot using the bot command!

	Hiring Managers can review all introductions in 1 shot
![Hiring Manager approve screen](/wiki/images/HiringManager_ReviewIntro.png)

	Hiring Managers can review all introductions in 1 shot
![Hiring Manager approve screen](/wiki/images/HM_ReviewIntro.png)

	Hiring Managers can approve intro or access more information about it and select the team and the channel to post it in
![Hiring manager approve introduction screen](/wiki/images/HM_Approve.png)
![Hiring Manager approve screen](/wiki/images/HiringManager_SelctTeamToPost.png)
![Hiring manager post intro screen](/wiki/images/HM_PostIntroInTeam.png)

5. **New Employees Checklist:** 
	
	New employees can use new employee checklist to find all resources/tasks for the current week. Clock for new employee starts when they get added to AAD as a new employee and app is preinstalled for them

	New hires can view tasks for the current week by clicking on weekly plan
![Hiring manager post intro screen](/wiki/images/NewEmployee-WelcomeCard.png)
![Hiring manager post intro screen](/wiki/images/NewHire_WeeklyLearningCard.png)

	Clicking on a learning opens a new card. pptx, xlsx, docxs, images open inside Teams and everything else is redirected to browser
![Hiring manager post intro screen](/wiki/images/NewHire_LearningContent.png)

	Automatically guide employees through their onboarding journey, managers can view and access a similar checklist
![Hiring manager post intro screen](/wiki/images/NewEmployeeCheckListTab.png)

6. **Weekly notification for checklist**

	New Employees receive weekly notification by the Neo app for tasks for the current week.
New Employees stop receiving notification once the new hire has stopped being a new hire after a time period set by your company. For example, 90 days

	The new hires receive weekly notifications for completing their scheduled tasks for the current on Mondays
![Hiring manager post intro screen](/wiki/images/Learning_Weekly_Notification.png)

	Users can leverage bot commands to quickly do everything, right from viewing their plan to sharing feedback
![Hiring manager post intro screen](/wiki/images/User_Feedback_Action.png)

7. **New Employees’ Pulse Survey**

	Human Resources/Admin teams can set the survey at the time of deployment to encourage new employees to share their feedback and review feedback using MS Forms

	Survey new hires on the impact of your onboarding program and improvement areas
![Hiring manager post intro screen](/wiki/images/Pulse_Survey.png)

	Configure survey questions using Microsoft Forms or any other survey tool. URL can be updated for the survey
![Hiring manager post intro screen](/wiki/images/Pulse_Survey_MSForm.png)

8. **Review feedback anytime**

	New Employees are enabled to share feedback on a resource/task in new employee checklist or simply use the bot command to share feedback that can be reviewed by HR

	The new hires can collaborate and submit ideas or share feedback for improving the learning
![Hiring manager post intro screen](/wiki/images/Share_Feedback.png)

	HR team will be notified, and feedback shared by new hires is available in feedback tab in HR team where NEO is installed
![Hiring manager post intro screen](/wiki/images/Feedback.png)

9. **Nudge new employees to connect to the extended team**

	Enable new employees to get to know more about their extend team with Icebreaker feature

	Connect with the extended team using Icebreaker
![Hiring manager post intro screen](/wiki/images/IceBreak.png)
	Create meetings, initiate chats to interact with your match right away
![Hiring manager post intro screen](/wiki/images/IceBreak_CreateMeeting.png)

10. **Use NEO in Teams**

	Enable new employees to use and take advantage of Neo app by installing it in your team

	Empower new hires and Hiring Managers to collaborate on onboarding, learning and interacting by installing the NEO app
![Hiring manager post intro screen](/wiki/images/Team_WelcomeCard.png)

**Updating the Applications**

Start by downloading the new Newemployeeonboarding.zip file from this github repository. See the Latest Update section for a table of the latest versions.

Important: updating an app will replace any customizations you have made to the template. Please document any revisions to menus and formulas separately before proceeding. You can also save the original app to your computer as an .msapp file and open it in another browser tab to copy content over to the new version. Note that you can always revert to a previous version by accessing the version history of an app.

**To update the app:**

Go to app store and update the manifest with the latest build version you have.