# Azure API Management

### Overall Estimated Duration: 8 Hours

## Overview

This lab provides a comprehensive introduction to the Azure API Management service, guiding you through the essential steps to set up, configure, and optimize API services in Azure. You will learn how to access an API Management instance, customize the Developer Portal, and integrate APIs. The lab exercises cover practical scenarios such as importing APIs, applying security policies, monitoring usage, and scaling your architecture for enterprise needs. By completing this lab, you will gain the skills needed to manage APIs efficiently and securely within the Azure ecosystem.

## Objective

Understand how to leverage Azure’s API Management tools to enhance your coding workflow. Gain hands-on experience in setting up API instances, managing user interactions, and optimizing API performance and security. By the end of this lab, you will be able to:

   - **Verify API Management Instance**: Set up and verify an Azure API Management instance in your environment. 
     Learn how to configure basic settings and ensure the instance is properly integrated with your Azure resources.
   - **Developer Portal**: Deploy and customize the Developer Portal to match your organization’s branding and 
     requirements. Configure email settings, manage user experience, and create product definitions for your API 
     offerings.
   - **Adding APIs**: Create new APIs and integrate them with existing APIs, such as the Star Wars API, to enhance 
     functionality. Import APIs using OpenAPI specifications, and manage aspects like testing, subscription keys, and 
     rate limits to ensure seamless operation.
   - **Policy Expressions**: Configure and implement policy expressions to control API behavior, enforce security 
     rules, 
     and handle transformations. Learn to write custom policies to tailor API responses and request handling as per 
     business requirements.
   - **Version and Revisions**: Handle API versions and revisions effectively to maintain backward compatibility and 
     manage updates. Learn best practices for versioning strategies to ensure smooth transitions and minimal disruption 
     to users.
   - **Analytics & Monitoring**: Implement and utilize tools for tracking API performance and usage, and generate 
     insightful reports. Set up monitoring to detect anomalies, analyze trends, and optimize API performance based on 
     real-time data.
   - **Security**: Integrate security measures such as OAuth and IP restrictions to protect your APIs from 
     unauthorized access. Implement robust authentication and authorization practices to safeguard sensitive data and 
     ensure secure interactions.
   - **Fusion Dev**: Utilize Fusion Dev tools to enhance API management, streamline development workflows, and automate 
     tasks. Explore features that support API lifecycle management and improve collaboration within development teams.
   - **Architecture Design Session**: Design and plan the architecture of your API Management setup with a focus on 
     scalability, security, and performance. Develop a comprehensive strategy to address potential challenges and 
     optimize the infrastructure for future growth.


## Prerequisites

   - **Azure Account**: An active Azure account with permissions to create and manage resources.
   - **Basic API Knowledge**: Understanding of API concepts such as endpoints, operations, and HTTP methods.
   - **API Management Familiarity**: Basic knowledge of API management tools and concepts.
   - **Programming Skills**: Proficiency in a programming language (e.g., Python, JavaScript, C#) to work with APIs and 
     integrations.
   - **OpenAPI Specification**: Familiarity with OpenAPI specifications for importing APIs.
   - **Web Development Knowledge**: Understanding of web technologies and concepts for customizing the Developer Portal.
   - **Security Fundamentals**: Basic knowledge of API security practices and measures.
   - **Analytics Understanding**: Familiarity with analytics and monitoring tools for tracking API performance.
   - **Fusion Dev Tools**: Basic knowledge of Fusion Dev tools for API management and development.

## Architecture

The architecture uses Azure API Management to manage and secure APIs. It includes setting up an API Management instance to handle and direct API requests while applying policies like rate limits and CORS for secure access. The Developer Portal is customized to offer easy-to-use API documentation, testing, and subscription features. APIs are hosted on Azure App Services or AKS, with security managed through Azure Key Vault and authentication methods. Analytics tools like Azure Monitor track performance, and Azure Logic Apps and CDN are used to improve integration and content delivery. This setup ensures a secure, scalable, and user-friendly API management system.

## Architecture Diagram

![](media/APIM-Arch-diag-2301.png)

## Explanation of Components

1. **Azure API Management Instance**: Central hub for managing and securing APIs. It directs API traffic, applies policies, and ensures smooth operation.

2. **API Gateway**: Routes requests to backend services and enforces rules like rate limiting and CORS (Cross-Origin Resource Sharing) for secure API access.

3. **Developer Portal**: User-friendly interface for developers to access API documentation, test APIs, and manage subscriptions.

4. **Azure Functions**: Executes serverless code in response to events, useful for processing or integrating with other services.

5. **Azure Key Vault**: Stores sensitive information like API keys and certificates securely.

6. **Azure Monitor and Application Insights**: Tracks API performance and provides alerts for monitoring and optimization.

7. **Azure Logic Apps**: Automates workflows and integrates with other services based on API events.

## Getting Started with Lab

Welcome to your Azure API Management workshop! We've prepared a seamless environment for you to explore and learn about Azure services. Let's begin by making the most of this experience:

## Accessing Your Lab Environment

Once the environment is provisioned, a virtual machine (JumpVM) and lab guide will be loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number at the bottom of the lab guide to switch to different exercises in the lab guide.

   ![07](media/guidetab.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab. Additionally, the credentials will also be emailed to your registered email address.

   ![08](media/env-tab.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.

  ![](media/split-tab.png)

## Managing Your Virtual Machine
 
Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!

   ![](media/resources-0109.png) 

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕: 100%** icon located next to the timer in the lab environment.

   ![](media/zoomintab.png)

## Let's Get Started with Azure Portal

1. In the Lab VM, click on the Azure portal shortcut of the Microsoft Edge browser, which is created on the desktop.

   ![09](media/api-08.png)
   
1. On the **Sign into Microsoft Azure** tab, you will see the login screen. In that, enter the following email/username and then click on **Next**. 
   * Email/Username: <inject key="AzureAdUserEmail"></inject>
   
     ![04](media/azure-signin1-0109.png)
     
1. Now enter the following password and click on **Sign in**.
   * Password: <inject key="AzureAdUserPassword"></inject>
   
     ![05](media/azpassword.png)
  
1. If you see the pop-up **Stay Signed in?**, click **No**.

1. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

    ![](media/Azure-cancel-tour.png)

      
## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:
- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support
 
Now, click on Next from the lower right corner to move on to the next page.

  ![](media/nextpagetab.png)

### Happy Learning!!
