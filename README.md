https://blog.johnnyreilly.com/2021/12/19/azure-container-apps-bicep-and-github-actions

List Azure regions
`az account list-locations -o table`

Setup up a resource group in *East US*
`az group create -g rg-aca -l eastus`

Deploy bicep infra with Azure CLI
```
az deployment group create \
  --resource-group rg-aca \
  --template-file ./infra/main.bicep \
  --parameters \
    name='container-app'
```

Get azure subscription id
`az account show`

```
az ad sp create-for-rbac --name "myApp" --role contributor \
    --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group} \
    --sdk-auth
```

Delete everything from demo
`az group delete --name re-aca`