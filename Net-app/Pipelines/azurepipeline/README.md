* Azure resource settings for az-cicd-webapp.yml
* Azure resource settings for az-cicd-docker.yml
* Azure resource settings for az-cicd-kubernetes.yml



## az-cicd-docker.yml
    In this file you are going to have to create two service connections for the pipeline to run correctly,
    one for your azure resource manager and a seperate one for your azure container registry. Therefore you
    would need to create the azure container registry before running the pipeline.

    Use the command below to create the resource on azure cli also create matching variables with ones on the yaml file.

```
AZURE_RESOURCE_GROUP="tailspin-space-game-rg"
REGISTRY_NAME="tailspin14559"
az configure --defaults location=westus2
az group create  --name $(AZURE_RESOURCE_GROUP) 
az acr create --name $(REGISTRY_NAME) --resource-group $(AZURE_RESOURCE_GROUP) --sku standard --admin-enabled true


```


## az-cicd-kubernetes.yml
    In this file you are going to have to create two service connections for the pipeline to run correctly,
    one for your azure resource manager and a seperate one for your azure container registry. Therefore you
    would need to create the azure container registry before running the pipeline.

    Use the command below to create the resource on azure cli also create matching variables with ones on the yaml file.

```
AZURE_RESOURCE_GROUP="tailspin-space-game-rg"
REGISTRY_NAME="tailspinspacegame9960"
AKS_NAME="tailspinspacegame-9960"
az configure --defaults location=westus2
az group create  --name $(AZURE_RESOURCE_GROUP) 
az acr create --name $(REGISTRY_NAME) --resource-group $(AZURE_RESOURCE_GROUP) --sku standard --admin-enabled true


```
<!-- Create a variable to store the ID of the service principal configured for the AKS instance.
```
clientId=$(az aks show --name $AKS_NAME --resource-group $AZURE_RESOURCE_GROUP --query "servicePrincipalProfile.clientId" --output tsv)
```

Create a variable to store the ID of the Azure Container Registry.
```
acrId=$(az acr show --name $REGISTRY_NAME --resource-group $AZURE_RESOURCE_GROUP --query "id" --output tsv)
```

Run the following az role assignment create command to create a role assignment to authorize the AKS cluster to connect to the Azure Container Registry.
```
az role assignment create --assignee $clientId --role acrpull --scope $acrId
``` -->