Continuous Deployment service in Azure App Services and Azure Function Apps offers merging latest code changes to Azure hosted environment from GitHub. It helps to seamlessly update the Azure services without need of new deployment.

### Continuous deployment in Azure App Services

Please follow below steps to deploy latest changes to the app service:

1. Log in to the Azure Portal for your subscription.

1. Select App Services from left menu blade

    ![Azure app service menu blade](/wiki/Images/Azure-appservice-menu.png)

1. Search and select the app service name (search for the `base resource name`) which is created during first deployment. For e.g. `constoso-newemployeeonboarding`.azurewebsites.net

1. Select Deployment Center under menu blade

    ![Deployment center in Azure app service](/wiki/Images/Deployment-center.png)

1. Click on Sync to synchronize the latest bits from GitHub master branch

    ![Sync GitHub deployment](/wiki/Images/sync-github.png)

    _note_: please make sure that `Repository` name is pointing to correct OfficeDev repo git path.

1. Once the deployment is successful, please restart the app service and check the application is working.