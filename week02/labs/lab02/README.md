# Lab 02 - [Azure - App Service Using ARM Template](https://learn.microsoft.com/en-us/azure/app-service/quickstart-arm-template)

1. Login to your A Cloud Guru account
1. Click the "Playground" icon at the top of the page
1. Click the "Start Azure Sandbox" button
1. Login to the Azure Sandbox using the provided instructions and credentials
1. Review the ARM template at `https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/quickstarts/microsoft.web/app-service-docs-linux/azuredeploy.json`
1. Open CloudShell in the Azure portal
1. When prompted, click "Bash"
1. Leave "No storage account required" selected, select the only available subscription from the dropdown, and click "Apply"
1. In the CloudShell, configure environment variables as follows (**NOTE:** Normal shortcut keys for copy/paste will not work in CloudShell; use right-click):

```
export RESOURCE_GROUP=$(az group list --query [0].name --output tsv)
export LOCATION=$(az group list --query [0].location --output tsv)
```

10. Use the following to deploy the infrastructure via the ARM template; replace the "app-name" placeholder with a unique name of your choosing (e.g., initials-year-month-day):

```
az deployment group create --resource-group $RESOURCE_GROUP --parameters webAppName="<app-name>" linuxFxVersion="PYTHON|3.9" \
--template-uri "https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/quickstarts/microsoft.web/app-service-docs-linux/azuredeploy.json"
```

11. Close "CloudShell"
11. Search for and launch "App Services"; you may need to click "Refresh" to get your new App Service to show up
11. Click the provided link for your newly created App Service
11. On the "Overview" tab, find and copy the link for your site ("Default domain")
11. Open that link in a new tab to view your deployed site (**NOTE:** It may take a few minutes for the site to complete its initial spinup)
