# Deploying a Container to Webapps 



# Create a resource group.
# Create a resource group.
resourceGroup="ivanresourcegroup"
appserviceplan="ivanappservice"
appname="myapplicationivans" ## This should be unique
az group create --location westeurope --name $resourceGroup

## Create App Service plan 
az appservice plan create --name $appserviceplan --resource-group $resourceGroup --is-linux

## Create application based on container
To change an existing custom container app from the current Docker image to a new image, use the following command:


az webapp create --resource-group $resourceGroup --plan $appserviceplan  --name $appname --deployment-container-image-name mcr.microsoft.com/azuredocs/azure-vote-front:v1
## Change port 
By default, App Service assumes your custom container is listening on port 80. If your container listens to a different port, set the WEBSITES_PORT app setting in your App Service app. You can set it via the Cloud Shell. In Bash:
az webapp config appsettings set --resource-group $resourceGroup --name $appname --settings WEBSITES_PORT=8080

##.azurecr.io/appsvc-tutorial-custom-image:latest

## see https://docs.microsoft.com/en-us/cli/azure/webapp/config/container?view=azure-cli-latest
## https://docs.microsoft.com/en-us/azure/app-service/tutorial-custom-container?pivots=container-linux

### Staging
https://docs.microsoft.com/en-us/azure/app-service/scripts/cli-deploy-staging-environment?toc=/cli/azure/toc.json

## Deploy container to service 
az webapp config container set --docker-custom-image-name MyDockerCustomImage --docker-registry-server-password StrongPassword --docker-registry-server-url https://{azure-container-registry-name}.azurecr.io --docker-registry-server-user DockerUserId --name MyWebApp --resource-group MyResourceGroup



# Customize and build image using ACR 
 Download docker source. modify 



# 

# 