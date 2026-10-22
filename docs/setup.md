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
In progress. 
