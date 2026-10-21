# Lab Architecture

## Purpose
  This document describes the planned architecture of the Toyworks Active Directory lab.

## Planned Components
  - Ubuntu host running VirtualBox
  - Windows Server domain controller
  - Active Directory Domain Services
  - DNS for domain name resolution
  - Windows client workstation (future phase)

## Network Design
  This lab uses a VirtualBox Internal Network named Toyworks-LAN to isolate virtual machines from the host's external network.

  The internal network will connect the domain controller and future Windows client machines.

  Internet connectivity is not provided directly through this internal network. External access may be introduced separately when required.
  
## Design Decisions
  Configuration decisions will be documented as the lab develops, including the reasons for each decision and any alternatives considered.

## Virtual Machine Configuration

### TW-DC01
| Setting | Value|
|---|---|
| Purpose | Active Directory Domain Controller |
| Operating System | Windows Server 2022 Evaluation |
| Installation Type | Desktop Experience |
| vCPUs | 2 |
| RAM | 4096 MB |
| Virtual Disk | 60 GB |
| Disk Allocation | Dynamically allocated |
| Hypervisor | Oracle VirtualBox |
| Network | VirtualBox Internal Network: Toyworks-LAN |

### Configuration Rationale
- **2 vCPUs:** Sufficient for a small lab running Active Directory Domain Services and DNS.
- **4 GB RAM:** Provides memory for Windows Server while leaving resources available for the Ubuntu host.
- **60 GB dynamic disk:** Provides room for Windows, updates, logs, and lab activities without immediately consuming the entire allocated capacity on the host.
- **Desktop Experience:** Provides a graphical interface while learning Windows Server administration. PowerShell will also be used for administrative tasks.
