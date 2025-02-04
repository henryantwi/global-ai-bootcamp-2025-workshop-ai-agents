# Setup

**Follow these steps to set up your environment and begin the workshop.**

## Prerequisites

1. Access to an Azure subscription. 
2. You need a GitHub account. If you don’t have one, create it at [GitHub](https://github.com/join){:target="_blank"}.


## Access to an Azure Subscription

To run the lab you need to deploy some resources deployed in an Azure Subscription. For this there are multiple options.

1. Use your own Azure Subscription
2. Create a [free account](https://azure.microsoft.com/free/){:target="_blank"} before you begin.
3. Use an Azure Pass you received from your trainer.


!!! note
    #### Azure Pass activation

    1. Ask you Global AI Bootcamp trainer for your event code. This is a 6 digits code.
    2. Navigate to [pass.globalaiyboocamp.com](https://pass.globalaibootcamp.com){:target="_blank"}
    3. Follow the instruction on screen.

## GitHub Codespaces

The way to run this workshop is using GitHub Codespaces. This provides a pre-configured environment with all the tools and resources needed to complete the workshop.

Select **Open in GitHub Codespaces** to open the project in GitHub Codespaces.

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/GlobalAICommunity/global-ai-bootcamp-2025-workshop-ai-agents){:target="_blank"}

!!! Warning "It will take several minutes to build the Codespace so carry on reading the instructions while it builds."

## Lab Structure

Each lab in this workshop includes:

- An **Introduction**: Explains the relevant concepts.
- An **Exercise**: Guides you through the process of implementing the feature.

## Project Structure

The workshop’s source code is located in the **src/workshop** folder. Be sure to familiarize yourself with the key **subfolders** and **files** you’ll be working with throughout the session.

1. The **files folder**: Contains the files created by the agent app.
1. The **instructions folder**: Contains the instructions passed to the LLM.
1. The **main.py**: The entry point for the app, containing its main logic.
1. The **sales_data.py**: Contains the function logic to execute dynamic SQL queries against the SQLite database.
1. The **stream_event_handler.py**: Contains the event handler logic for token streaming.

![Lab folder structure](./media/project-structure-self-guided.png)

## Authenticate with Azure

You need to authenticate with Azure so the agent app can access the Azure AI Agents Service and models. Follow these steps:

1. Ensure the Codespace has been created.
1. In the Codespace, open a new terminal window by selecting **Terminal** > **New Terminal** from the **VS Code menu**.
2. Run the following command to authenticate with Azure:

    ```powershell
    az login --use-device-code
    ```

    !!! note
        You'll be prompted to open a browser link and log in to your Azure account.

        1. A browser window will open automatically, select your account type and click **Next**.
        2. Sign in with your Azure subscription **Username** and **Password**.
        3. Select **OK**, then **Done**.

3. Then select the appropriate subscription from the command line.
4. Leave the terminal window open for the next steps.

## Deploy the Azure Resources

The following resources will be created in your Azure subscription:  

- An **Azure AI Foundry hub** named **agent-wksp**
- An **Azure AI Foundry project** named **Agent Service Workshop** 
- A **Serverless (pay-as-you-go) GPT-4o model deployment** named **gpt-4o (Global 2024-08-06)**. See pricing details [here](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/){:target="_blank"}.

From the VS Code terminal run the following command:

```bash
cd infra && ./deploy.sh
```

## Workshop Configuration

The deploy script generates the **src/workshop/.env** file, which contains the project connection string, model deployment name, and Bing connection name.

Your **.env** file should look similar to this but with your project connection string.

```python
MODEL_DEPLOYMENT_NAME="gpt-4o"
PROJECT_CONNECTION_STRING="<your_project_connection_string>"
```