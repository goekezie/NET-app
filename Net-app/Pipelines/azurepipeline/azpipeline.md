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