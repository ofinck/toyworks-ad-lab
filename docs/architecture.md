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
  The virtual machines will use an isolated virtual network to prevent experimental configurations from affecting the host's normal network.

  Exact addressing and VirtualBox network settings will be documented during implementation.

## Design Decisions
  Configuration decisions will be documented as the lab develops, including the reasons for each decision and any alternatives considered.
