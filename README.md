# Azure Data Factory to Azure Service Bus Queue integration using REST API
Configuring Azure Data Factory (ADF) to send messages to an Azure Service Bus queue.

## Prerequisites
* Azure Subscription
* Azure Data Factory
* Azure Service Bus
* Azure Active Directory

# Create a User Assigned Managed Identity
* In the Azure portal, search for Managed Identities and select it.
* Click on + Add.
* Fill in the necessary details such as the subscription, resource group, and name for your managed identity.
* Click Review + create and then Create.

# Assign the Managed Identity to Azure Data Factory
* In the Azure portal, navigate to your Azure Data Factory instance.
* Under the Settings section, click on Identity.
* Click on the User Assigned tab.
* Click + Add.
* Select the managed identity you created earlier.
* Click Add.

# Assign Roles to the User Assigned Managed Identity
* Navigate to Service Bus Namespace
* Navigate to Access control (IAM).
* Click on Add role assignment.
* Select the role Azure Service Bus Data Sender.
* In the Members section, choose Managed Identity (System Or User).
* Select the managed identity you added to the Data Factory.
* Click Save.

# Configure Web Activity in Azure Data Factory
* In your Data Factory pipeline, drag and drop a Web activity onto the canvas.
* Set to the Service Bus REST API URL for sending messages - https://**your-service-bus-namespace**.servicebus.windows.net/**your-queue-name**/messages
* Method: Set to POST and provide body
* Authentication: System assigned managed entity Or User assigned managed entity
* Resource: https://servicebus.azure.net/
