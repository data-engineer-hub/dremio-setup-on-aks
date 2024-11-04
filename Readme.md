## Create an AKS cluster

Node Type: standard_ds3_v2


RESOURCE_GROUP="dremio-poc-rg"
CLUSTER_NAME="dremio-poc-cluster"
LOCATION="eastus"
NODE_SIZE="Standard_DS3_v2"  # For a POC, this is smaller and cost-effective
NODE_COUNT=3                 # Adjust based on your POC requirements

#### Create a resource group:
az group create --name $RESOURCE_GROUP --location $LOCATION

#### Create the AKS cluster:

az aks create \
  --resource-group $RESOURCE_GROUP \
  --name $CLUSTER_NAME \
  --node-vm-size $NODE_SIZE \
  --node-count $NODE_COUNT \
  --location $LOCATION \
  --generate-ssh-keys

Connect to the cluster:

az aks get-credentials --resource-group $RESOURCE_GROUP --name $CLUSTER_NAME


## Create a Storage Account

## Create a client