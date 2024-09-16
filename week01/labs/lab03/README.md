# Lab 03 - [Azure - Function App in Azure Portal](https://learn.acloud.guru/handson/137df37d-a233-42ba-b63b-15d81e1a057f)

1. For this lab, instead of using the provided lab environment, we're going to use a Playground (to give us a little more time to complete the work)
1. Login to your A Cloud Guru account
1. Click the "Playground" icon at the top of the page
1. Click the "Start Azure Sandbox" button
1. Login to the Azure Sandbox using the provided instructions and credentials
1. Follow along with the step-by-step instructions provided in the "Guide" tab for the lab
1. When creating the new Azure Function App and you are presented with the "Select a hosting option" screen, select "App Service"
1. On the "Overiew" tab for the Function App, click the "Create with VS Code Desktop" button and follow along with the provided instructions to deploy function code for testing
    - Create a new folder in your local file system using `mkdir -p azure-func-demo`
    - Navigate to that folder using `cd azure-func-demo`
    - Execute `code .` in that folder to launch Visual Studio Code
    - Under "Extensions" in VS Code, search for and install the "Azure Functions" extension
    - Use `Ctrl + Shift + P` (or `Cmd + Shift + P` on a Mac) to bring up the VS Code command palette
    - Search for and select "Azure Functions: Create New Project..."
    - Select the current folder, use C# for the language, use ".NET 8.0 LTS" for runtime, select "HTTP Trigger", and give the function the name "HttpTrigger"
    - For namespace, use `ACG.AzureDemo`
    - For access, choose "Function"
    - With the "Azure Resources" extension installed, login to the ACG sandbox through VS Code using the ACG-provided credentials
    - Navigate to the Function App in the tree view, right-click the Function App, and choose "Deploy to Function App..."
    - Navigate back to the Azure portal, refresh the Function App view, drill down into the function details, and run a test
