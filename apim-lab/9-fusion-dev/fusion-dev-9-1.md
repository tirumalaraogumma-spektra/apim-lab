# Exercise 9: Fusion Dev (Optional)

### Estimated Duration: 30 Minutes

## Overview

In this exercise, you will create a Power Apps Canvas application that uses an Excel worksheet as the primary data source and integrates with the Star Wars API via a custom connector exported from Azure API Management. This application will allow users to view and search for information about Star Wars characters.

## Objectives

In this exercise, you will perform:

- Task 1: Power Apps and APIM
- Task 2: View your custom connector in Power Platform
- Task 3: Generate the Star Wars Fan Club Application
- Task 4: Add the Star Wars API Data Source

### Task 1: Power Apps and APIM

The *premier* Star Wars Fan club is growing and the club officers would like to upgrade from their existing member tracking worksheet to a mobile application that would be available to their members all over the world. The members would also like to see information about their favorite Star Wars movies and characters in the application that would update as new shows and movies are released.

In this exercise, you will be using [Star Wars API](https://swapi.dev/) with the Azure API Management instance that you created [in part three](../3-adding-apis/adding-apis-3-1-from-scratch.md) of this lab. The Excel worksheet of member profiles will serve as the primary backing data source and will be used to generate a base application. You will export the Star Wars API from Azure API Management as a Power Platform Custom Connector so that the Canvas App can access real-time Star Wars character information. 

> *Note: This exercise requires access to Power Apps Premium connectors. Sign up for a [free Developer Plan](https://powerapps.microsoft.com/en-us/developerplan/).* Use the credentials given in the lab environment to sign up for a Developer Plan.

#### Task 1.1: Update CORS policy

In this task, you will update the CORS policy in your Azure API Management instance to allow requests from Power Apps.

1. IN your Azure API management instance, navigate to API section. 
 
1. Click on **All APIs (1)**, and click on **edit icon (2)** from the Inbound Processing tab.

   ![](media/aaa1a.png)

1. Click on **+ Add Allowed origin (1)** and add **`https://flow.microsoft.com` and `https://make.powerapps.com` (2)** as allowed origins, and click on **Save (3)**.

   ![](media/E9T1.1S3-1901.png)

#### Task 1.2: Create a custom connector

1. Navigate to the following link: [Power Platform](https://www.microsoft.com/en-us/power-platform/products/power-apps/free) in a new browser tab.

1. Click on **Start Free**.

   ![](media/mapi100.png)

1. Select your mail: <inject key="AzureAdUserEmail"></inject> and check the Agreement checkbox **(2)**, then click on **Start free (3)**.

   ![](media/p22t1.2p3.png)

1. On the Welcome to Power Apps page, select the country/region and click on **Get started**.

   ![](media/p22t1.2p4.png)

1. Navigate back to your API management service, from the left pane, click on **Power platform (1)** present under APIs section and click on **Create connector (2)**.

   ![](media/E8T1.2S5-0309.png)

   >**Note:** If you see **Activate account** button, then click on it to activate your Power Platform account and then click on **Create connector**.

1. On the **Create a Connector** page, enter the following details:

   - API : Select the **Star Wars (1)** API.
   - Power Platform Environment: From the dropdown select **ODL_User <inject key="DeploymentID" enableCopy="false"/>'s Environment (2)**.
   - API display name: **Star Wars API (3)**.
   - Click on **Create (4)**.

        ![](media/p22t1.2p6.png)

### Task 2: View your custom connector in Power Platform

In this task, you will view and edit the custom connector that you created in the previous task in Power Platform.

1. Once the connector is created, go to [https://make.powerapps.com](https://make.powerapps.com/) and sign in.

1. Select **More (1)** from the left pane, and click on **Discover all (2)** to see your generated custom connector to your Azure API Management API.
   
   ![](media/more.png)

1. Scroll down and select **Custom connectors**.

   ![](media/p22t2p3.png)

1. On the Custom connectors page, click on **New custom connector (1)** dropdown and select Create from **Azure service (Preview) (2)**.

   ![](media/E9T2S4-2109.png)

1. On the Create from Azure service (preview) window, select the following options, and click on **Continue (6)**:

   - Connector name: **Star Wars (1)**.
   - Subscription: Select the subscription where your API Management instance is deployed **(2)**.
   - Azure Service: Select **API Management (3)**.
   - Service name: Select your API Management instance **(4)**.
   - API name: **star-wars (5)**.

      ![](media/E9T2S5-1004.png)

1. In the top left corner, click on **1. General** from the drop-down and select **3. Definition** screen, we need to define a search query string for people so that the Power App can search for character records by name.

   ![](media/def.png)

1. In **Action** dropdown you can select the get people and get people by id options. 

   ![](media/select-action.png)

1. Scroll down to the **Request** section, select **+ Import from sample (1)**. Select **Get (2)** in the Verb option, enter a sample request **URL (3) given below** with the search query string, and select **Import (4)**:

   - **https://apim-dev-hol-ms-<inject key="Deployment ID" enableCopy="false" />.azure-api.net/sw/people?search=Luke**

       ![](media/E9T2S7.1-1004.png)

       ![](media/E9T2S7.2-1004.png)

1. In the **Response** section of the `getpeople` action, select the `200` response and then select **+ Import from sample**. To get the sample JSON response, follow the steps below:

   - Navigate back to the **API Management service** in Azure Portal.
   
   - On the **API Management service** page, from the left menu, under **APIs**, select **APIs**. Select **Star Wars** drop-down and select **v2 (1)**. Select `Get People (2)`, and from the top menu select **Test (3)**, select the product scope as **Unlimited** and now select **Send (4)** and **copy (5)** the Response into a notepad.  

      ![](media/api.png)

   - Paste the response into the `Body` section of the response, and select **Import**.

      ![](media/aa5.png)

      ![](media/5.png)

1. Repeat step 7 to import for the `getpeoplebyid` action. Provide the ID as `1`. And in step - 7 Request section add this url - https://apim-dev-hol-ms-2253824.azure-api.net/sw/people/1/ and complete the step - 8 also.

   >**Note:** Delete if you have other **Actions** Apart from `getpeople` and `getpeoplebyid`.

   > Click on **... icon (1)** and select **delete (2)**.
   > ![](media/delete-o-operations.png)

1. In the left pane, select **+ New policy** under the **Policies** section.

   ![](media/E9T2S9-1901.png)

1. Fill out the new policy with the following information:

     - **Name: set-origin-header (1)**
  
     - **Template: Set HTTP header (2)**
  
     - **Header name: Origin (3)**
  
     - **Header value: https://make.powerapps.com (4)**
  
     - **Action if the header exists: override (5)**
  
     - **Run policy on: request (6)**

       ![](media/setorigin.png)
      
       ![](media/action.png)

1. Click on the **tick** mark on the top right, which will update the Connector.

   ![](media/tick-connector.png)

1. Select **5.Test (2)**, from the top left corner **(1)**, and click on **+New connection (3)** in the **Connections** section.

      ![](media/E9T2S12-1901.png)

1. When prompted to provide the subscription key, navigate to Azure Portal, and you can find the subscription key in the API Management Service, from the left menu under APIs click on **Subscriptions (1)**, choose **Unlimited**, click on **... > Show/hide keys (2)**. Copy the **Primary key (3)**.  

      ![](media/Pg25-subscriptionid.png)

1. Navigate back to the Power Apps page, paste the **subscription key (1)**, and select **Create (2)**.

      ![](./media/E9T2S13-2109.png)

1. Click More options, select Discover all, and scroll down to choose the **Custom Connectors** page in Power apps portal and click on the pencil icon i.e **Edit (2)** for **Star Wars API (1)**.

   ![](media/select-starwars-cc.png)

1. Return to the **Test** page and test each of the API actions, in **getpeople** in the search section type **Luke** and select **Test operations**.

   ![](media/8.png)

   ![](./media/E9T2S15.2-1901.png)

### Task 3: Generate the Star Wars Fan Club Application

In this task, you will create a Canvas App in Power Apps using the Excel worksheet as the primary data source.

1. In the Power Apps portal, click on **Home (1)** from the left navigation list and select **Start with data (2)** to create your app.

   ![](media/E9T3S1-1004.png)

1. On the Creat an app page, select **Upload file (1)** option and click on **Select from device (2)**.

   ![](media/E9T3S2-1004.png)

   ![](media/E9T3S2.1-1004.png)

1. Navigate to **C:\LabFiles (1)** path, select the **fanclubmembers.xlsx (2)** and click on **Open (3)** to upload the file. Then click on **Create app (4)**.

   ![](media/E9T3S4-2109.png)

   ![](media/E9T3S3.1-1004.png)

1. It may take a couple of minutes for Power Apps to generate the application based on the Excel data. Once the app is created, you would be navigated to the app canvas page. 

1. Click on **Skip** on the Welcom to Power Apps Studio pop-up window. 

1. The App will be open in Editing mode in Power Apps editor. You can click on the Play button at the top right corner to use the app. 

   ![](media/E9T3S7-2109.png)

### Task 4: Add the Star Wars API Data Source

In this task, you will add the Star Wars API custom connector as a data source to your Canvas App.

1. Select **Data (1)** from the left pane and then select **+ Add data (2)** from the drop-down menu.

2. Search for **Star Wars API (3)** in the search field and choose the connection to the **Star Wars API (4)**.

     ![](media/E9T4S2-2109.png)

1. Click on Play button to open the app and the app will look like this

     ![](media/E9T4S3-1004.png)

1. After the app is generated, you can customize it to match your requirements. This includes changing the app theme and branding, renaming labels and headers, reordering or hiding fields, adjusting the layout of lists and details, and applying conditional formatting based on data values. You can also enhance the app by adding search capabilities, buttons, and integrating external APIs using connectors to extend the app’s functionality.
--- 

## Summary

In this exercise, you created a Power Apps Canvas application that uses an Excel worksheet as the primary data source and integrates with the Star Wars API via a custom connector exported from Azure API Management. This application allows users to view and search for information about Star Wars characters.

## Conclusion

By completing this **Azure API Management** hands-on lab, you have gained practical experience in designing, implementing, and managing APIs using Azure API Management. You have learned how to create APIs from scratch, add existing APIs, implement security policies, apply rate limiting and throttling, monitor API performance, and export APIs for use in Power Platform applications. Through these exercises, you've developed skills in API governance, developer portal management, and integration with modern cloud services, enabling you to build scalable and secure API solutions for your organization.

### Congratulations! You've successfully completed the Hands-on lab.
