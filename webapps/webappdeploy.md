# Deploy a web app by using an image from an Azure Container Registry repository
You can deploy a web app to Azure App Service directly from Azure Container Registry.

In the example scenario, the team wants to host the web app in App Service. They need to configure App Service to retrieve the image for the web app from the repository in Container Registry.

In this section , you'll learn how you can configure App Service to deploy a web app from a repository in Container Registry.

## Create and deploy a webapp 
In the example scenario, you have uploaded the image for the web app to Azure Container Registry and is now ready to deploy the web app.
- In  Azure portal home page, and under Azure services, select Create a resource. The Create a resource pane appears.
- Search for "Web App" or on the left  select Web, and under Popular offers, select Web App.
- On the Basics tab, enter the following values for each setting.

| Setting   | value |
| ------------- | ------------- |
| Subscription | Select your default Azure subscription in which you are allowed to create and manage resources. | 
| Resource Group | From the dropdown list, select the existing resource group learn-deploy-container-acr-rg. | 
| Name |  Enter a unique name and make a note of it for later.| 
| Publish |  Docker Container | 
| Operating System | Linux | 
| Region |  Select the same location that is close to you from previous exercise. | 
| App Service plan | Use the default.| 
- Select Next: Docker >.
- On the Docker tab, enter the following values for each setting.
