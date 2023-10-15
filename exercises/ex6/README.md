## Exercise 6 - Set up Device, Rule and Destination in Azure IoT Central    
In this exeercis, your objective is to generate a Device Template and a simulated Device that produces an event every minute. This exercise also involves setting up a Data Export with filters for your device, and sending these events to the SAP Integration Suite's Advanced Event Mesh for additional processing.

### 1. Role of Microsoft Azure IoT Central    
>
>**Azure IoT Central is a fully managed Internet of Things (IoT) platform provided by Microsoft. It simplifies the process of creating, deploying, and managing IoT solutions. Designed for businesses and organizations, IoT Central allows users to connect, monitor, and control their IoT devices securely and at scale.**     
>You can find more information about Microsft Azure IoT Central [here](https://azure.microsoft.com/en-in/products/iot-central).

### 2. Setting up Microsoft Azure IoT Central      
- We've configured a Microsoft Azure IoT Central application within our Azure subscription. You can access the application by logging in with the provided credentials here: [Systems annd Credentials](../ex0/README.md/#systems-annd-credentials)
- If you're interested in setting it up or trying it out within your own Microsoft Azure subscription, you can refer to the instructions provided on this page for detailed steps: [Set Up Microsoft Azure IoT Central](./SetUp_Azure_IoT.md)

### 3. Create a new Device Template  - "Waste Container v2"

1. Open IoT Central Application using the ceredentials provided here: [Industry 4.0 Microsoft Azure IoT Central](../ex0/README.md/#systems-annd-credentials).

    <img src="./images/MSAzureIoTCentralHome.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/MSAzureIoTCentralHome.jpg) -->

2. In this scenario, you will create a new device template based on your custom capabilities. Open **Extend Side Navigation** and Choose **Device templates** 

    <img src="./images/newdevice-template0.jpg" width="80%" height="80%" />

3. Select **New** to create a new device template. 

    <img src="./images/newdevice-template00.jpg" width="80%" height="80%" />

4. In the **Select type** > **Create a custom device template**, select **IoT Device** to create a custom device template. Choose **Next:Customize**.

    <img src="./images/newdevice-template1.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/newdevice-template1.png) -->

5. In the **Device template name** field, enter **Waste Container v2**. Choose **Next: Review**.

   <img src="./images/newdevice-template2.jpg" width="80%" height="80%" />
   <!-- ![plot](./images/newdevice-template2.png) -->

6. Review and choose **Create**. 

   <img src="./images/newdevice-template3.jpg" width="80%" height="80%" />
   <!-- ![plot](./images/newdevice-template3.png) -->

7. Choose **Import a model** to import model file.

    <img src="./images/import-template1.jpg" width="80%" height="80%" />
    <img src="./images/import-template0.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/import-template.png) -->

    **Note**: **Container-Data.json** file is available in [devicetemplate](./devicetemplate/) folder. Upload this model file.

    <img src="./images/model-imported.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/model-imported.png) -->

8. Choose **Views** and the choose **Editing device and cloud data** to add a test view.

    <img src="./images/addview.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/addview.png) -->

9. Select the fields as per your requirement. For a sample view, you can choose **Container ID**, **Container Type**, **Location ID** and **Status** fields and choose **Save**.

    <img src="./images/addview1.jpg" width="80%" height="80%" />
    <img src="./images/addview2.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/addview1.png) -->

10. Choose **Publish**.

    <img src="./images/publish.jpg" width="80%" height="80%" />
    <img src="./images/publish1.jpg" width="80%" height="80%" />
    <img src="./images/publish2.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/publish.png) -->

### 4. Create a new Device of template "Waste Container v2"

1. Choose **Devices** and then choose **+ New** to create a new device. 

    <img src="./images/newdevice00.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/newdevice.png) -->

2. In the **Device Template** dropdown menu, choose the device template you created and then choose **Create**.

    <img src="./images/newdevice01.jpg" width="80%" height="80%" />
    <img src="./images/newdevice02.jpg" width="80%" height="80%" />
    <img src="./images/newdevice03.jpg" width="80%" height="80%" />
    <!-- ![plot](./images/newdevice1.png) -->


### 5. Configure Data Export

During this step, you'll initially establish a Destination, outlining the connection specifics for the Advanced Event Mesh. Afterward, you'll configure a Data Export to transmit event information when the device's Fill Level drops below 30.

1. Choose **Data export**, navigate to **Destinations** and then choose **New destination**

    <img src="./images/data-export00.jpg" width="80%" height="80%" />

2. Enter following values:
    - **Name: DEST-AEM-IN263-XXX** where XXX is the id from your email id.
    - **Destination type: Webhook**
    - **Callback URL: https://{Username}:{Password}@{Secured Rest HOST}/{Topic Subscription}** where Username, Password, Secured Rest HOST, Topic Subscription are noted in exercise 2.     
    <img src="./images/data-export01.jpg" width="80%" height="80%" />     
    Then choose **Save**.

3. Choose **Data export** and then choose **+ New Data Export** to create new Data export.

    <img src="./images/data-export02.jpg" width="80%" height="80%" />

4. Enter **EXPORT-IN263-XXX** as value where XXX is your id from email. 
   - Disable the Data export by switiching of the status 
   - In the **Type of data to export** dropdown menu, select **Telemetry** and then choose **+Filter**. 

    <img src="./images/data-export03.jpg" width="80%" height="80%" />

5. In the **Export the data if** dropdown menu, select **all of the conditions are true**. Add following filters as shown in following image:
    - Device Template = Waste Container v2
    - Filling Level LT 30
    - Waste Container / Status = Working    
    <img src="./images/data-export04.jpg" width="80%" height="80%" />

    <!-- ![plot](./images/dataexport-new.png) -->

6.  In the **Enrichments** section, choose **+Custom String** and enter the below key value pairs as shown below.
    - Application: Industry-40
    - DeviceName: Azure     
    <img src="./images/data-export05.jpg" width="80%" height="80%" />

7. In the **Enrichments** section, choose **+Property** and enter the below key value pairs as shown below.
    - ContainerID: Waste Container v2 / Container ID
    - System: Device name
    - DeviceTemplate: Device template name
    - Location: Waste Container v2 / Location Id     
    <img src="./images/data-export06.jpg" width="80%" height="80%" />

8. In the **Destinations** section, choose **+Destination** 

    <img src="./images/data-export07.jpg" width="80%" height="80%" />       

    Then select the detination created earlier in step 2 of part 5 and choose **Save**. 
    <img src="./images/data-export08.jpg" width="80%" height="80%" />    


### 6. Congratulations!

Congratulations on completing your Exercise 6! You have successfully created Device Template, Device and Data export with destination to send event to SAP Inetrgation Suite, Advanced Event Mesh. 

Let's Continue to - [Exercise 7 - Execute the End-to-End Scenario](../ex7/README.md)