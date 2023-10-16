## Exercise 1 - Build and Deploy Events-to-Business-Actions Framework on SAP BTP 

In this exercise, you will clone the codebase and deploy the Events-to-Business-Actions Framework on SAP BTP using SAP Business Application Studio. You can find the SAP BTP account and SAP Business Application Studio details here: [Systems and Credentials](../ex0/README.md/#4-systems-annd-credentials)

### 1. Discover Events-to-Business-Actions Framework

>**The Events-to-Business Actions Framework implements an event-driven architecture which enables integration of SAP and non-SAP systems which can be source for events to SAP business systems like SAP S/4HANA, SAP Customer Experience or SAP Asset Performance Management etc.**

<img src="./images/framework.png" width="75%" height="90%" />  
    
<br>

**Understanding the framework**

The framework is developed using SAP Cloud Application Programming (CAP) Model and Node.js. It has primarily 3 components.
1. **Modeler**
    - Using the Modeler UI, you can configure the business actions that need to be triggered in the Business systems (Ex: Creation of Purchase Order Requisition in SAP S/4HANA, Service Ticket in SAP Service Cloud etc.) based on the incoming event. Modeler UI is built using SAP Fiori elements and provides the following tiles to configure action types, actions, and monitor the business action execution logs.
    - “Manage action” tile can be used to configure the business actions. It is integrated with SAP Destination Service so that you can select the required destination configured for SAP business system to add the endpoint and the payload that is needed to create the business action.
    - The modeler supports defining and chaining actions based on the context flow as depicted in below figure .
        - “Default action” is used by the processor to determine which main action needs to be triggered for an incoming event. Only one default action can be defined in modeler.
        - “Main action” is the action that can be used to create a transaction in the business system (Purchase Order Requisition, Service Tickets etc.).
        - “Pre-actions” are actions that are like supporting actions that are executed before the “Main Action” so that you can use the output parameters from them while creating “Main-Action”.
        - “Post-actions” are actions that are executed after the “Main Action” is successfully executed that you can use to trigger further business processes or notify any users/systems of the Business action creation.    
        <img src="./images/actionslogicflow.png" width="75%" height="90%" />  

2. **Processor**
    - Processor is the backend module that receives the from SAP Inetrgation Suite, Advanced Event Mesh topic and executes the corresponding business actions in the SAP S/4HANA system.
    - The processor executes the following steps once it receives an event:
        - Processes ‘Default Action’ to determine which business actions (Main Action) needs to be processed.
        - Fetches the respective business action definition and the associated pre/post actions.
        - Executes the defined pre-actions one by one and then executes the main business action. The processor replaces the respective dynamic values from the event/pre-actions before executing the main action.
        - Once the main action is successfully created, it executes the post-actions that are defined for this main action.

3. **Monitor**
    - Monitor application is used to monitor the status of the business actions and check the logs for troubleshooting.
    - You can drill down to the individual action execution to find out the respective logs and can be used for troubleshooting any failed execution.

For more details about the framework, you can refer the blog here: [Explore “Events-To-Business Actions” Framework](https://blogs.sap.com/2023/02/01/part-2-explore-events-to-business-actions-framework/)


Access the [Event To Action Framework](https://github.com/SAP-samples/btp-events-to-business-actions-framework) GitHub repository to download the project.

### 2. Check the Prerequisites for Deployment

Ensure you have added the required entitlements as described in section **Step1-Set-Up** page before deployment.

### 3. Deploy the Extension Application

Build and deploy the application. Run the following commands:

**Note**: Ensure you have Cloud MBT Build Tool. Refer [The Cloud MTA Build Tool (MBT)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2b99f19e9264c4d9ae9221b22f6f589/1412120094534a23b1a894bc498c2767.html) for more details.

1. Open the SAP Business Application Studio and follow the steps below:

    ![plot](./images/BAS_1.png)

    ![plot](./images/BAS_2.png)

    ![plot](./images/BAS_3.png)

    Click on **Clone from Git** and copy the Git Clone url of this github repo and paste it.

    ![plot](./images/BAS_4.png)

    ![plot](./images/BAS_5.png)

    ![plot](./images/BAS_6.png)

    Navigate to **action-management** directory. To do so, right click on **action-management** folder and choose **Open in integrated terminal**. Your terminal will be as shown below. 

    ![plot](./images/BAS_8.png)

    Fetch the dependencies.

        ```
        npm install
        ```
    Build action-management modules.

        ```
        npm run build
        ```
    Log in to your subaccount in SAP BTP to deploy the extension application. For this follow the below step. 

    ![plot](./images/BAS_9.png)

    ![plot](./images/BAS_10.png)

    ![plot](./images/BAS_11.png)

    ![plot](./images/BAS_12.png)

    ![plot](./images/BAS_13.png)

    ![plot](./images/BAS_14.png)

    ![plot](./images/BAS_15.png)

    ![plot](./images/BAS_16.png)

    Push the application to your subaccount.

    ```
    npm run deploy
    ```

    ![plot](./images/BAS_17.png)



2. You can also check the status of your applications in the SAP BTP cockpit. Copy the value of the extension application URL.

    ![plot](./images/SAPBTPCockpit.png)

3. In the SAP BTP cockpit, navigate to your subaccount and choose **Services** > **Instances and Subscriptions**. Check if you have all of the instances created post deployment as shown below. Make sure the status of all of the instances are **Created**.

    ![plot](./images/postdeploy.png)

### 4. Congratulations!

Congratulations on completing your Exercise 1! You have successfully deployed the Events-to-Business-Actions Framework on SAP BTP.

Let's Continue to - [Exercise 2 - Configure SAP Integration Suite, Advanced Event Mesh](../ex2/README.md)