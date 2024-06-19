# BICEP Template to automate the deployment of a VM for Cloud Gaming in Microsoft Azure

## Prerequisites
- [Azure Account & Subscription](https://azure.microsoft.com/en-us/free)
- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) or [PowerShell installed](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell?view=azps-12.0.0)
- [BICEP cli installed](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/install) 

## Template Overview

This template provisions the following resources:

- **Virtual Machine**:
  - Configured with Windows 11 (Windows-11, 21h2-pro)
  - Options for various VM sizes based on the gaming requirements (Standard_NG8ads_V620_v1, Standard_NG16ads_V620_v1, Standard_NG32ads_V620_v1)
  - Optional spot instance configuration for cost efficiency

- **Network Security Group**:
  - Security rules for RDP, VNC, and Parsec to facilitate remote access and gaming network configurations

- **Public IP Address**:
  - Static IPv4 address for the VM, making it accessible over the Internet

- **Virtual Network and Subnet**:
  - A virtual network with a default subnet to host the gaming VM

- **Network Interface**:
  - Connected to the created VM, subnet, and public IP with network security group rules applied
 
## Parameters

- `virtualMachines_gamevm_name`: Name of the virtual machine (Default: "gamevm")
- `adminUsername`: Administrator username for the VM
- `adminPassword`: Administrator password for the VM (Secure string)
- `virtualMachines_gamevm_sku`: SKU for the VM (Options: "Standard_NG8ads_V620_v1", "Standard_NG16ads_V620_v1", "Standard_NG32ads_V620_v1")
- `virtualMachines_gamevm_priority`: Deployment priority ("regular" or "spot", Default: "spot")
- `virtualNetworks_gamevm_name`: Name of the virtual network (Default: "gamevm-vnet")
- `networkInterfaces_gamevm_name`: Name of the network interface (Default: "gamevm-nic")
- `publicIPAddresses_gamevm_ip_name`: Name of the public IP address (Default: "gamevm-ip")
- `networkSecurityGroups_gamevm_nsg_name`: Name of the network security group (Default: "gamevm-nsg")
