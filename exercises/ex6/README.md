## Exercise 6 - Set up Device, Rule and Destination in Azure IoT Central    
In this exercise, your objective is to generate a Device Template and a simulated Device that produces an event every minute. This exercise also involves setting up a Data Export with filters for your device, and sending these events to the SAP Integration Suite's Advanced Event Mesh for additional processing.

### 1. Role of Microsoft Azure IoT Central    
>
>**Azure IoT Central is a fully managed Internet of Things (IoT) platform provided by Microsoft. It simplifies the process of creating, deploying, and managing IoT solutions. Designed for businesses and organizations, IoT Central allows users to connect, monitor, and control their IoT devices securely and at scale.**     
>You can find more information about Microsft Azure IoT Central [here](https://azure.microsoft.com/en-in/products/iot-central).

### 2. Access Microsoft Azure IoT Central

- We've configured a [Microsoft Azure IoT Central](https://industry-40.azureiotcentral.com/)application within our Azure subscription. You can access the application by logging in with the provided credentials here:

| Systems | Credentials |
|---------|-------------|
| **[Microsoft Azure IoT Central](https://industry-40.azureiotcentral.com/)** | **Email:** IN263-XXX@teched2023outlook.onmicrosoft.com <br> _replace XXX with the number on your laptop_ |

### 3. Create a new Device of template "Waste Container v2"

1. Choose **Devices** and then choose **+ New** to create a new device. 

    <img src="./images/newdevice00.jpg" width="90%" height="90%" />
    <!-- ![plot](./images/newdevice.png) -->

2. Fill the **Device name** as WC IN263-XXX , where XXX is the id in your email id. **Device ID** is auto-populated. In the **Device Template** dropdown menu, choose the device template named **Waste Container v2**. Set the **Simulate this device** toggle to **yes**  and then choose **Create**.

    <img src="./images/newdevice01.jpg" width="90%" height="90%" />

3. Once your device is created, Under the **Form** tab, configure the following values:
    ```
    Container ID: Container-IN263-XXX
    Location Id: Plant A
    Status: Working
    ```
    Your configuration should like as shown below, and then **Save**

    <img src="./images/newdevice02.jpg" width="90%" height="90%" />

4. As we have enabled simulation, the device now simulates real-time IoT device events, you can see the generated events under **Raw Data** tab.
5. 
    <img src="./images/newdevice03.jpg" width="90%" height="90%" />



### 4. Configure Data Export

During this step, you'll initially establish a Destination, outlining the connection specifics for the Advanced Event Mesh. Afterward, you'll configure a Data Export to transmit event information when the device's Fill Level drops below 30.

1. Choose **Data export**, navigate to **Destinations** and then choose **New destination**

    <img src="./images/data-export00.jpg" width="90%" height="90%" />

2. Enter following values:
    - **Name: DEST-AEM-IN263-XXX** where XXX is the id from your email id.
    - **Destination type: Webhook**
    - **Callback URL: https://{Username}:{Password}@{Secured Rest HOST}/{Topic Subscription}** where Username, Password, Secured Rest HOST, Topic Subscription are noted in exercise 2. **Note:** remove the https:// from the Secured Rest HOST before pasting. Then choose **Save**.

    <img src="./images/data-export01.jpg" width="90%" height="90%" />
       


3. Choose **Data export** and then choose **+ New Data Export** to create new Data export.

    <img src="./images/data-export02.jpg" width="90%" height="90%" />

4. Enter **EXPORT-IN263-XXX** as value where XXX is your id from email. 
   - Disable the Data export by switiching of the status 
   - In the **Type of data to export** dropdown menu, select **Telemetry** and then choose **+Filter**. 

    <img src="./images/data-export03.jpg" width="90%" height="90%" />

6. In the **Export the data if** dropdown menu, select **all of the conditions are true**. Add following filters as shown in following image:
    - **Name:** Device Template **Operator:**:Equals **Value:** Waste Container v2
    - **Name:** Filling Level **Operator:** is less than **Value**: 30
    - **Name:** Waste Container / Status **Operator:** Equals **Value**: Working  
    - **Name:** Device name **Operator:** Equals **Value**: WC-IN263-XXX, replace XXX with the id from your email (device name that you created in step 2 of Part 4)
   
    <img src="./images/data-export04.jpg" width="90%" height="90%" />

    <!-- ![plot](./images/dataexport-new.png) -->

7.  In the **Enrichments** section, choose **+Custom String** and enter the below key value pairs as shown below.
    - Application: **Industry-40**
    - System: **Azure**     
    <img src="./images/data-export05.jpg" width="90%" height="90%" />

8. In the **Enrichments** section, choose **+Property** and enter the below key value pairs as shown below.
    - ContainerID: **Waste Container v2 / Container ID**
    - DeviceName: **Device name**
    - DeviceTemplate: **Device template name**
    - Location: **Waste Container v2 / Location Id**     
    <img src="./images/data-export06.jpg" width="90%" height="90%" />

9. In the **Destinations** section, choose **+Destination** 

    <img src="./images/data-export07.jpg" width="90%" height="90%" />       

    Then select the detination created earlier in step 2 of part 4 and choose **Save**. 
    <img src="./images/data-export08.jpg" width="90%" height="90%" />    


### 5. Congratulations!

Congratulations on completing your Exercise 6! You have successfully created Device Template, Device and Data export with destination to send event to SAP Inetrgation Suite, Advanced Event Mesh. 

Let's Continue to - [Exercise 7 - Execute the End-to-End Scenario](../ex7/README.md)
