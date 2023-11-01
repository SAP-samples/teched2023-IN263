## Exercise 2 - Configure SAP Integration Suite, Advanced Event Mesh 

In this exercise, you will create REST Delivery Point, Queue, Topic Subscriptions, REST Consumer etc in SAP Integration Suite, Advanced Event Mesh. You can find the [SAP Integration Suite, Advanced Event Mesh](https://eu10.console.pubsub.em.services.cloud.sap/login?tenant-id=0e652f06-6ee7-48d1-8877-b84274456b22) details here: 

| Systems | Credentials |
|---------|-------------|
| **[SAP Integration Suite, Advanced Event Mesh](https://eu10.console.pubsub.em.services.cloud.sap/login?tenant-id=0e652f06-6ee7-48d1-8877-b84274456b22)** | **Email:** IN263-XXX@education.cloud.sap <br> _replace XXX with the number on your laptop_ |

### 1. Discover SAP Integration Suite, Advanced Event Mesh

### 2. Get REST Connection details
1. Open the [SAP Integration Suite, Advanced Event Mesh](https://eu10.console.pubsub.em.services.cloud.sap/login?tenant-id=0e652f06-6ee7-48d1-8877-b84274456b22) application.

2. Navigate to **Cluster Manager** . 

    <img src="./images/aem-application.png" width="90%" height="90%" />   

    <!-- ![plot](./images/-application.png) -->

3. Unselect **Only show my services** option and then choose **TechEd-IN263**.

    <img src="./images/aem-0.jpg" width="90%" height="90%" />  


4. The following screen will be displayed.

    <img src="./images/aem-1.png" width="90%" height="90%" />     
    <!-- ![plot](./images/aem-1.png) -->

    Click on the **connect** tab, expand the **REST** tile and then keep a note of messaging connectivity information like **Username, Password, Secured REST Host**.

    <img src="./images/aem-2.png" width="90%" height="90%" />       
    <!-- ![plot](./images/aem-2.png) -->

### 3. Configure Topic subscription

1. Click on **Open Broker Manager**.

    <img src="./images/open-broker-manager.png" width="90%" height="90%" /> 
    <!-- ![plot](./images/open-broker-manager.png) -->

2. The **Broker Manager** application loads. The next step is to create a topic subscription for the queue, on the left pane click on **Queues**  

    <img src="./images/aem-4.png" width="90%" height="90%" /> 
    <!-- ![plot](./images/aem-4.png) -->

3. You will see the following screen, the queues are already created. Search the queue **Q-IN263-XXX** where XXX is the id from your email id.
   
    <img src="./images/aem-5.png" width="90%" height="90%" /> 
    <!-- ![plot](./images/aem-5.png) -->

7. Now Click on the Queue. 

    <img src="./images/aem-8.png" width="90%" height="90%" /> 
    <!-- ![plot](./images/aem-8.png)     -->

8. Add a **Topic Subscription** to the queue. Click on the **Subscriptions** Tab.

    <img src="./images/aem-9.png" width="90%" height="90%" /> 
    <!-- ![plot](./images/aem-9.png) -->

9. Then click on **+ Subscription** to add a topic.

    <img src="./images/aem-10.png" width="90%" height="90%" /> 
    <!-- ![plot](./images/aem-10.png) -->

10. In the **Create Subscription** screen, type in the topic name as **IN263-XXX/messages** where XXX is the id from your email id and click **Create**

    <img src="./images/aem-11.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-11.png)     -->

    Topic Subscription successfully created.  

    <img src="./images/aem-12.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-12.png)    -->

### 4. Configure Queue Binding.

1. On the left pane click on **Clients** and then Navigate to **REST** tab.
    
    <img src="./images/aem-14.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-14.png) -->

2. **REST Delivery Point** are already created. Search for the RDP named **IN263-RDP-XXX** where XXX is the id from your email id. **Note:** select Show 100 to view all the RDPs.

    <img src="./images/aem-15.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-15.png) -->

4. Create a Queue Binding to your queue. This indicates the RDP where to fetch messages from.    
    Click on the REST Delivery Point **IN263-RDP-XXX** . Navigate to **Queue Bindings** Tab.

    <img src="./images/aem-19.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-19.png) -->

5. Click on **+ Queue Binding** to create queue binding.

    <img src="./images/aem-20.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-20.png) -->

6. Choose the queue created previously from the drop down - **Q-IN263-XXX** where XXX is the id from your email id

    <img src="./images/aem-21.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-21.png) -->

    Click on **Create**

    <img src="./images/aem-22.png" width="90%" height="90%" />
     <!-- ![plot](./images/aem-22.png) -->

7. Set the POST request target to **/api/events** This is the end point to which events will be forwarded which is nothing but extension application of Events-to-Business-Actions framework.
    Then Choose **Apply**

    <img src="./images/aem-23.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-23.png) -->

    **Note:** that the RDP is down - it will automatically start up when a REST consumer makes a connection to the RDP.

    <img src="./images/aem-24.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-24.png) -->

8. Create a **REST Consumer** object. Navigate to **REST Consumers** Tab and click on **+ REST Conusmer**

    <img src="./images/aem-25.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-25.png) -->

    Fill in the **REST Consumer Name** as **IN263-RC-XXX** where XXX is the id from your email id and choose **Create**

    <img src="./images/aem-26.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-26.png) -->

9. To get the **Host** , Navigate to the [SAP BTP Subaccount](https://emea.cockpit.btp.cloud.sap/cockpit/?idp=tdct3ched1.accounts.ondemand.com#/globalaccount/e2a835b0-3011-4c79-818a-d7767c4627cd/subaccount/0e652f06-6ee7-48d1-8877-b84274456b22) and then to Cloud Foundary Space where the application is deployed.

    <img src="./images/aem-27.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-27.png) -->

10. Click on **action-management-srv** application which will open application details.

    <img src="./images/aem-28.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-28.png) -->

    Copy the link under **Application Routes**,. (**Note:** Remove the **https://** from the URL while copying).

    <img src="./images/aem-29.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-29.png) -->

    Then paste it in HOST field on Edit REST Consumer configuration page.

11. Fill in the following Value

    | Field | Value |
    |------|------|
    | Enabled  | Enable toggle |
    | Port | 443 |
    | HTTP Method |  POST |
    | TLS | Enable toggle |
    | Outgoing Connection Count | 1 |
    | Max Response Wait Time (sec) | 30 |
    | Connection Retry Delay (sec) | 300 |
    | Authentication Scheme | OAuth 2.0 Client Credentials |
    | Client Id | `clientid`|
    | Client Secret | `clientsecret`|
    | Token Endpoint URL | `url`/oauth/token |
    | Token Exipry Default |900 |
    | Scope | uaa.resource |

    Follow the steps below to fetch the value of Client Id, Client Secret and Token Endpoint URL


12. Go back to the [SAP BTP Subaccount](https://emea.cockpit.btp.cloud.sap/cockpit/?idp=tdct3ched1.accounts.ondemand.com#/globalaccount/e2a835b0-3011-4c79-818a-d7767c4627cd/subaccount/0e652f06-6ee7-48d1-8877-b84274456b22) 
    and then to Cloud Foundary Space. Navigate to **Services** > **Instances** and under the **Instances** select **action-management-auth**. 

    <img src="./images/aem-30.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-30.png) -->

    Under the **Service Keys** the key named **action-management-auth-key** is already created. Click on the **View** Option to get the **OAuth 2.0 Client Credentials**.  

    <img src="./images/aem-31.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-31.png) -->

13. Copy the **clientid**, **clientsecret** and **url** and paste it on the **REST Consumer** configuration as below:
    - Client ID : ```clientid```
    - Client Secret: ```clientsecret```
    - Token Endpoint URL: ```url```/oauth/token 

    <img src="./images/aem-32.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-32.png) -->

    Make sure to follow step 9 to 13 carefully and Fill the remaining fields as shown in the screenshot below. Then choose **Apply**.

    <img src="./images/aem-33.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-33.png)   -->

    REST Consumer successfully created

    <img src="./images/aem-34.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-34.png)   -->

    A final, configured **RDP settings** would look like this.

    <img src="./images/aem-35.png" width="90%" height="90%" />
    <!-- ![plot](./images/aem-35.png) -->

### 5. Congratulations!

Congratulations on completing your Exercise 2! You have successfully configured REST Delivery Point, Queue, Topic Subscriptions, REST Consumer etc in SAP Integration Suite, Advanced Event Mesh.

Let's Continue to - [Exercise 3 - Configure Decision in Build Process Automation: Part 01](../ex3/README.md)
