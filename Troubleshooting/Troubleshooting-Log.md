# **IT Operations Home Lab — Troubleshooting Log**

## **1. Overview**

This log records selected setup issues, troubleshooting activities, and resolutions encountered while building the virtual IT environment.



## **2. Virtualization Permissions**

Issue: Virtual Machine Manager initially encountered permission problems when connecting to the system libvirt service.

Troubleshooting and Resolution:

    * Checked libvirt access permissions.
    * Added the lab administrator account to the required libvirt group.
    * Rebooted the host.
    * Verified that Virtual Machine Manager could connect successfully.


Result: Virtual machine management became operational.



## **3. Windows Server Domain Controller DNS Validation**

Issue: The newly promoted domain controller required DNS verification to ensure that Active Directory domain records were available.

Troubleshooting and Resolution:

    * Used nslookup to query the domain name.
    * Checked the domain controller's fully qualified domain name.
    * Queried the LDAP domain controller SRV record.
    * Ran dcdiag /test:dns.


Result: Domain and domain controller DNS records resolved successfully, and the DNS diagnostic tests passed.



## **4. Windows Client DNS Configuration**

Issue: CLIENT01 initially received the virtual NAT gateway (192.168.122.1) as its DNS server through DHCP.

Troubleshooting and Resolution:

    * Identified DC01's static IPv4 address (192.168.122.10).
    * Changed CLIENT01's preferred DNS server to 192.168.122.10.
    * Kept automatic IP address assignment enabled.
    * Used nslookup to test domain and domain controller name resolution.


Result: CLIENT01 successfully resolved corp.test and DC01.corp.test.



## **5. Windows Client Domain Integration**

Issue: CLIENT01 needed to be joined to the Active Directory domain.

Troubleshooting and Resolution:

    * Verified that both virtual machines were connected to the same virtual network.
    * Confirmed that CLIENT01 could resolve the domain through DC01.
    * Joined CLIENT01 to corp.test using domain administrator credentials.
    * Restarted the client and signed in using a domain user account.


Result: Domain joining and domain user authentication succeeded.



## **6. Departmental File Access Verification**

Issue: Departmental users needed access to their own shared folders without accessing other departments' folders.

Troubleshooting and Resolution:

    * Configured departmental NTFS permissions using Active Directory security groups.
    * Tested access using IT, HR, and Finance domain accounts.
    * Attempted to access unauthorized departmental folders.
    * Verified access-denied responses.


Result: Each department account successfully accessed and created files in its authorized folder while access to other departments was denied.



## **7. Summary**

The project involved troubleshooting virtualization permissions, validating DNS configuration, configuring Windows client DNS, integrating a domain client, and verifying departmental file access controls.

These activities provided practical experience with basic IT infrastructure troubleshooting and Windows Server administration.




