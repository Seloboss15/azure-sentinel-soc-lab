# Data Connector Setup for Log Analytics Workspace in SOC Simulation

This guide explains how to set up a data connector in the Log Analytics workspace "Law-lab" to collect logs from the Linux VM `selobosslinux` for a Microsoft Sentinel SOC simulation. Initially, we explore the deprecated "Syslog via Legacy Agent" approach as requested, but due to its deprecation, we recommend transitioning to the modern "Syslog via AMA" data connector for long-term support.

## Prerequisites

Before proceeding, ensure you have completed the following:

- **Resource Group**: The resource group "azure-sentinel-rg" is created (see [Resource Group Setup](resource_group_setup.md)).
- **Virtual Machines**: The VMs `selobosslinux` and `windowsvm` are deployed (see [VM Setup](vm_setup.md)).
- **Log Analytics Workspace**: The workspace "Law-lab" is created and integrated with Microsoft Sentinel (see [Log Analytics Setup](law_lab_setup.md)).
- **Permissions**: Ensure you have Contributor or Owner role on the subscription to manage data connectors and agents.

## Important Note: Legacy Agent Deprecation

The "Syslog via Legacy Agent" data connector relies on the legacy Log Analytics agent, which was deprecated on August 31, 2024. Microsoft no longer provides support for this agent, and users are strongly recommended to migrate to the Azure Monitor Agent (AMA). However, for historical context and to address the original request, we’ll outline the legacy approach first, followed by the recommended AMA-based approach.

## Approach 1: Syslog via Legacy Agent (Deprecated)

### Step 1: Search for and Set Up the Syslog via Legacy Agent Data Connector

1. **Navigate to Microsoft Sentinel**:
   - Sign in to the [Azure Portal](https://portal.azure.com/).
   - Search for "Microsoft Sentinel" and select your workspace ("Law-lab").

2. **Access Data Connectors**:
   - In Microsoft Sentinel, under the **Configuration** section, select **Data connectors**.
   - In the search bar, type "Syslog via Legacy Agent" and select it from the list.

3. **Install the Connector**:
   - On the "Syslog via Legacy Agent" connector page, click **Open connector page**.
   - Click **Install** if the connector isn’t already installed. Note: Since this connector is deprecated, it may not be available in the portal as of June 2025
