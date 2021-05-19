
# SharePoint configuration

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

Note: Make sure the site list **New hire checklist** contains below columns & column names should also be same:  
  
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