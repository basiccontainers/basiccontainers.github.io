# GitHub Actions 
In this lab you will: 
 - Integrate Azure Appservices with Azure 
 - Create a github actions workflow 
 - Workflow is triggers on each push to master 
 - A container image  is built and pushed to ACR
 - A AppService redeployment is triggered on successful build 

A github actions workflow is defined by a YAML (.yml) file in the /.github/workflows/ path in your repository. This definition contains the various steps and parameters that are in the workflow. These configurations and setup can be manually setup per project. this involves secret configuration and service principal setup. In this lab we are going to use App Services Deployment center to automate all these tasks. 


## Setup 

A workflow is defined by a YAML (.yml) file in the /.github/workflows/ path in your repository. This definition contains the various steps and parameters that are in the workflow.

For an Azure App Service container workflow, the file has three sections:

![webapp](./img/githubactions-deploy.png)
## Reference 
- Patterns container : https://docs.microsoft.com/en-us/azure/app-service/deploy-best-practices#continuously-deploy-containers 
- Github Actions: https://docs.microsoft.com/en-us/azure/app-service/deploy-best-practices#use-github-actions
- Web app Deployment  https://docs.microsoft.com/en-us/azure/app-service/deploy-ci-cd-custom-container?tabs=acr&pivots=container-linux
