# Sitecore XDB Single Environment

Visualize: 
[Infrastructure](http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FSitecore%2Fsitecore-azure-quickstart-templates%2Fmaster%2FSitecore%209.0.0%2Fxdbsingle%2Fnested%2Finfrastructure.json),
[Application deployment](http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FSitecore%2Fsitecore-azure-quickstart-templates%2Fmaster%2FSitecore%209.0.0%2Fxdbsingle%2Fnested%2Fapplication.json)

This template creates a Sitecore XDB Single Environment using a minimal set of Azure resources while still ensuring Sitecore Experience Database will run. 
It is best practice to use this configuration for development and testing rather than production environments.

Resources provisioned:

  * Azure SQL databases : core, master, web, reporting, pools, tasks, refdata, smm, shard0, shard1, ma
  * Sitecore roles: Processing, Reporting as a single WebApp instance
  	* Hosting plans: single hosting plan
	  * Preconfigured Web Application, based on the provided WebDeploy package
  * XConnect services: Search, Collection, Reference data, Marketing Automation, Marketing Automation Reporting as a single WebApp instance
	  * Hosting plans: single hosting plan	
	  * Preconfigured Web Application, based on the provided WebDeploy package
  * Azure Search Service
  * Application Insights for diagnostics and monitoring

## Parameters

The **deploymentId** and **licenseXml** parameters in azuredeploy.parameters.json are to be filled in by the PowerShell script using **Name** and **LicenseXmlPath** parameters respectively.

|Parameter                                  | Description
--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------
| location                                  | The geographical region of the current deployment.
| sitecoreAdminPassword                     | The new password for the Sitecore **admin** account.
| sqlServerLogin                            | The name of the administrator account for Azure SQL server that will be created.
| sqlServerPassword                         | The password for the administrator account for Azure SQL server.
| singleMsDeployPackageUrl                  | The HTTP(s) URL to a Sitecore XDB Single Web Deploy package.
| xcSingleMsDeployPackageUrl                | The HTTP(s) URL to a XConnect Single Web Deploy package.
| authCertificateBlob                       | A Base64-encoded blob of the authentication certificate in PKCS #12 format.
| authCertificatePassword                   | A password to the authentication certificate.

> **Note:**
> * The **searchServiceLocation** parameter can be added to the `azuredeploy.parameters.json`
> to specify geographical region to deploy Azure Search Service. Default value is the resource
> group location.
> * The **applicationInsightsLocation** parameter can be added to the`azuredeploy.parameters.json`
> to specify geographical region to deploy Application Insights. Default value is **East US**.