## SAP Integration Suite, Advanced Event Mesh Configuration

 1. To access the SAP Integration Suite, Advanced Event Mesh, navigate to **Services** > and choose **Instances and Subscriptions**.
    Choose the row for the SAP Integration Suite, Advanced Event Mesh subscription and choose **Go to Application**

    ![plot](./images/access-aem.png)

2. Choose **Cluster Manager** in the SAP Integration Suite, Advanced Event Mesh Application. 

    ![plot](./images/aem-application.png)



4. Click on the created service **TechEd-IN263**

    ![plot](./images/aem-1.png)

    Click on the **connect** tab and expand the **REST** tile to get the messaging connectivity information.

    ![plot](./images/aem-2.png)

5. Configuring a **REST Delivery Point**
     Next, you must configure a queue and a REST delivery point on Message VPN.

     **a.** Click on **Open Broker Manager**.

     ![plot](./images/open-broker-manager.png)

     **b.** The **Broker Manager** application loads. The next step is to create a queue, on the left pane click on **Queues**  

     ![plot](./images/aem-3.png)

     You will see the following screen, Click on **Queues** to create a new queue.

     ![plot](./images/aem-4.png)

     Click on **+Queue** 

     ![plot](./images/aem-5.png)

     **c.** Create a Queue by name **Q-IN263-XXX**

     ![plot](./images/aem-6.png)

     Enable both incoming and outgoing configuration and Click on **Apply**

     ![plot](./images/aem-7.png)    

     Queue successfully created, now Click on the Queue. 

     ![plot](./images/aem-8.png)    

     **d.** Add a **Topic Subscription** to the queue.

     Click on the **Subscriptions** Tab.

     ![plot](./images/aem-9.png)

     Then click on **+ Subscription** to add a topic.

     ![plot](./images/aem-10.png)

     In the **Create Subscription** screen, type in the topic name as **IN263-XXX/messages** and click **Create**

     ![plot](./images/aem-11.png)    

     Topic Subscription successfully created. 

     ![plot](./images/aem-12.png)

     **e.** Create a **REST Delivery Point** object

     On the left pane click on **Clients** and then Navigate to **REST** tab.

     ![plot](./images/aem-13.png)
    
     ![plot](./images/aem-14.png)

     Click on ** + REST Delivery Point** 

     ![plot](./images/aem-15.png)

     Fill the **RDP Name** as **IN263-RDP-XXX**
    
     ![plot](./images/aem-16.png)
    
     Configure the REST Delivery Point and Click on **Apply**

     ![plot](./images/aem-17.png)  

     REST Delivery Point successfully created
     
     ![plot](./images/aem-18.png)  

     **f.**  Create a Queue Binding object

     Create a queue binding to the queue you created previously. This will tell the RDP where to fetch messages from. **Note:** that REST Delivery Points (RDPs) can be bound to multiple queues.

     Click on the **IN263-RDP-XXX** created in the previous step. Click on **Queue Bindings** Tab.

     ![plot](./images/aem-19.png)

     Click on **+ Queue Binding**

     ![plot](./images/aem-20.png)

     Choose the queue created reviously from the drop down - **Q-IN263-XXX**

     ![plot](./images/aem-21.png)

     Click on **Create**

     ![plot](./images/aem-22.png)

     Set the POST target where the requests would be sent - **/api/events** and then Choose **Apply**

     ![plot](./images/aem-23.png)

     **Note:** that the RDP is down - it will automatically start up when a REST consumer makes a connection to the RDP.

     ![plot](./images/aem-24.png)

     **g.** Create a **REST Consumer** object.

     Navigate to **REST Consumers** Tab and click on **+ REST Conusmer**

     ![plot](./images/aem-25.png)

     Fill in the **REST Consumer Name** as **IN263-RC-XXX** and choose **Create**

     ![plot](./images/aem-26.png)

     Enable the **REST Consumer** and set HOST:PORT details of the message HTTP listener. 

     To Fill the **Host** , Navigate to the Cloud Foundary Space where the application is deployed.

     ![plot](./images/aem-27.png)

     Click on **action-management-srv**.

     ![plot](./images/aem-28.png)

     Copy the link under **Application Routes**,. **Note:** Strip the **https://** before pasting the value in the **Host** field

     ![plot](./images/aem-29.png)

     Fill in the Value of **Port** as **443**

     Select **POST** as the **HTTP Method**.

     Enable the TLS.

     Keep **Outgoing Connection Count** value as **1**.

     Fill the **Max Response Wait Time (sec)** as **30**

     Populate **Connection Retry Delay (sec)** field with **300**

     From the drop down menu, choose **OAuth 2.0 Client Credentials** as the **Authentication Scheme**.

     Next, Go to your **BTP subaccount** ,Navigate to **Services** > **Instances** and under the **Instances** select **action-management-auth**.

     ![plot](./images/aem-30.png)

     Under the **Service Keys** the key named **action-management-auth-key** is already created. Click on the **View** Option to get the **OAuth 2.0 Client Credentials**.  

     ![plot](./images/aem-31.png)

     Copy the **clientid**, **clientsecret** and **url**. Navigate back to the **REST Consumer** configuration and paste the values for **Client ID** and **Client Secret**. Paste the **url** copied earlier in the **Token Endpoint URL** and appened **/oauth/token** at the end of the **url**. 
     Effective **Token Endpoint URL** is **url/oauth/token**.

     Fill the remaining fields as shown in the screenshot below and click on **Apply**.

     ![plot](./images/aem-33.png)  

     REST Consumer successfully created

     ![plot](./images/aem-34.png)  

     A final, configured **RDP settings** would look like this.

     ![plot](./images/aem-35.png)