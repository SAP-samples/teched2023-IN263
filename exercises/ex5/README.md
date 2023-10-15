## Exercise 5 - Configure Decision in Build Process Automation: Part 02

In this exercise, you will update decision created in Exercise 3 - Configure Decision in SAP Build Process Automation: Part 01 with action id details and activate the project.

### 1. Update Decision Table 

1. In the SAP BTP Cockpit, Navigate to your subaccount -> **Sevices** -> **Instances and Subscriptions** , Open the SAP Build Process Automation Application.

    ![plot](./images/subscriptions.png)

2. In the SAP Build Process Automation Application, In the **Lobby** Tab , Click on **Events-to-Business-Actions-Framework** project.

    ![plot](./images/lobby.png)

3. Choose the **E2BDecision** , On the **Rules** Tab, Click the **DecideAction** Decision table.

    ![plot](./images/E2BDecision.png)

4. Click on the **ActionId** Field. 

    ![plot](./images/FillActionId.png)

    Paste the ActionId of the Action Created in Step-7.  

    ![plot](./images/ActionId.png)

5. The Decision is now configured with the Business Rule successfully. To use the decision in our CAP extension application we need to deploy all the latest changes in the Decision. 

    First click on **Release** to release the Decisions. 
    
    ![plot](./images/RuleCreated.png)

    Click on **Release**

    ![plot](./images/ProjectRelease.png)

6. Now that the project is released, it is ready for deployment. Click on the **Deploy**

    ![plot](./images/Deploy1.png)

    Follow the steps shown in the following screenshots.

    ![plot](./images/Deploy2.png)

    ![plot](./images/Deploy3.png)

    ![plot](./images/Deploy4.png)

7. The Project is successfully Redeployed ! 

    ![plot](./images/Deployed.png)

### 3. Congratulations!

Congratulations on completing your Exercise 5! You have successfully updated the decision table with action id details in SAP Build Process Automation.

Let's Continue to - [Exercise 6 - Set up Device, Rule and Destination in Azure IoT Central](../ex6/README.md)

