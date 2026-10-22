# Setup Guide

## 1. Create the Virtual Machine
Created a Windows Server 2022 Evaluation VM in
VirtualBox using the Desktop Experience installation.

Configuration details are documented in Architecture.

## 2. Configure the Server

### Hostname
Renamed the server to TW-DC01.

### Network
Configured a static IPv4 address.

- IP address: 192.168.50.10
- Subnet mask: 255.255.255.0
- Default gateway: None
- Preferred DNS: 192.168.50.10

Verified the hostname and network configuration
using PowerShell commands.

## 3. Install Active Directory Domain Services
Installed Active Directory Domain Services role on TW-DC01 through Server Manager.

The role installation completed successfully.

## 4. Promote the Sever to a Domain Controller
Used the Active Directory Domain Services Configuration Wizard and entered the following selections:

### Deployment Configuration

| Setting | Value |
|---|---|
| Deployment operation | Add a new forest |
| Root domain name | `ad.toyworks.test` |
| NetBIOS domain name | `TOYWORKS` |
| Domain controller hostname | `TW-DC01` |

### Domain Controller Options

| Setting | Value |
|---|---|
| Domain functional level | Windows Server 2025 |
| Forest functional level | Windows Server 2025 |
| DNS Server | Enabled |
| Global Catalog | Enabled |
| Read-only domain controller (RODC) | Disabled |
| DSRM password | Configured and stored securely |

### Additional Configuration

| Setting | Value |
|---|---|
| DNS delegation | No |
| Database path | C:\WINDOWS\NTDS |
| Log files path | C:\WINDOWS\NTDS |
| SYSVOL path | C:\WINDOWS\SYSVOL |
| Prerequisites check | Passed, with a DNS delegation warning |
