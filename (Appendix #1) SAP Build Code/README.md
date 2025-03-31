# SAP BTP - Hands-On Enblements Day - SAP Build Code Overview

## Description

This repository contains the material for the SLB: SAP BTP  Hands-On Enablement Day (21.02.2025).

## Overview

Introduction to SAP Build Code and how it accelerates app development with the incorporated sevices from SAP Business Technology Platform (BTP). Highlights on on key features and benefits for SAP partners and customers.
Wihin the current tutorial we will setup your SAP BTP subaccount and SAP Build Code with all the needed entitlements and permissions so that you can proceed with the actual CAP development.
![](./images/build-01.png)

## Prerequisites

To complete the exercices in this repository, please make sure that you meet the following prerequisites:

* You have an [SAP Business Technology Platform (BTP) Trial Account](https://developers.sap.com/tutorials/hcp-create-trial-account.html).


## Create your first BTP Subaccount in your BTP Trial account

Create your first subaccount in “US East (VA) – AWS” region and click on “Create Account” button. 

<img src="./images/build-02.png" width="700" height="400">



You will see a that the process of creating your resources in your SAP BTP Trial account had started. 

![](./images/build-03.png)


Once completed you will see the SAP BTP Cockpit welcome page. Click on “Go To Tour Trial Account” 
![](./images/build-04.png)


You will be redirected to your Global Account Explorer view where you also will be able to find the subaccount you just have created.

## Provision “SAP Build Code”

We’ll setup SAP Build Code using a booster. To do so, from the Global Account Explorer view, click on Boosters menu item, followed by choosing to start the booster “Get Started with SAP Build Code” (see screenshot below). 
![](./images/build-05.png)


Once the booster gets loaded, click on the “Start” button. 
![](./images/build-06.png)


You can monitor booster’s progress at the progress popup displayed: 

![](./images/build-07.png)


Once it is complete, click on “Navigate to Subaccount” which will direct you to the subaccount you had created. 

![](./images/build-08.png)


Congratulations – you had landed to your first subaccount in SAP BTP. 
![](./images/build-09.png)


## Create a CF Space 
Take a look in your subaccount. In case there is no space created, please proceed with this step. 
You will need to create a space on your CF Environment. To do so, at the subaccount overview page, just click on “Create Space” button: 

![](./images/build-10.png)


Type `dev` as a space name and click “Create” :

![](./images/build-11.png)

## HANA Cloud dependencies for your CAP app 
### Provision HANA Cloud, plan "tools" 

Before proceeding with the CAP application, you will need to provision few dependencies in your subaccount related to HANA Cloud. That’s needed as your CAP app will be using HANA Cloud as DB. 

To do so, go to “Instances and Subscriptions” and click on “Create” button. 
![](./images/build-12.png)

 

Within the popup screen “New Instance or Subscription”, look for: 
-	Service: `SAP HANA Cloud` 
-	Plan: `tools`

![](./images/build-13.png)



Once the process completes, you shall be able to see the subscription provisioned: 
![](./images/build-14.png)


Remember this step, you will repeat the same step along the way of setting up your subaccount with the needed resources for your development purposes. 

### Provision HANA Cloud, plan "hana" 
As a next, click over again at the “Instances and Subscriptions” menu and click on “Create” button. Within the Popup, look for 
-	Service: `SAP HANA Cloud`
-	Plan: `hana` 
See the screenshot for further reference and click on the button “Next” 
![](./images/build-15.png)


Within the parameters section, please add input for “systempassword” and click “Next” button: 
![](./images/build-16.png)


Review the inputs provided and click on “Create” 

![](./images/build-17.png)


The process of provisioning HANA Cloud will take a while. To save time for our tutorial, you could proceed with another step and come back to HANA 

![](./images/build-18.png)


### Configure your HANA Cloud instance 

At this point your hana instance previously created in your **Trial** subaccount should be up and running. For the MTA Deployment Service to deploy the app and initialize the db schemas and data, the hana instance must be configured properly. First add required hana permissions.

In your **Trial** subaccount in the SAP BTP cockpit, choose **Security** and **Users**.

Choose the arrow **>** next to your user entry.
![](./images/build-19.png)


In the **Role Collections** overview of your user entry, click on **Assign Role Collection** or, if the button is not visible, click the three dots (**...**) and choose **Assign Role Collection**.

<img src="./images/build-20.png" width="400" height="400">



Check the boxes for **SAP Hana Cloud Administrator**, **SAP Hana Cloud Security Administrator** and **SAP Hana Cloud Viewer**, then click **Assign Role Collection**.

Navigate to **Instances and Subscriptions** and click the **SAP Hana Cloud** instance to open **Hana Cloud Central**.

![](./images/build-21.png)



In **Hana Cloud Central** you should see running SAP Hana instance. Click **Manage Configuration**:

![](./images/build-22.png)

In the Manage Configuration view scroll down to **Allowed Connections** and set **Allow all IP addresses**. This setting will allow you to initialize the SAP HANA Cloud instance once deployment is started by Cloud Transport Management Service.

![](./images/build-23.png)


 **Apply your changes with a restart** and **save the changes**.
![](./images/build-24.png)


## Setting up Managed Application Router provided by SAP Build Work Zone, standard edition


Another dependency to you CAP app is the SAP managed app router provided by SAP Build Work Zone, standard edition. You will need it to serve the front-end of your CAP app. 

To initiate such a router in your subaccount, click on the “Instances and Subscriptions” main menu item within your subaccount, followed by the “Create” button. 
![](./images/build-25.png)


Provision a subscription of SAP Build Work Zone, standard edition and click the “Create” button. 

![](./images/build-26.png)




## Assigning role collections to your user on subaccount level

By this moment you should have these subscriptions and services available in your subaccount: 
![](./images/build-27.png)



Before proceeding with the development, make sure you have all the needed permissions. To do so, in your subaccount in the SAP BTP cockpit, choose **Security** and **Users**.

Choose the arrow **>** next to your user entry.
![](./images/build-28.png)



In the **Role Collections** overview of your user entry, click on **Assign Role Collection** or, if the button is not visible, click the three dots (**...**) and choose **Assign Role Collection**.

<img src="./images/build-29.png" width="400" height="400">


Check all the boxes and save the configuration. 

## Summary
Now you are all set to proceed with the next steps , please see [Cloud App Development with SAP Business Application Studio](https://github.com/bisinho/Enablement-Day-Guides/tree/main/2%20-%20Cloud%20App%20Development%20with%20SAP%20Business%20Application%20Studio)



