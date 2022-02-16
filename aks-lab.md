## Check the expiration date of your service principal

```bash
myResourceGroup=xxx
myAKSCluster=xxx

SP_ID=$(az aks show --resource-group $myResourceGroup --name $myAKSCluster \
    --query servicePrincipalProfile.clientId -o tsv)
az ad sp credential list --id "$SP_ID" --query "[].endDate" -o tsv
```
