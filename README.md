# Demo - IT Marketplace

"IT Marketplace" is an online repository developed by the Americas University's IT team in US and intend to act as a center of environments-ready repository in such way that IT's internal customers (mostly university departments its professionals) would be able to come in and pick up automatically environments for host web applications, environments for dev/test, and so forth by their own.

To accomplish that, IT's team have developed a simple web solution which is constituted by four main aspects:

1) **Frontend**: A single landing page is written in HTML5 to show the packages available and its description. There's no interaction with a backend so because of this, they can host it in some cheap and straightforward structure, like Storage Websites, CDN, and so forth.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/frontend.PNG" width="700">

2) **Request form**: Because IT's team don't want to spend money with this application and also, because they have already Office 365 available for each user inside the institution, they decide to use O365 Forms service to provide that form whereby users will formally request to IT the spin-up of the environment.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/form.PNG" width="400">


3) **Form & SQL integration**: Once they decided to use Forms as part of this process, they choose to use O365 Flow to send out user's requests to an existing SQL database, to appropriately keep track of that requests.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/flow.PNG" width="400">


4) **Azure ARM Templates**: The environments itself are being packaged using Azure Resource Manager Templates. This way, IT can easily adjust the sizing, capacity and availability rules for each environment being wrapped.

## How it works?

* IT's customer (researcher, marketing professional, teacher, and so forth) do visit the institution's intranet and get access to the webpage where the packaged environments are being showed.

* He/she pick up the environment which best support his/her needs. By clicking in "Request this environment", the webpage redirects the user to the O365 form whereby requests can be made.

* User fill the form out and send that info to the IT's admin.

* ID's admin is automatically notified by the system and then, after do some internal validations with the related area, execute out the ARM template who delivers the requested environment on Azure.

* When it is done, IT's administrator sends a mail to the requestor informing connections strings and further data regarding that environment.

This way, the final architecture for that solution would be that one presented by the image below.

<img src="https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/demo-itmarketplace-arch.PNG">