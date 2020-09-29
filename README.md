# Store ARM Templates in Azure Repos and Deploy via Visual Studio 2019

This method allows you to store ARM templates in an Azure Repo and deploy directly to Azure using Visual Studio 2019. Both the ARM templates as well as the entire Visual Studio project folder will be synced to Azure Repos using Git.

### Steps to Follow in Azure DevOps 

- Create a new Azure DevOps Organisation in Azure DevOps if you don't already have one
- Create a new project in the Azure DevOps Organisation if you don't already have one
- Create a new Git Repo within the project via Azure Repos if you don't already have one
- Copy the HTTPS Clone URL for the Repo

### Steps to Follow in Visual Studio 2019

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


