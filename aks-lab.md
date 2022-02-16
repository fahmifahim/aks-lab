## Create new service principal

```bash
az ad sp create-for-rbac --role Contributor

    Result sample: 
    {
      "appId": "7d837646-b1f3-443d-874c-fd83c7c739c5",
      "name": "7d837646-b1f3-443d-874c-fd83c7c739c",
      "password": "a5ce83c9-9186-426d-9183-614597c7f2f7",
      "tenant": "a4342dc8-cd0e-4742-a467-3129c469d0e5"
    }

    ServicePrincipal ID = appId
    ServicePrincipal Secret = password 
```



## Check the expiration date of your service principal

```bash
myResourceGroup=xxx
myAKSCluster=xxx

SP_ID=$(az aks show --resource-group $myResourceGroup --name $myAKSCluster \
    --query servicePrincipalProfile.clientId -o tsv)
az ad sp credential list --id "$SP_ID" --query "[].endDate" -o tsv
```
