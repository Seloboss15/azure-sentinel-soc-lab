# Azure Sentinel SOC Lab

This project simulates the operations of a Security Operations Center (SOC) using Microsoft Sentinel. The lab includes a hybrid setup of both Linux and Windows VMs, integrated log collection rules, custom KQL analytics, and incident alerting. It also includes detection rules, hunting queries, dashboards, simulated attacks, and incident responses — all documented and supported with visuals. 📘 Overview

## 🔐 Key Features

- 🔍 Custom Detection Rules in KQL
- 🧪 Simulated Attacks and Alerting
- 📊 Dashboards and Workbooks
- 📁 Documented Incidents with Screenshots
- 💡 Threat Hunting with Sentinel

## Lab Architeture
🧩 Resource Group: azure-sentinel-rg

🔷 Virtual Machines  
  - selobosslinux (Linux, Syslog via AMA)  
  - windowsvm (Windows, Windows Security Events via AMA)  

🔗 Network Infrastructure  
  - Virtual Network: vnet1  
  - Network Interfaces: Linked to each VM.  
  - Network Security Groups: linux-vm-nsg, windows-vm-nsg, and selobosslinux-nsg for firewall control.  

🛠️ Log and Monitoring Tools  
   - Log Analytics Workspace: law-lab
   - Microsoft Sentinel: Enabled on law-lab  

Data Collection Rules:

## 📁 Project Structure


