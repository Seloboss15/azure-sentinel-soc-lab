# Virtual Machine Setup for SOC Simulation

This guide provides instructions to set up two virtual machines, `selobosslinux` (Linux) and `windowsvm` (Windows), under the resource group "azure-sentinel-rg". These VMs will be used in a Microsoft Sentinel SOC simulation, sending logs to the Log Analytics workspace "Law-lab" for monitoring and analysis.

## Prerequisites

Before proceeding, ensure you have completed the following:

- **Resource Group**: The resource group "azure-sentinel-rg" must be created (see [Resource Group Setup](resource_group_setup.md)).
- **Active Azure Subscription**: Ensure your subscription is active and has sufficient credits or quota to create VMs.

## Virtual Machine Creation

We’ll create two VMs: `selobosslinux` (a Linux VM for Syslog collection) and `windowsvm` (a Windows VM for Windows event collection). Both will be deployed in the "azure-sentinel-rg" resource group.

### Step 1: Set Up `selobosslinux` (Linux VM)

1. **Navigate to Virtual Machines**:
   - Sign in to the [Azure Portal](https://portal.azure.com/).
   - In the left-hand menu, click on **Virtual machines**, or search for "Virtual machines" in the search bar.

2. **Create a New Linux VM**:
   - Click **+ Create** > **Azure virtual machine**.
   - In the "Create a virtual machine" pane, configure the following under the **Basics** tab:
     - **Subscription**: Select your active subscription.
     - **Resource group**: Choose `azure-sentinel-rg`.
     - **Virtual machine name**: Enter `selobosslinux`.
     - **Region**: Select the same region as your resource group (e.g., East US).
     - **Image**: Choose a Linux distribution (e.g., `Ubuntu Server 20.04 LTS - Gen2`).
     - **Size**: Select a small size for testing (e.g., `Standard_B1s` – 1 vCPU, 1 GiB memory).
     - **Authentication type**: Choose **Password** or **SSH public key** (recommended for Linux).
       - If using a password, set a username (e.g., `azureuser`) and a strong password.
       - If using an SSH key, generate or upload your public key.
   - Under the **Networking** tab:
     - Ensure a virtual network (VNet) and subnet are created (or use defaults).
     - Enable **Public IP** for SSH access (e.g., `selobosslinux-ip`).
     - Add an inbound port rule for SSH (port 22) in the Network Security Group (NSG).
   - Under the **Monitoring** tab:
     - Enable **Boot diagnostics** (optional, for troubleshooting).
     - Leave other settings as default for now.
   - Click **Review + create**, then **Create** after validation.
   - Wait for deployment (5–10 minutes). Once complete, click **Go to resource**.

3. **Verify Deployment**:
   - Confirm `selobosslinux` is running in the Azure portal.
   - Note the public IP address for SSH access (e.g., `selobosslinux-ip`).

4. **Connect to the VM**:
   - Use an SSH client (e.g., PuTTY, terminal):
     ```bash
     ssh azureuser@<selobosslinux-public-ip>

    Verify connectivity and basic functionality (e.g., sudo apt update for Ubuntu).

## Step 2: Set Up windowsvm (Windows VM)  

1. **Create a New Windows VM**:
   - In the Azure portal, go to **Virtual machines** > **+ Create** > **Azure virtual machine**.
   - In the "Create a virtual machine" pane, configure the following under the **Basics** tab:
     - **Subscription**: Select your active subscription.
     - **Resource group**: Choose `azure-sentinel-rg`.
     - **Virtual machine name**: Enter `windowsvm`.
     - **Region**: Select the same region as `selobosslinux` (e.g., East US).
     - **Image**: Choose a Windows image (e.g., `Windows Server 2019 Datacenter - Gen2`).
     - **Size**: Select a small size (e.g., `Standard_B1s`).
     - **Authentication type**: Choose **Password**.
       - Set a username (e.g., `azureuser`) and a strong password.
   - Under the **Networking** tab:
     - Use the same VNet as `selobosslinux` (or let Azure create a new one).
     - Enable **Public IP** for RDP access (e.g., `windowsvm-ip`).
     - Add an inbound port rule for RDP (port 3389) in the NSG.
   - Under the **Monitoring** tab:
     - Enable **Boot diagnostics** (optional).
   - Click **Review + create**, then **Create** after validation.
   - Wait for deployment (5–10 minutes). Once complete, click **Go to resource**.

2. **Verify Deployment**:
   - Confirm `windowsvm` is running in the Azure portal.
   - Note the public IP address for RDP access (e.g., `windowsvm-ip`).

3. **Connect to the VM**:
   - Use Remote Desktop Protocol (RDP) client (e.g., Windows Remote Desktop):
     - Open RDP client, enter the public IP of `windowsvm`.
     - Use the username (`azureuser`) and password set during creation.
   - Verify connectivity and basic functionality (e.g., open PowerShell, check system info).
