### Role of Microsoft Azure IoT Central    
>
>**Azure IoT Central is a fully managed Internet of Things (IoT) platform provided by Microsoft. It simplifies the process of creating, deploying, and managing IoT solutions. Designed for businesses and organizations, IoT Central allows users to connect, monitor, and control their IoT devices securely and at scale.**     
>
>You can find more information about Microsft Azure IoT Central [here](https://azure.microsoft.com/en-in/products/iot-central).

### Setting up Microsoft Azure IoT Central    
- We've configured a Microsoft Azure IoT Central application within our Azure subscription. You can access the application by logging in with the provided credentials here: [Systems annd Credentials](../ex0/README.md/#systems-annd-credentials)
- If you're interested in setting it up or trying it out within your own Microsoft Azure subscription, you can refer to the instructions provided on this page for detailed steps: [Set Up Microsoft Azure IoT Central](./SetUp_Azure_IoT.md)

### 3. Create a new device template in IoT Central application

1. Select the created IoT Central Application to view the details. Choose the created IoT Central Application URL to open the application.

    ![plot](./images/created-app.png)

2. Select the IoT Central Application URL to open the application.

    Your application should have two devices added for the device template type **Connected Waste Bin** as shown in the screenshot.

    ![plot](./images/iot-app.png)

3. In this scenario, you will create a new device template based on your custom capabilities. Choose **Device templates** and then select **New**. In the **Select type** > **Create a custom device template**, select **IoT Device** to create a custom device template.

4. Choose **Next:Customize** to create a new device template.

    ![plot](./images/newdevice-template1.png)

5. In the **Device template name** field, enter **Waste Container v2**. Choose **Next: Review**.

   ![plot](./images/newdevice-template2.png)

6. Review and choose **Create**. 

   ![plot](./images/newdevice-template3.png)

7. Choose the created device template and choose **Import a model** to import model file.

    ![plot](./images/import-template.png)

    **Note**: **Container-Data.json** file is available in [devicetemplate](./devicetemplate/) folder. Upload this model file.

    ![plot](./images/model-imported.png)

8. Choose **Views** and the choose **Editing device and cloud data** to add a test view.

    ![plot](./images/addview.png)

9. Select the fields as per your requirement. For a sample view, you can choose **Container ID**, **Container Type**, **Location ID** and **Status** fields and choose **Save**.

    ![plot](./images/addview1.png)

10. Choose **Publish**.

    ![plot](./images/publish.png)

11. Choose **Devices** and then choose **+ New** to create a new device. 

    ![plot](./images/newdevice.png)

12. In the **Device Template** dropdown menu, choose the device template you created and then choose **Create**.

    ![plot](./images/newdevice1.png)


### 4. Configure Data Export

1. Choose **Data export** and then choose **+ New Data Export** to create new Data export.

    ![plot](./images/iot-dataexport.png)

2. Enter **Waste Container Export** as value. 

    In the **Type of data to export** dropdown menu, select **Telemetry** and then choose **+Message property filter**.

    ![plot](./images/dataexport-new.png)

3. In the **Export the data if** dropdown menu, select **all of the conditions are true**. You can configure this as per your requirement.

4. In the **Name** field, enter **Device template** as value.

5. In the **Operator** dropdown menu, select **Equals** and in the **Value**, enter **Waste Container v2**.

    ![plot](./images/dataexport-new1.png)

6. Choose **+Filter**.

    ![plot](./images/dataexport-new2.png)

    Enter the details as shown in the below screen shot.

    ![plot](./images/dataexport-new3.png)

    
7. In the **Enrichments** section, choose **+Custom String** and enter the below key value pairs as shown below.

    ![plot](./images/enrichment-custom.png)

8. Choose **+Property** and enter the below key value pairs as shown below.

    ![plot](./images/enrichment-property.png)

9. Choose **Save**.
