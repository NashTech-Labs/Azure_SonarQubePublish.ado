# Azure_SonarQubePublish.ado
Use this template to Publish SonarQube's Quality Gate result on the Azure DevOps build result, to be used after the actual analysis.

## Parameters:

The pipeline requires the following parameters to be defined:


| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | :-------------: | :-------------: | ------------- | :-------------: | ------------- |
| pollingTimeoutSec | Timeout (s)| string | '300' | | Required | This task will poll SonarQube until the analysis is completed, or until the timeout is reached. It also add a build property with the quality gate status of the current build(s) analyses. |
--------------------------------------------------------------------------------------------------------------------------------------------------

These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

 ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_SonarQubePublish.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Azure_SonarQubePublish.yml
    parameters:
      pollingTimeoutSec: '${{parameters.pollingTimeoutSec}}' . 
  ```
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.
