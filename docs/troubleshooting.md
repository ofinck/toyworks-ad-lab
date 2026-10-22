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

## Issue: 2
**Date:** 10-22-2026 **System:** TW-DC01 **Component:** DNS Server/DNS name resolution

### Symptoms
Running nslookup TW-DC01.ad.toyworks.test results in a DNS request timeout. The output identifies the DNS server as UnKnown when using the IPv6 loopback address (::1). When explicitly querying the IPv4 loopback address (127.0.0.1), the server is identified as localhost, but the query still times out. Despite the timeouts, both queries eventually return the expected hostname and IPv4 address.

### Initial investigation
- Confirmed that the DNS Server service is running.
- Confirmed that the system has DNS listeners on port 53 for UDP and TCP.
- Successfully resolved TW-DC01.ad.toyworks.test using Resolve-DnsName against 127.0.0.1.
- Tested nslookup against the IPv4 and IPv6 loopback addresses. Both returned the expected DNS record but also reported request timeouts.
- DNS listening-address configuration returns the correct IP address for TW-DC01.
- DNS server event log does not list any obvious errors.
- nslookup debug output reported the DNS request timeout before displaying the expected A record
- Compared DNS resolution using Resolve-DnsName and nslookup requesting the same A record from the domain controller's IPv4 address. Resolve-DnsName returned the expected IPv4 address and nslookup reported a DNS request timeout but afterwards returned the expected IPv4 address.

### Root Cause
Undetermined. The available evidence confirms that the DNS server can resolve the domain controller's A record, but it does not explain why nslookup reports a timeout. Further investigation is required to identify the cause.
### Status
**Deferred.** Normal DNS resolution has been resolved using Resolve-DnsName. The intermittent or command specific timeout behavior remains unexplained. No configuration changes were made because the investigation has not identified a a confirmed cause.



