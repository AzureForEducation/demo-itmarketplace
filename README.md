# Demo - IT Marketplace

"IT Marketplace" is an online repository developed by the Americas University's IT team in US and intend to act as a center of environments-ready repository in such way that IT's internal customers (mostly university departments its professionals) would be able to come in and pick up automatically environments for host web applications, environments for dev/test, and so forth by their own.

To accomplish that, IT's team have developed a simple web solution which is constituted by four main aspects:

1) **Frontend**: A single landing page is written in HTML5 to show the packages available and its description. There's no interaction with a backend so because of this, they can host it in some cheap and straightforward structure, like Storage Websites, CDN, and so forth.

![Frontend view](https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/frontend.PNG width=100)

2) **Request form**: Because IT's team don't want to spend money with this application and also, because they have already Office 365 available for each user inside the institution, they decide to use O365 Forms service to provide that form whereby users will formally request to IT the spin-up of the environment.

![Request form view](https://raw.githubusercontent.com/AzureForEducation/demo-itmarketplace/master/doc/images/form.PNG)

3) **Form & SQL integration**: Once they decided to use Forms as part of this process, they choose to use O365 Flow to send out user's requests to an existing SQL database, to appropriately keep track of that requests.

4) **Azure ARM Templates**: The environments itself are being packaged using Azure Resource Manager Templates. This way, IT can easily adjust the sizing, capacity and availability rules for each environment being wrapped.