---
layout: post
title: "Azure Key Vault Part 1"
categories: daily
excerpt: ""
tags:
  - daily
  - software development
  - azure
  - azure key vault
  - c#
  - code
image:
  feature:
date: 2016-10-22T20:01:17-06:00
modified: 2016-10-22T20:01:17-06:00
---

# Azure Key Vault Part 1

Over the last few weeks I have been learning a pretty cool new feature / product in azure. It is called Key Vault. Key vault is essentially a cloud hsm (place that you do encryption and decryption) and a store for your keys and secrets. (I.E. Certificates and things like database passwords or other connection values.) There are several low hanging fruit advantages to this. For us this allowed us to move our tenant configuration information from a sql database to more secure place. I will go into more depth of what we used it for in a subseqent post. This post will cover setting up an azure key vault instance in the new portal (Yeah! No PowerShell required!)

### Let's Get Started

#### Set up the Key Vault

- The first step is to log in to your azure account (The new portal!).
- Click the Plus button on the left of the menu.

![alt image](http://i.imgur.com/rq7sRA3.png)

- Search for Key Vault

![alt image](http://i.imgur.com/lMqc7xS.png)

- Select Azure Key Vault a click Create. (I tend to suffix all of my azure resources names with the type of resource it is, e.g. Jacksonjahyes-keyVault.)

![alt image](http://i.imgur.com/EoUUBga.png)

- Once the Key Vault has been created, use the search bar at the top and search the name you created.

![alt image](http://i.imgur.com/ctwsBFc.png)

#### Add the Secrets

- One the main page of the key vault instance, click on secrets.

![alt image](http://i.imgur.com/dw8LbGq.png)

- For a text based secret do the following:
  - Fill out the name
  - This will be part of the url for the secret
  - Enter your secret value.
    - Example: We stored a json object with tenant configuration which we serialized on application start and used it to set up or api instance.

![alt image](http://i.imgur.com/n9RWi4G.png)
- Your azure user is automatically given access.
- In the next step we will setup access to azure web apps.

![alt image](http://i.imgur.com/1ZbtvEj.png)

- If you click into one of the versions of the secret you can see the URL.


Secrets can be updated by creating a new version. The new version will become the default version. The root url for the secret will give you the default version.

https://ctg-dev-key-vault.vault.azure.net/secrets/tenant-list/ <-- default version
Vs.
https://ctg-dev-key-vault.vault.azure.net/secrets/tenant-list/fei3223920d9s0d9032329  <--specific version

If you want clients to always get the most up to date version they should save the root url and hit that address when requesting the secret. If they want a specific version always, obviously store the address to the specific version.

#### Allow Azure Applications to Access Key Vault


- On the left click the Azure Active Directory Button

![alt image](http://i.imgur.com/1ZbtvEj.png)

- This should bring up the Default Azure Active Directory for the Azure Subscription you are using.
- It is important that the
	- Your Portal Login is added to this Azure Active Directory as an Account Co-Admin or Service Account Admin
		- If this is done incorrectly, you will not be able to give applications access to keys and secrets
	- Your App Registrations are created in this same AAD.
		- Your application will not be able to be given access to the key vault keys and secrets

Add an application to active directory:

![alt image](http://i.imgur.com/2esoiqF.png)


On the top click Add

![alt image](http://i.imgur.com/OWgbskc.png)


- In the box that appears on the right:
  - Create a name for the application such as jacksonjhayes-website
  - Insert the URL of the application that is being created (example: http://jacksonjhayes.azurewebsites.net)
- Repeat these steps for all allowed applications.

##### Note:

The names and urls are mostly symbolic as you could distribute the applicationid and secrets to anyone. But this was it is easy to manage what applications have access to what keys and secrets. It is NOT recommended that one AAD app registration be shared by multiple applications. Especially if they are applications outside of Azure. The beauty of Azure Key the credentials to access the keys and secrets never has to leave azure. If your live account doesn't get comprised, neither do the secrets. (No promises, but you know what I mean. Nothing is ever absolutely secure. And you should plan for such scenarios.)

#### Enable an Applications in Key Vault

Navigate to your key vault and click "Access Policies" under "Monitoring



Click Add new
After a moment a list of your applications will be displayed as well as live accounts that are registered with the subscription default active directory.
If the desired applications do not appear then your applications were added to the wrong active directory.

Click the application you want to grant access to and click "Select"


Click Key Permissions, Click All, Select All and Press Ok
Click Secret Permissions, Click All, Press Ok
Press Ok at the bottom and your application will be granted access

Repeat these steps for every application you want to have access to the key vault.

### More More more
I will do a follow up post on how to use the keys in an application in a later post. 
