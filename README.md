# Store ARM Templates in Azure Repos and Deploy via Visual Studio 2019

Create a new Azure DevOps Organisation in Azure DevOps if you don't already have one
Create a new project in the Azure DevOps Organisation if you don't already have one
Create a new Git Repo within the project via Azure Repos if you don't already have one
Copy the HTTPS Clone URL for the Repo

Open Visual Studio 2019
Under Get Started, click on Clone or check out code
Paste the HTTPS Clone URL in to the Repository location
Specify a local path to which the files in the Azure Repo will be cloned to
Click on Clone
Now Click on File - New - Project
Select Azure Resource Group (C# Azure Cloud) and click Next
Specify a Project Name
Specify the location to be the same folder as the local path for the Azure Repo files
Specify a Solution Name or alternatively select the check box to "Place solution and project in the same directory"
Click Create and select Blank Template



## High Level Components

The high level components that make up Windows Virtual Desktop are a Tenant Group, Tenant, Host Pool and App Groups.

- Tenant Group - When you create a tenant in Windows Virtual Desktop it is associated by default to a Tenant Group called "Default Tenant Group". While the New-RdsTenantGroup PowerShell cmdlet appears to make it possible to create multiple Tenant Groups, there is no documentation or use cases available from Microsoft regarding the creation of multiple tenant groups so it is better to leave this as is for now and operate from the Default Tenant Group. Management access and end user permissions can be configured via controls available at the Tenant and Application Group levels.

- Tenant - Creating a tenant in Windows Virtual Desktop is the first step toward building your desktop virtualization solution. A tenant is a group of one or more host pools. With a tenant, you can build out host pools, create app groups, assign users, and make connections through the service. 
