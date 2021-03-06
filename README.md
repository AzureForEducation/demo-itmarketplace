# Demo - IT Marketplace

## What is this is about?

"IT Marketplace" is an online repository developed by the Americas University's IT team in US and intend to act as a center of environments-ready repository in such way that IT's internal customers (mostly university departments its professionals) would be able to come in and pick up automatically environments for host web applications, environments for dev/test, and so forth by their own.

## Why this demo is so cool?

This demo was developed to give you an idea in how IT departments inside educational institutions can take advantage of Microsoft Azure and Office 365 services to optimize its operations, delivering fast, with high quality without loosing control both of the environment and related costs.

## When you should present this out?

This demo is ideal to be shown in the context of **IT transformation/optimization**. By raising this up, your customer will be able to understand how their IT would be empowered to quickly deliver more with less by using the cloud's power.

## Internal view

To accomplish that, IT's team have developed a simple web solution which is constituted by four main aspects:

1) **Frontend**: A single landing page is written in HTML5 to show the packages available and its description. There's no interaction with a backend so because of this, they can host it in some cheap and straightforward structure, like Storage Websites, CDN, and so forth.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/frontend.PNG" width="700">

2) **Request form**: Because IT's team don't want to spend money with this application and also, because they have already Office 365 available for each user inside the institution, they decide to use O365 Forms service to provide that form whereby users will formally request to IT the spin-up of the environment.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/form.PNG" width="400">


3) **Form & SQL integration**: Once they decided to use Forms as part of this process, they choose to use O365 Flow to send out user's requests to an existing SQL database, to appropriately keep track of that requests.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/flow.PNG" width="400">


4) **Azure ARM Templates**: The environments itself are being packaged using Azure Resource Manager Templates. This way, IT can easily adjust the sizing, capacity and availability rules for each environment being wrapped.

## How it works?

* IT's customer (researcher, marketing professional, teacher, and so forth) do visit the institution's intranet and get access to the webpage where the packaged environments are being shown.

* He/she picks up the environment which best supports his/her needs. By clicking on "Request this environment". So, the webpage redirects the user to the O365 form whereby requests can be made.

* User then fill out the form and send that info to the IT's admin by clicking on "Submit".

* ID's admin is automatically notified by the system about the new request and then, after do some internal validations with the related area, executes out the ARM template who delivers the requested environment on Azure.

* When it is done, IT's administrator sends a mail to the requestor informing connections strings and further info regarding that environment.

This way, the final architecture for that solution would be that one presented by the image below.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-arch.PNG">

## ARM Templates

For this demo we're offering the following packages:

1) **Linux-based Web App with MySQL Server**: When executed, this ARM Template will create on Azure two primary elements: 1 Web App shared with 1.75 GB RAM and 10 GB of local storage; 1 MySQL database with 5 GB of storage. This database will not be dedicated, and the performance levels will be shared between the other databases existing on that server.

2) **Wordpress site with Container Instances**: A ARM templae that creates a storage account, configures a File Share and installs a Wordpress and MySQL into a Azure Container Instance (ACI). Ideal scenario for dev/test.

3) **Minecraft Server on a Ubuntu Virtual Machine**: This template deploys and sets up a customized Minecraft server on an Ubuntu Virtual Machine, with you as the operator. It also deploys a Storage Account, Virtual Network, Public IP addresses and a Network Interface. You can set common Minecraft server properties as parameters at deployment time. Once the deployment is successful you can connect to the DNS address of the VM with a Minecraft launcher. The following Minecraft server configuration parameters can be set at deployment time: Minecraft user name, difficulty, level-name, gamemode, white-list, enable-command-block, spawn-monsters, generate-structures, level-seed.

## How to make this work

### Pre-requisites

To accomplish the steps described in this demo, first you should have already settled:

* A Azure Subscription with enough credits to afford it.
* A Office 365 account with both Forms and Flow services accessible.
* Azure Storage Explorer installed and set up (including your login process). To get that, please, download it [here](https://azure.microsoft.com/en-us/features/storage-explorer/).

### Deploying the demo

In order to reproduce this demonstration to your customers, partners, and so forth, you should walk through the following steps:

1) Navigate to the Azure Portal (https://portal.azure.com) and create a new resource group (suggestivelly called "ITMarketplace"). This resource group will host our entire solution. To see how to create a new resource group through the Azure Portal, please, follow up [this link](https://www.juniper.net/documentation/en_US/vsrx/topics/task/multi-task/security-vsrx-azure-marketplace-resource-group.html).

2) Once you have your resource group set up, you will need to create a new "Storage Account" into it. Please, keep in mind you need to create a storage account using the GPv2 tier. You can follow up [this tutorial](https://docs.microsoft.com/en-us/azure/storage/common/storage-quickstart-create-account?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&tabs=portal#create-a-storage-account-1) to accomplish that.

3) Now, you we will publish the frontend application (the whereby our packaged environments are shown) using a new Storage Account's feature: Static Website. But first, web need to enable the resource. To get there, once in the main blade of Storage Account service, browse out to **"Static Website"** option menu placed in the left. On the right side, click on "Enable". Then, type both the "Index document name" and "Error document path" as below.

    - Index document name: index.html
    - Error document path: error.html

    Click "Save" and that's it. Your storage account configuration meant to be something like the picture below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-enabling-static-website.PNG">

4) Now, let's get the frontend application. Open up a new tab in your browser and then, navigate to "https://github.com/AzureForEducation/demo-itmarketplace" website. Once there, click on green button "Clone or donwload" and then, in "Download ZIP", as you can see throught the image below. Save the zip file and unpack it. We will use it soon.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-donwload-zip.png">

5) Now we're ready to move the frontend application to our storage. To get there, execute the Azure Storage Explorer app in your machine. Under your in use subscription, select the storage account we just created and configured. Expand it out and select the "Blob Containers" option. Once again, expand it down. You should be able to see two itens: "$web" and "$logs". The one which we're interested is "$web" because we're going to move our frontend application to it.

    Just select "Upload files" on Azure Storage Explorer's menu and select all frontend application files to be uploaded, as you can see through the image below.

     <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-uploading-website.png">

    At the end, your $web container should be pretty similar to the one presented by the image below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-frontend-uploaded.PNG" width="300">

    Now, test your frontend application. The url to do this is available on the storage account blade into the Azure Portal. It is similar (not equal) to this: "https://itmarketplacestorage.z22.web.core.windows.net/". The result should be the following.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-frontend-up-running.PNG">

6) Now we need to do some actions (three to exact) in Office 365. First, we need to create the form whereby IT's customers will land their requests regarding the environments. To accomplish that, just navigate to Forms service on O365 console and create a new one with the following fields:

    - **Request date**: date format
    - **Department you belongs to**: options list in dropdown format
    - **Your manager's email**: text format
    - **Template selected**: options list (values: Linux-based Web App with MySQL | Wordpress site with Container Instance (ACI) | Minecraft server on an Ubuntu Virtual Machine) in dropdown format
    - **Purpose iof this environment**: Long text format

    Some additional configurations to that form are necessary to garantee that only authorized people will be able to fullfill it, as you can see below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-form.PNG">

7) Now we need to create two automatizations to conclude the process. To do that, we'll use a very useful service available on O365 (Flow) in partnership with another one available on Azure (SQL Azure Databases). Instead to use spreadsheets to store our users requests, we're going to store that data in a Azure SQL Database so we can safely track everything.

    Considering we have the form already in place, what we need to do next is to create our database in which the data will be stored in on Azure, right? Sugestivelly, I've created a database called "EnvRequests". Please, follow up [this tutorial](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-get-started-portal#create-a-sql-database) to create yours.

    Now you should have the database set up. Its time to create a table inside it who will meet the form structure. To get that, on the Azure Portal, into the SQL Database's blade, on the left side, select the option "Query Editor (Preview)" then authenticate yourself into the server and then, copy, paste and run the the following code.

    ```sql
    CREATE TABLE [dbo].[Requests](
	    [Id] [int] IDENTITY(1,1) NOT NULL,
	    [RequestDate] [varchar](50) NOT NULL,
	    [Department] [varchar](50) NOT NULL,
	    [ManagerEmail] [varchar](250) NOT NULL,
	    [Template] [varchar](250) NOT NULL,
	    [Purpose] [text] NOT NULL,
	    [Nome] [varchar](250) NOT NULL,
	    [Date] [datetime] NOT NULL
    ) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
    GO
    ```

    As result of this operation you should be able to see a new table called "Requests" at the left side of the editor, as you can see through the image below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-database-creation.PNG">

8) Now we have both the form and the storage service to host the information sent through it. Now we need to create the connection between them and here is where O365 Flow is going to help us. We will create an automation to add into SQL database a new record every single time a new answer is sent through our form. Cool!

    - Fortunately all you need to do is import a pre-built package for this operation. This package is available inside the zip package you downloaded and unziped earlier in this tutorial and its name is "FormsSQLServerIntegration".

    - Go to O365 dashboard at Flow area and click at "Import" option, available on the top menu area. 

    - Then, select the "FormsSQLServerIntegration" file and upload it to Flow service.

    - When it finish you will be presented to a screen pretty similar to that one presented by the image below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-import-integration.PNG">

    As you can see, there are 3 steps to be accomplished as follows:

    - In the first option, click in "Create as new". A new window will opened. Just rename it or accept the current one the integration flow and click in "Save".

    - Now, under "Related resources" area you will need to create two connections: one to the form itself and another one to the database. We've created both already so the only thing you need to do is go through each option there and add the configurations requested and, in the end, click in "Import". By doing this, you should have the connection between your Form and SQL Database established.

    - Finally, you can test the integration by using a fake data to it. At the Flow dashboard (inside your integration panel) just click at "Test" option and then, go to the form and fill it out with some fake data. You should be able to see something like the image below in your screen.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-integration-running.PNG">

9) Another integration ahead. Now, the very last thing we need to do is to automatically send a message to the Azure's admin inside the IT informing that we have a new environment request and giving him/her the ability to deploy that environment directly from the email. Once again, Flow is going to help us.

    The process is going to be exactly the same of before's step, meaning that you will import an integration package (NotifyITAzureAdmin) and do some final configurations. After the test, your Azure Admin's inbox should present out a message like that one shown by the image below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-notification-running.PNG">

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-email-notification2.PNG">

    That's it. Hope it helps!