# url-shortener

## Infrastructure as Code

### Download Azure CLI
https://docs.microsoft.com/en-us/cli/azure/install-azure-cli


### Log in into Azure

```bash
az login
```

### Create Resource Group

```bash
az group create --name urlshortener-dev --location westeurope
```

### Look through the plan of resources creation

```bash
az deployment group what-if --resource-group urlshortener-dev --template-file infrastructure/main.bicep
```

### Create Resources

```bash
az deployment group create --resource-group urlshortener-dev --template-file infrastructure/main.bicep
```

### Create user for GitHub Actions

```bash
az ad sp create-for-rbac \
        --name "GitHub-Actions-SP" \
        --role contributor \
        --scopes /subscriptions/c48358f1-a13c-45eb-950e-be826e18b3b8 \
        --sdk-auth
```

### Configure a federated identity credential on an app
