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

### Deploying the demo

In order to reproduce this demonstration to your customers, partners, and so forth, you should walk through the following steps:

1) Navigate to the Azure Portal (https://portal.azure.com) and create a new resource group (suggestivelly called "ITMarketplace"). This resource group will host our entire solution. To see how to create a new resource group through the Azure Portal, please, follow up [this link](https://www.juniper.net/documentation/en_US/vsrx/topics/task/multi-task/security-vsrx-azure-marketplace-resource-group.html).

2) Once you have your