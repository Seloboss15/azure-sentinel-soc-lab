# Resource Group Setup for SOC Simulation

This guide outlines the initial setup of the resource group "azure-sentinel-rg" for a Microsoft Sentinel SOC simulation using the Log Analytics workspace "Law-lab". A resource group is a container that holds related Azure resources, providing a way to manage and organize them effectively.

## Prerequisites

Before proceeding, ensure you have the following:

- **Active Azure Subscription**: You need an active Azure subscription to create and manage resources. If you don’t have one, sign up at [Azure Free Account](https://azure.microsoft.com/free/) or use an existing subscription provided by your organization.

## Resource Group Creation

The resource group "azure-sentinel-rg" serves as the foundation for deploying virtual machines (`selobosslinux` and `windowsvm`) and the Log Analytics workspace ("Law-lab") for this SOC simulation.

### Steps to Create the Resource Group

1. **Sign in to Azure Portal**:
   - Open your web browser and navigate to [Azure Portal](https://portal.azure.com/).
   - Sign in with your Azure account credentials.

2. **Access Resource Groups**:
   - In the left-hand menu, click on **Resource groups**.
   - Alternatively, use the search bar at the top and type "Resource groups" to find it.

3. **Create a New Resource Group**:
   - Click the **+ Create** button on the top left.
   - In the "Create a resource group" pane:
     - **Subscription**: Select your active Azure subscription from the dropdown.
     - **Resource group name**: Enter `azure-sentinel-rg`.
     - **Region**: Choose a region close to your location or where your VMs will be deployed (e.g., East US, West Europe). Note the region for consistency with other resources.
   - Click **Review + create**.
   - After validation, click **Create** to deploy the resource group.

4. **Verify Creation**:
   - Once the deployment is complete (usually within a few seconds), click **Go to resource**.
   - Confirm that "azure-sentinel-rg" appears in the list of resource groups with a status of "Active".
