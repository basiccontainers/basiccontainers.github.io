# Create and Access AKS 
In this exercise  we will create a Kubernetes cluster that can autoscale and is configured to pull images  automatically from our registry . To achieve this so we will:

- Use the Azure CLI
- Configure your local access credentials to control your cluster using kubectl
- Take some first steps
- Run our first pod
## Create the cluster
 - Create resoruce group for cluster 
```
az group create --location westeurope --name $resourceGroup 
```
- Create AKS: The following script creates an AKS with the following configuration 
    | Parameter  | Description |
| ------------- | ------------- |
| Subscription  | Select your Azure subscription.  |
|--resource-group  |  The resource group where the AKS cluster will be created  |
| --nodepool-name  |   Name of the nodepool where our apps will run   |
| --attach-acr|  The resourceid or name of the ACR registry. This is the name of the registry in the Registry overview page. Alternatively you can execute the following command   ``az acr show  --name ivanacrdemo  --query id``|
| Registry name  | Enter a unique name and make a note of it for later.  |
| --min-count|  The min number of nodes that will run when using cluster-autoscaler. When the cluster down scales it will not go below this value  |
| --max-count | The max numebr of nodes that the cluster auto scaler will scale to   | 
| --zones 3 | Spread the node pool vms across multiple zones for resilency. Can be 1,2,3. This indicates how many zones it should be spread across |
|  --enable-cluster-autoscaler | Enabled cluster auto scaler | 
|  --kubernetes-version | The version of kubernetes to deploy |
| SKU  | standar |
-- Set variables 
```
## Set Variables 
RESOURCE_GROUP="ivanresourcegroup"
AKS_CLUSTER="mysimpleaks"
ACR_REGISTRY="ivanacrdemo"
```
-- Create Cluster  
```
## Create Cluster 
az aks create \
 --resource-group $RESOURCE_GROUP \
 --node-vm-size=Standard_D2s_v3 \
 --kubernetes-version=1.20.9 \
 --name $AKS_CLUSTER \
 --nodepool-name="apppool" \
 --enable-cluster-autoscaler \
 --min-count 1 \
 --max-count 2 \
 --zones 3 \
 --attach-acr $ACR_REGISTRY \
 --node-count 1 \
 --generate-ssh-keys 
```

Access the cluster
Browse the Dashboard 
Scale node pool 
Access the dashboard 















