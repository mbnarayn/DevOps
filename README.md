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
- Specify a local path to which the files in the Azure Repo will be cloned to (ensure the path points at a specific and dedicated sub folder for the Repo)
- Click on Clone

You can only need complete the steps below if you plan to deploy to Azure directly from Visual Studio. (See When Do You Create a Project or a Solution?)

- Now Click on File - New - Project
- Select Azure Resource Group (C# Azure Cloud) and click Next
- Specify a Project Name
- Specify the location to be the same folder as the local path for the Azure Repo files
- Specify a Solution Name or alternatively select the check box to "Place solution and project in the same directory"
- Click Create and select Blank Template

### Visual Studio 2019 - When Do You Create a Project or a Solution?

You only need to create a Project or a Solution if you plan to deploy to Azure directly from Visual Studio. A Project/Solution is not required if you plan to deploy via Azure Pipelines, you can simply clone a repo and git commit files back into the Repo to deploy via Azure Pipelines.


# ARM Template Deployment Errors

### Get-ChildItem : Cannot find path JSONFileName because it does not exist

If you get this error, select the JSON file under Solution Explorer and then in Properties pane, under Advanced change the Build Action from None to Content. Complete the same action for the paramaters JSON file too.

### 'deploymentName' does not match expected pattern '^[-\w\._\(\)]+$'.

If you get this error, change the JSON file name. I got this error because the JSON file name had spaces which had to be removed.

# Azure Pipeline Deployment Errors

### No hosted parallelism has been purchased or granted. To request a free parallelism grant, please fill out the following form https://aka.ms/azpipelines-parallelism-request

Microsoft has changed the policy to allow the free tier of a hosted agent pools for public and private projects of newly created DevOps organizations by citing the reason that many are abusing this feature by sending a huge amount of traffic on these hosted agents pools. Due to this reason, many are getting the above error during the build pipeline.

Microsoft say that over the past few months, the situation has gotten substantially worse, with a high percentage of new public projects in Azure DevOps being used for crypto mining and other activities we classify as abusive. In addition to taking an increasing amount of energy from the team, this puts our hosted agent pools under stress and degrades the experience of all our users – both open-source and paid.

Microsoft have published a temporary alternative approach which is fill out the form here https://aka.ms/azpipelines-parallelism-request requesting access to free hosted agent pools.

In the meantime you could also use a self hosted agent pool. Details on how to build a self host agent pool are clearly explained on this video https://www.youtube.com/watch?v=a1tWj3ytVSQ.

Once you have deployed a Self Hosted Agent Pool, update your pipelines YAML as described here.

Find the text below on YAML File:
```
pool:
  vmImage: ubuntu-latest
```
And replace with the below, where Default is the name of pool on which you installed the Self Hosted Agent:
```
pool: Default
```




