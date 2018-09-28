# Create a WordPress site on a Container Instance

Create a WordPress site (and its MySQL database) on a Container Instance

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzureForEducation%2Fdemo-itmarketplace%2Fmaster%2Ftemplates%2Fpackage2-aci-wordpress%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

This template creates a WordPress website and its MySQL database on a Container Instance. The WordPress site content and MySQL database are persistently stored on an Azure Storage File Share.

## Solution overview and deployed resources

The following resources are deployed as part of the solution

+ **Azure Container Instance**: Azure Container Instance to host the WordPress site and the MySQL database.
+ **Azure Container Instance**: A [run-once](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-restart-policy#container-restart-policy) Azure Container Instance, where the az-cli is executed to create the file shares
+ **Storage Account**: Storage account for the file shares to store the WordPress site content and MySQL database
+ **File share**: Azure File shares to store WordPress site content and MySQL database.