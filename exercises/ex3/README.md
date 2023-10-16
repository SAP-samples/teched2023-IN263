## Exercise 3 - Configure Decision in SAP Build Process Automation: Part 01

In this exercise, you will configure SAP Build Process Automation project where a Decision will be used to determine which business action should be executed for an event. You will also configure a decision table in the decision project.

### 1. Create SAP Build Process Automation Project

1. Open the [SAP Build Process Automation](https://in263-ol7jr9xc.eu10.build.cloud.sap/) Application.

2. In the SAP Build Process Automation Application, In the **Lobby** Tab , Click on **Create** button to create a new project.

    <img src="./images/lobby.png" width="90%" height="100%" />
    <!-- ![plot](./images/lobby.png) -->

3. Choose the **Build an Automated Process Tile**, and then choose **Business Process** Tile.

    <img src="./images/automatedprocess.png" width="90%" height="80%" />
    <!-- ![plot](./images/automatedprocess.png) -->

    <img src="./images/process.png" width="90%" height="80%" />
    <!-- ![plot](./images/process.png) -->

4. Fill the project name as **Events-to-Business-Actions-Framework-xxx** where XXX is the id from your email id and Choose **Create**

    <img src="./images/createproject.png" width="90%" height="90%" />
    <!-- ![plot](./images/createproject.png) -->

    **Accept** the disclaimer if prompted!

    <img src="./images/AcceptDisclaimer.png" width="90%" height="90%" />
    <!-- ![plot](./images/AcceptDisclaimer.png)     -->

5. The Project is now created , click on **Cancel** for the **Create Process** pop-up , as we will be creating **Decisions** and it's related **Data Types** in the next steps.

    <img src="./images/ProjectCreated.png" width="90%" height="100%" />
    <!-- ![plot](./images/ProjectCreated.png) -->


### 2. Configure Decision in SAP Build Process Automation Project

1. Under the **Artifacts** Tab of your project, Click on **Create** and then choose **Decision** .

    <img src="./images/CreateDecision.png" width="90%" height="100%" />
    <!-- ![plot](./images/CreateDecision.png) -->

    Fill in the Decision Name as **E2BDecision** and Click on **Create**.

    <img src="./images/DecisionName.png" width="90%" height="100%" />
    <!-- ![plot](./images/DecisionName.png) -->

    You will see the following screeen as the decision is created successfully.

    <img src="./images/DecisionCreated.png" width="90%" height="100%" />
    <!-- ![plot](./images/DecisionCreated.png)    -->

2. The **Decision** configuration requires the **Input and Ouput parameters** as well as the business **Rule** that maps the incoming event to it's associated business action. To configure the Input/Output parameters we need to create the Custom Data Type with the fields that the incoming event payload contains.

    Under the**Artifacts** Tab, Click on **Create** and choose **Data Types**.

    <img src="./images/CreateDataType.png" width="90%" height="100%" />
    <!-- ![plot](./images/CreateDataType.png) -->

3. We will be creating two data types namely **eventInfo** and **actionInfo** which will have the structure of the incoming event payload and the action Id respectively. To create the datatypes follow the steps shown below:

    a. Create Data Type called **eventInfo**

    <img src="./images/eventInfoDT.png" width="90%" height="100%" />
    <!-- ![plot](./images/eventInfoDT.png) -->

    b. Click on **New Field** and Enter the following three field details and click on **Save**. 

    | Name | Type |
    |------|------|
    | SourceSystem | String |
    | DeviceType |  String |
    | DeviceLocation | String |

    _**Note:**_ Name is case-sensitive.
       
    <img src="./images/eventDTFields.png" width="90%" height="100%" />
    <!-- ![plot](./images/eventDTFields.png) -->

    c. Under the **Artifacts** Tab, Click on **Create** and choose **Data Types**.

    <img src="./images/actionInfoDT.png" width="90%" height="100%" />
    <!-- ![plot](./images/actionInfoDT.png) -->

    d. Create data type called **actionInfo** 

    <img src="./images/actionDTname.png" width="90%" height="100%" />
    <!-- ![plot](./images/actionDTname.png) -->

    **e.** Click on **New Field** and Enter the following field details and click on **Save**. 

    | Name | Type |
    |------|------|
    | ActionId | String |

    _**Note:**_ Name is case-sensitive.

    <img src="./images/actionDTFields.png" width="90%" height="100%" />
    <!-- ![plot](./images/actionDTFields.png) -->

4. As we have now created the required data types , let us go to the **E2BDecision** and configure the Input/Output parameters.    
    - Fill the Input Paramter Name as **EventInfo** and Choose the Type from the drop down as **eventInfo**. 
    - Fill the Output Parameter Name as **ActionInfo** and choose the Type from the drop down as **actionInfo**.

    <img src="./images/addIpOp.png" width="90%" height="100%" />
    <!-- ![plot](./images/addIpOp.png) -->

5. Next let us configure the **Rules**. 

    a. Click on **Add Rule**

    <img src="./images/addRule.png" width="90%" height="100%" />
    <!-- ![plot](./images/addRule.png) -->

    b. Fill in the **Rule Name** as **DecideAction** and click on **Next Step**

    <img src="./images/CreateRule1.png" width="90%" height="90%" />
    <!-- ![plot](./images/CreateRule1.png) -->

    c. To configure the **Conditions** follow the steps shown below in sequence. 

    <img src="./images/CreateRule2.png" width="90%" height="90%" />
    <!-- ![plot](./images/CreateRule2.png) -->

    d. To configure the **Results** follow the steps shown below.

    <img src="./images/CreateRule3.png" width="90%" height="90%" />
    <!-- ![plot](./images/CreateRule3.png) -->

    e. Verify the **Review** Tab 

    <img src="./images/CreateRule4.png" width="90%" height="90%" />
    <!-- ![plot](./images/CreateRule4.png) -->

    f. An empty **Decision Table** will be created.

    <img src="./images/CreateRule5.png" width="90%" height="90%" />
    <!-- ![plot](./images/CreateRule5.png) -->

    g. Fill the fields with following values:

    >- SourceSystem: **='Azure'**,
    >- DeviceType: **='Waste Container v2**',
    >- DeviceLocation: **='Plant A'**

    ActionId to be filled later.

    <img src="./images/RuleField.png" width="90%" height="100%" />
    <!-- ![plot](./images/RuleField.png) -->

### 3. Release and Deploy SAP Build Process Automation Decision

1. To use the decision in our CAP extension application we need to deploy the Decision created. 

    First click on **Release** to release the Decisions. 
    
    <img src="./images/RuleCreated.png" width="90%" height="100%" />
    <!-- ![plot](./images/RuleCreated.png) -->

    Click on **Release**

    <img src="./images/ProjectRelease.png" width="90%" height="100%" />
    <!-- ![plot](./images/ProjectRelease.png) -->

2. Now that the project is released, it is ready for deployment. Click on the **Deploy**

    <img src="./images/Deploy1.png" width="90%" height="100%" />
    <!-- ![plot](./images/Deploy1.png) -->

    Follow the steps shown in the following screenshots.

    <img src="./images/Deploy2.png" width="90%" height="100%" />
    <!-- ![plot](./images/Deploy2.png) -->

    <img src="./images/Deploy3.png" width="90%" height="90%" />
    <!-- ![plot](./images/Deploy3.png) -->

    <img src="./images/Deploy4.png" width="90%" height="100%" />
    <!-- ![plot](./images/Deploy4.png) -->

3. The Project is successfully deployed ! 

    <img src="./images/Deployed.png" width="90%" height="100%" />
    <!-- ![plot](./images/Deployed.png) -->


4. Go to **E2BDecision** , Click on the three dots to **View Details** and Click on **View Details**

    <img src="./images/ViewDetails.png" width="90%" height="100%" />
    <!-- ![plot](./images/ViewDetails.png) -->

    Copy the **Id** from the **Decision Details** and keep a note, which will be used in the Next Step.

    <img src="./images/ViewDetails2.png" width="90%" height="100%" />
    <!-- ![plot](./images/ViewDetails2.png) -->
 

### 4. Congratulations!

Congratulations on completing your Exercise 3! You have successfully configured part of SAP Build Process Automation project for Decision.

Let's Continue to - [Exercise 4 - Configure Business Actions in Events-to-Business-Actions Framework](../ex4/README.md)


