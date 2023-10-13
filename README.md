[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/teched2023-IN263)](https://api.reuse.software/info/github.com/SAP-samples/teched2023-IN263)

# IN263 - Support Industry 4.0 with Event-Driven Architecture  

## Description

This repository contains the material for the SAP TechEd 2023 session called IN263 - Support Industry 4.0 with Event-Driven Architecture.

## Overview

This session introduces attendees to a event-driven Industry 4.0 business scenario where they will implement Events-to-Business-Actions framework built on SAP BTP to integrate real time events generated from Microsoft Azure IoT Central into SAP Business Processes to enrich the outcome of enterprise operations and facilitate rapid decision making. This Events-to-Business-Actions framework can be used in combination with any hyperscaler or telco IoT.

## Business Process Flow

In this event-driven scenario, based on the real-time status of the IoT Devices , actionable events are sent to SAP BTP to decide on the critical business actions to be taken in the SAP Enteprise Business systems based on business rules defined in the system.

![plot](./exercises/ex0/images/businessprocess.png)

a.  Data from industrial IoT Devices are sent to Microsoft Azure IoT Central.   
b.  Rules in Microsoft Azure IoT identifies any event which needs attention and forwards it to SAP Integration Suite Advanced Event Mesh.
c.  SAP Integration Suite, Advanced Event Mesh receives the events and triggers webhook to send the events to extension application of Events-to-Business-Actions framework running on SAP BTP.
d.  Extension application of Events-To-Business-Actions framework is configured with all necessary actions to be taken.    
    -  (Default Action) Calling SAP Build Process Automation - Decision capability API to determine which business action to be taken   
    -  (Main Action) execute the business action OData API call to trigger business process in ERP systems   
    -  (Pre Action) call api to get master data required for business action api (Main Action)   
    -  (Post Action) After business action is executed, call Azure IoT device api to update it's status.   
   Extension application executes the business actions and any pre or post actions.

In today's hand-on session, Based on the fill level of waste container/silo a new Purchase Order Requisition is created in SAP S/4HANA.
   -   Simulate a Waste Container device in Azure IoT Central which constantly generates events.
   -   Set up a rule which identifies when waste container is close to filled and forwards the event to SAP IAdvanced Event Mesh uisng detinations in Azure I0T Central.
   -   Advanced Event Mesh triggers the webhook to forward the event to Events-to-Business-Actions framework.
   -   Events-to-Business-Actions-Framework will first identify that a Purchase Requisition needs to be created in SAP S/4 HANA using Decision from SAP Build Process Automation and then creates a Purchase Requisition in SAP S/4 HANA system. Once purchase requisitionn is created, it also update the Waste Container device status on Azure IoT Central.

## Exercises

Provide the exercise content here directly in README.md using [markdown](https://guides.github.com/features/mastering-markdown/) and linking to the specific exercise pages, below is an example.

- [Getting Started](exercises/ex0/)
- [Exercise 1 - Build and Deploy Events-to-Business-Actions Framework](exercises/ex1/)
- [Exercise 2 - Configure Advanced Event Mesh](exercises/ex2/)
- [Exercise 3 - Configure Decision in Build Process Automation: Part 01](exercises/ex3/)
- [Exercise 4 - Configure Business Actions in Events-to-Business-Actions Framework](exercises/ex4/)
- [Exercise 5 - Configure Decision in Build Process Automation: Part 02](exercises/ex5/)
- [Exercise 6 - Set up Device, Rule and Destination in Azure IoT Central](exercises/ex6/)
- [Exercise 7 - Test end to end Scenario](exercises/ex7/)

**To Be Updated**


  
**OR** Link to the Tutorial Navigator for example...

Start the exercises [here](https://developers.sap.com/tutorials/abap-environment-trial-onboarding.html).

**IMPORTANT**

Your repo must contain the .reuse and LICENSES folder and the License section below. DO NOT REMOVE the section or folders/files. Also, remove all unused template assets(images, folders, etc) from the exercises folder. 

## Contributing
Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct
Please read the [SAP Open Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (c) 2023 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
