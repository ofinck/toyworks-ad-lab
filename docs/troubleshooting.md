# Troubleshooting Log

## Issue: 1
**Date:** 10-22-2026
**System:** TW-DC01
**Component:** Active Directory Domain Services (AD DS)

### Symptoms
During the Domain Controller promotion process, the deployment configuration wizard reported that the server TW-DC01 could not be contacted and that I had to verify that I supplied the correct DNS domain name.

### Initial Investigation
I reviewed the deployment configuration options and discovered that I had selected the option to add a domain controller to an existing domain rather than create a new Active Directory Forest.

This lab required a new Active Directory environment; the selected deployment option did not match the intended architecture.

### Root Cause
The incorrect deployment configuration was selected because I had not yet reviewed the distinction between creating a new forest and joining an existing domain.

### Resolution
1. Reviewed the options on the Deployment Configuration step of the Active Directory Domain Services Configuration Wizard.
2. Selected Add a new forest.
3. Entered the Root domain name.
4. Continued with the setup.

### Lessons learned
- Understand the purpose of configuration options before selecting them.
- Distinguish between creating a new Active Directory forest and adding a domain controller to an existing domain.
- Investigate error messages than than dismissing them or repeatedly retrying the same operation.
- Document the root cause and resolution so the issue can be diagnosed more efficiently in the future.

### Verification
Changing that option on the Deployment Configuration step allowed the wizard to continue and the domain controller promotion completed successfully.
