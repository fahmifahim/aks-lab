## Create new service principal

```bash
az ad sp create-for-rbac --role Contributor

    Result sample: 
    {
      "appId": "xxxxx-b1f3-443d-874c-fd83c7c739c5",
      "name": "xxxxx-b1f3-443d-874c-fd83c7c739c",
      "password": "xxxxxx-9186-426d-9183-614597c7f2f7",
      "tenant": "xxxxxx-cd0e-4742-a467-3129c469d0e5"
    }

    ServicePrincipal ID = appId
    ServicePrincipal Secret = password 

SP_ID=xxxxx-b1f3-443d-874c-fd83c7c739c5
```

## Check the expiration date of your service principal

```bash
az ad sp credential list --id $SP_ID
    [
        {
        "additionalProperties": null,
        "customKeyIdentifier": "rbac",
        "endDate": "2023-02-16T22:16:06.397318+00:00",
        "keyId": "xxxxx-7b93-441a-bcf1-a2960c56299c",
        "startDate": "2022-02-16T22:16:06.397318+00:00",
        "value": null
        }
    ]
```



### Node auto scaling

Check node autoscaling enabled/disabled

```bash
az aks nodepool show --cluster-name [AKS-CLUSTERNAME] --name [AKS-NODEPOOL-NAME] --resource-group [AKS-RG-NAME] | grep enableAutoScaling
    "enableAutoScaling": false,
```