---
summary: Explore how to configure Azure resources for OutSystems 11 (O11) chatbot integration, including creating services and channels.
tags: azure, cognitive services, chatbots, qna maker, cloud services
locale: en-us
guid: 2d4d86ce-b835-4fb6-9af8-ecee723d94a7
app_type: traditional web apps, mobile apps, reactive web apps
platform-version: o11
figma: https://www.figma.com/file/jSgZ0l0unYdVymLxKZasno/Extensibility%20and%20Integration?node-id=410:5
audience:
  - full stack developers
  - frontend developers
  - backend developers
  - mobile developers
outsystems-tools:
  - service studio
coverage-type:
  - apply
  - unblock
---

# Create the chatbot resources in Azure

This document contains instructions for using Azure resources to add and get configurations for your OutSystems chatbot. You need a valid Azure subscription to follow instructions in this document.

<div class="info" markdown="1">

Just starting? Check the [chatbot configuration wizard](configuration-wizard.md) to speed up the setup of your chatbot.

</div>

## Create a QnA Maker service in Azure { #create-qna-service }

Follow these instructions to create a QnA Maker service which you need for the FAQ chatbot. QnA Maker is part of Azure Cognitive Services.

<div class="info" markdown="1">

You can also use the [chatbot configuration wizard](configuration-wizard.md) to set up this part of chatbot.

</div>

1. Sign into the Azure portal at [portal.azure.com](https://portal.azure.com).

1. Click the search field (or press **Ctrl + /** ) and enter `QnA Maker`. Locate the **Marketplace** section in the results and click **QnA Maker**.
   
    ![Screenshot showing how to search for QnA Maker in the Azure portal](images/azure-portal-qna-search.png "Azure Portal QnA Maker Search")

1. Enter the information for your QnA Maker and click **Create**. Here is what you need to provide:

    <div class="info" markdown="1">

    The availability of the settings in Azure depends on your Azure account permissions. You may have to ask your administrators to create resources if your account doesn't have permissions to create them.

    </div>

    * **Name**. Name and custom domain for the service.
    * **Subscription**. The Azure subscription you want to use for the bot.
    * **Pricing tier**. The pricing tier for the service.
    * **Resource group**. The resource group to which you want to add the bot.
    * **Azure search pricing tier**. The pricing tier for the service.
    * **Azure Search location**. The location of the datacenter from which the bot service runs.
    * **App name**. The name of your bot service that's part of the URL to reach the service.
    * **Website location**. The location where you deploy the service.
  
    Optional settings:

    * **App insights**. If you want to track your app performance and collect telemetry information, activate this option.
  
    ![Screenshot of the Azure portal interface for creating a new QnA Maker service](images/azure-qna-maker-service-new.png "Azure QnA Maker Service Creation")

1. Click **Create**. After validation and deployment, the website redirects you to the Azure home page.

    <div class="info" markdown="1">

    If you reached this step while creating an FAQ chatbot, you should now do one of the following:

    * If you haven't created a knowledge base: [create a new knowledge base](guide-azure-kb.md#create-kb)
    * If you already have a knowledge base: [publish the knowledge base and create a chatbot service](guide-azure-kb.md#publish-kb)

    For an overview see [Getting started: How to create an FAQ chatbot](get-started-faq-chatbot.md).

    </div>

## Add a direct line channel for a bot service { #create-direct-line-channel }

Follow these steps to add a direct line channel and allow the OutSystems chatbot component to communicate with the Azure chatbot back end.

<div class="info" markdown="1">

You can also use the [chatbot configuration wizard](configuration-wizard.md) to set up this part of chatbot.

</div>

1. Sign into the Azure portal at [portal.azure.com](https://portal.azure.com).

1. Locate your bot name in **Recent resources** or search the bot in the search bar, then click the bot name. The settings page opens.

    ![Screenshot of the Azure Web App Bot dashboard showing the bot settings](images/azure-web-app-bot-dashboard.png "Azure Web App Bot Dashboard")

1. Open **Channels** from the side menu, locate **Add a featured channel** and click **Configure direct line channel button**. A page to configure direct line opens. 

    ![Screenshot of the Azure portal showing the configuration page for a new Direct Line channel in a Web App Bot service](images/azure-web-app-bot-service-direct-channel-new.png "Azure Web App Bot Direct Line Channel Configuration")

1. In **Configure Direct Line** you can copy a direct line key now, or do it later when you are configuring the OutSystem component. Click **Close** to return to the main settings page.

    ![Screenshot displaying the secret key for a Direct Line channel in the Azure Web App Bot service](images/azure-web-app-bot-service-direct-channel-key.png "Azure Web App Bot Direct Line Channel Secret Key")

## Getting the settings from bot service { #get-settings }

This section shows you where to locate the Azure settings you need for the OutSystems chat component. You first need to [create a bot service in Azure](#create-bot-service) to get these parameters.

<div class="info" markdown="1">

You can also use the [chatbot configuration wizard](configuration-wizard.md) to set up this part of chatbot.

</div>

### App id and password { #get-id-pass }

Azure application and password fields are, by default, named **MicrosoftAppId** and **MicrosoftAppPassword**. Find them under **Configuration** in the **App Service Settings** section.

1. Open the chatbot configuration page. You can open it by clicking your bot name in the Azure home page or by searching for the bot name in the search bar.

1. In the chatbot configuration page, click **Configuration** in the side menu.

1. In the **Configuration** page, under the **Application settings** section, locate **MicrosoftAppId** and **MicrosoftAppPassword**. Click the eye icons to reveal the field values. Copy the values.

    ![Screenshot showing the configuration values for MicrosoftAppId and MicrosoftAppPassword in the Azure Web App Bot service](images/azure-web-app-bot-service-direct-config.png "Azure Web App Bot Service Configuration")

Another way to get the settings is to download the source code. In the bot configuration page, click **Build** in the side menu and then **Download bot source code**. Open the **settings.json** file in the source code folder to get the values.

### Direct line secret { #get-direct-line-key }

You can get the secret after you [create a direct line channel](#add-a-direct-channel-for-a-bot-service) for your bot. 

1. Open the chatbot configuration page. You can open it by clicking your bot name in the Azure home page or by searching for the bot name in the search bar.

1. In the chatbot configuration page, click **Channels** in the side menu.

1. In the Connect to channels page, click **Edit** next to **Direct Line**. **Configure Direct Line** page opens.

    ![Screenshot of the Azure portal interface for editing a Direct Line channel in a Web App Bot service](images/azure-web-app-bot-service-direct-channel-edit.png "Editing Azure Web App Bot Direct Line Channel")

1. In the **Configure Direct Line** page, click **Show** under one of the secret keys. Copy the value.

    ![Screenshot displaying the secret key for a Direct Line channel in the Azure Web App Bot service](images/azure-web-app-bot-service-direct-channel-key.png "Azure Web App Bot Direct Line Channel Secret Key")

    <div class="info" markdown="1">

    You can select any of the two keys.

    </div>

## Create a bot service in Azure { #create-bot-service }

<div class="info" markdown="1">

Follow these instructions if you need to create a generic bot service in Azure, for example an echo chatbot to test the UI and back end. For creating an FAQ chatbot see [Getting started: How to create an FAQ chatbot](get-started-faq-chatbot.md).

</div>

Follow these steps to create a bot service in Azure. This bot monitors for new messages from your users. 

<div class="info" markdown="1">

You can also use the [chatbot configuration wizard](configuration-wizard.md) to set up this part of chatbot.

</div>

1. Sign into the Azure portal at [portal.azure.com](https://portal.azure.com).

1. Click the plus button titled **Create a resource**.

    ![Screenshot of the Azure portal highlighting the 'Create a resource' button](images/azure-add-resource-button.png "Azure Portal Create a Resource Button")

1. Select **AI + Machine Learning** and then click **Web App Bot**. A page to create In the new Web App Bot opens.
    
    ![Screenshot of the Azure portal page for creating a new Web App Bot service](images/azure-web-app-bot-service-new.png "Creating a New Azure Web App Bot")
    
1. Enter the information for your bot and click **Create**. Here is what you need to provide:

    * **Bot handle**. Unique identifier for the bot.
    * **Subscription**. The Azure subscription you want to use for the bot.
    * **Resource group**. The resource group to which you want to add the bot.
    * **Location**. The location of the datacenter from which the bot service runs.
    * **App name**. The name of your bot service that's part of the URL to reach the service.
    * **Bot template**. Click to expand. In the **SDK language** select **C#**. For creating an echo bot, select **Echo Bot**. For advanced bot service select **Basic Bot**.
    * **App service plan / location**. This is a set of the compute resources which the bot uses.   
    * **Microsoft App ID and password**. Verify the selected option is **Autocreate App Id and password**.

    ![Screenshot showing the form to create a new Web App Bot service in the Azure portal](images/azure-web-app-bot-service-create.png "Azure Web App Bot Service Creation Form")

    <div class="info" markdown="1">

    The availability of the settings in Azure depends on your Azure account permissions. You may have to ask your administrators to create resources if your account doesn't have permissions to create them.

    </div>

1. You are back to the Azure home page and there's a notification that a deployment is in process. Once the deployment of your bot finishes, you can get the settings you need for the OutSystems Chatbot component.

## Troubleshooting

Here are troubleshooting tips that can help you resolve issues in Azure.

### Azure resource provider isn't registered

While creating a resource in Azure you get the following error: "Azure (resource name) resource provider isn't registered, please click to search (resource handle) and register it first".

Check if the combination of settings in **Subscription** and **Resource group** match. You may be trying to create a resource in a group that doesn't belong to the subscription, or vice versa.
