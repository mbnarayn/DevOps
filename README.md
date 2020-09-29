# Store ARM Templates in Azure Repos and Deploy via Visual Studio 2019

This method allows you to store ARM templates in an Azure Repo and deploy directly to Azure using Visual Studio 2019. Both the ARM templates as well as the entire Visual Studio project folder will be synced to Azure Repos using Git. The steps below will need to followed in Azure DevOps and Visual Studio to make this work.

### Azure DevOps 

- Create a new Azure DevOps Organisation in Azure DevOps if you don't already have one
- Create a new project in the Azure DevOps Organisation if you don't already have one
- Create a new Git Repo within the project via Azure Repos if you don't already have one
- Copy the HTTPS Clone URL for the Repo

### Visual Studio 2019

- Open Visual Studio 2019
- Under Get Started, click on Clone or check out code
- Paste the HTTPS Clone URL in to the Repository location
- Specify a local path to which the files in the Azure Repo will be cloned to
- Click on Clone
- Now Click on File - New - Project
- Select Azure Resource Group (C# Azure Cloud) and click Next
- Specify a Project Name
- Specify the location to be the same folder as the local path for the Azure Repo files
- Specify a Solution Name or alternatively select the check box to "Place solution and project in the same directory"
- Click Create and select Blank Template

# ARM Template Deployment Errors

### Get-ChildItem : Cannot find path JSONFileName because it does not exist

If you get this error, select the JSON file under Solution Explorer and then in Properties pane, under Advanced change the Build Action from None to Content. Complete the same action for the paramaters JSON file too.

### 'deploymentName' does not match expected pattern '^[-\w\._\(\)]+$'.

If you get this error, change the JSON file name. I got this error because the JSON file name had spaces which had to be removed.
