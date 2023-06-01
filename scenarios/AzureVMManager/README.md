# Azure Virtual Machine Management 

This scenario provides an approach to using PowerBI, PowerApps, and Power Automate to monitor and manage your Azure Virtual Machines. While not a complete

## Design Approach

Using a scheduled Power Automate flow, we capture the current state of every VM within the Azure tenant and store it as a JSON document within CosmosDB for low-latency querying and updating.
CosmosDB provides an out of the box output for PowerBI via Azure Synapse, which allows for the easy creation of a Power BI Dashboard. Using the Power App visualization control within Power BI, the embedded Power App provides the control pane for stopping and starting the VMs.

![Azure VM Management Design Pattern](img/Architecture.png)

## Environment Setup

* Azure App Registration with User Impersonation delegated permissions to the Azure Service Management API.
* Azure Cosmos DB with a container for storing the VM images

## Using the solution

* Ensure to pre-create the Azure App Registration and the Cosmos DB resources first
* Import the [Solution Zip](solutions/VMManagementFlows_1_0_0_1.zip) into your existing Dev / Non-Prod Dataverse Environment
* Upon import, you will be prompted to create the connections for Azure Resource Manager, Azure Virtual Machines, the Custom Connector, and Azure CosmosDB
* Ensure you update the connection references & configuration for the included flows, specifically the steps for connecting to CosmosDB.
* The App canvas app incuded in the solution is provided as reference. When you create your own PowerBI report, you may want to create your own new canvas app instead.

