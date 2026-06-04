## Exercise 4 Task 2: Caching policy

In this task, you will explore and apply the caching policy to your API.

Azure API Management can be configured for response caching which can significantly reduce API latency, bandwidth consumption, and web service load for data that does not change frequently.

1. Navigate to **All API's** section in the API management resource. We will now apply caching to the **Colors API** we created in Exercise 3.

1. Go to the **Colors API (1)** and select the **Get random color (2)** call:

      ![APIM Adding Enable Caching](media/10.png)

1. Under **Inbound processing**, click on **+ Add policy**.
    
      ![APIM Adding Enable Caching](media/E4T2S3-0209.png)

1. Scroll down and select **Cache responses**.

      ![APIM Enable Caching](media/12.png)

1. Set a caching duration of `15` **(1)** seconds and **Save (2)**.

      ![APIM Cache Duration](media/p10t2p5.png)

1. Navigate back to the website and configure the Colors website from **Exercise 3(Task 4.2)** to use the Unlimited subscription URL.

1. Select **Start**.

1. Notice that for each 15-second period, the same color is set.

    > **Note:** If you are unable to see colors, please refresh the page once. 

    ![Colors Website Caching](media/14.png)

1. Looking at the **Get Random color** GET API policies in the **Policy Code editor**, you'll see the caching policy defined:

    ![Colors Website Caching](media/14a.png)

    ![Colors Website Caching](media/E4T2S9-0209.png)

   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - If you receive a success message, you can proceed to the next task.
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
   > - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
         
      <validation step="23e3a74f-bdaf-49f0-9cab-d1090fe06328" />

## Summary

In this task, you configured response caching for the "Get random color" call in the Colors API using Azure API Management.

### Now, click on Next from the lower right corner to move on to the next page for further tasks of Exercise 4.

  ![](../gs/media/nextpagetab.png)




