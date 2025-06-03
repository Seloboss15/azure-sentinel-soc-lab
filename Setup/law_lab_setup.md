# Log Analytics Workspace Setup for SOC Simulation

This guide outlines the steps to create the Log Analytics workspace "Law-lab" and integrate it with Microsoft Sentinel. The workspace will collect logs from the virtual machines `selobosslinux` (Syslog) and `windowsvm` (Windows events) for security monitoring and analysis in a SOC simulation environment.

## Prerequisites

Before proceeding, ensure you have completed the following:

- **Resource Group**: The resource group "azure-sentinel-rg" is created (see [Resource Group Setup](resource_group_setup.md)).
- **Virtual Machines**: The VMs `selobosslinux` and `windowsvm` are deployed (see [VM Setup](vm_setup.md)).
- **Active Azure Subscription**: Ensure your subscription is active with sufficient permissions (e.g., Contributor or Owner role) to create Log Analytics workspaces and enable Microsoft Sentinel.

## Log Analytics Workspace Creation

The Log Analytics workspace "Law-lab" will store logs and metrics from your VMs, enabling analysis and threat detection in Microsoft Sentinel.

### Step 1: Create the Log Analytics Workspace

1. **Navigate to Log Analytics Workspaces**:
   - Sign in to the [Azure Portal](https://portal.azure.com/).
   - In the search bar at the top, type "Log Analytics workspaces" and select it from the results.

2. **Create a New Workspace**:
   - Click **+ Create** to start creating a new Log Analytics workspace.
   - In the "Create Log Analytics workspace" pane, configure the following under the **Basics** tab:
     - **Subscription**: Select your active subscription.
     - **Resource group**: Choose `azure-sentinel-rg`.
     - **Name**: Enter `Law-lab`.
     - **Region**: Select the same region as your resource group and VMs (e.g., East US).
   - Under the **Pricing tier** tab:
     - Leave the default pricing tier (e.g., Pay-as-you-go) unless you have specific requirements.
   - Under the **Tags** tab (optional):
     - Add tags if needed (e.g., `Environment: SOC-Simulation`).
   - Click **Review + create**, then **Create** after validation.
   - Wait for deployment (1–3 minutes). Once complete, click **Go to resource**.

3. **Verify Creation**:
   - Confirm that "Law-lab" is listed under **Log Analytics workspaces** with a status of "Active".
   - Note the **Workspace ID** (found in **Overview**) for future configurations.

### Step 2: Enable Microsoft Sentinel on the Workspace

Microsoft Sentinel will use the "Law-lab" workspace to provide security analytics, threat detection, and incident response capabilities.

1. **Navigate to Microsoft Sentinel**:
   - In the Azure portal, search for "Microsoft Sentinel" in the search bar and select it.

2. **Add the Workspace to Sentinel**:
   - Click **+ Create** or **Add Microsoft Sentinel to a workspace**.
   - In the "Add Microsoft Sentinel to a workspace" pane:
     - Select your subscription and resource group (`azure-sentinel-rg`).
     - Choose the workspace `Law-lab` from the list.
   - Click **Add**.
   - Wait for Sentinel to enable (1–5 minutes). Once complete, you’ll be redirected to the Sentinel overview page for "Law-lab".

3. **Verify Sentinel Integration**:
   - In **Microsoft Sentinel**, confirm that the workspace "Law-lab" is active.
   - Explore sections like **Overview**, **Logs**, and **Data connectors** to familiarize yourself with the interface.

### Step 3: Prepare for Log Collection (Overview)

The workspace is now ready to collect logs from `selobosslinux` and `windowsvm`. This will involve installing the Azure Monitor Agent (AMA) and configuring data collection rules, which will be covered in the next guide. Here’s a brief overview:

- **selobosslinux**:
  - Configure Syslog via AMA to collect SSH logs (e.g., failed login attempts).
- **windowsvm**:
  - Configure Windows Security Events via AMA to collect Windows event logs (e.g., failed logins).
- **Microsoft Sentinel**:
  - Use the workspace to create analytics rules and workbooks for SOC monitoring.

### Details
- **Resource Group**: azure-sentinel-rg
- **Workspace Name**: Law-lab
- **Created On**: June 03, 2025, 02:12 AM CDT
- **Purpose**: To collect and analyze logs from VMs for a SOC simulation using Microsoft Sentinel.

## Next Steps
- Install the Azure Monitor Agent (AMA) on `selobosslinux` and `windowsvm` and configure data collection rules to send logs to "Law-lab" (see upcoming guide).
- Set up data connectors in Microsoft Sentinel (e.g., Syslog via AMA, Windows Security Events via AMA).
- Create analytics rules in Sentinel to detect security events like failed logins.

## Notes
- Ensure the region for "Law-lab" matches the region of your VMs to minimize latency.
- Microsoft Sentinel may incur additional costs; monitor usage in the Azure Cost Management tool.
- Familiarize yourself with the Logs section in "Law-lab" to run KQL queries (e.g., `Syslog | take 10`).
