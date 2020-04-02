# EXPRESSCLUSTER Hardening Guide

This guide describes how to hardening configuration of EXPRESSCLUSTER from security perspective.

## Firewall

Configuring firewall so that open minimum ports.

1. Close all the port.
2. Open ICMP (ping) communication.
3. Open the port which the system uses for fundamental services. (e.g. NTP)
4. Open the port which the application uses.
5. Open the port which ECX uses. Find the below manual describing port number for ECX.

	[Getting Started Guide - P.87 Communication port number](https://www.nec.com/en/global/prod/expresscluster/en/support/Windows/W40_SG_EN_02.pdf#page=87)

## HTTPS

Configuring ECX WebManager to use HTTPS.

1. Get and install [OpenSSL](https://slproweb.com/download/Win64OpenSSL_Light-1_0_2p.exe) to all the member node in the cluster. Win32 OpenSSL is distributed at [here](https://slproweb.com/products/Win32OpenSSL.html).

2. Create the certificate file for WebManager (https) server. For more details, please refer to https://github.com/EXPRESSCLUSTER/Tips/blob/master/HTTPSconfiguration.md.

3. Configure the cluster according to [Reference Guide - P.161 WebManager tab](https://www.nec.com/en/global/prod/expresscluster/en/support/Windows/W40_RG_EN_02.pdf#page=161)

## Password

- ECX is ran as one of Windows services and the executing user name is "SYSTEM" which is built-in user account.
There is no effect for ECX to change the password of "Administrator".

- ECX configuration can have "user account" information for application execution in "application resource". When the password of the user account is changed on the operating system, ECX configuration also need to be changed to mutch the new password.

	[Reference Guide - P.605 Understanding application resources](https://www.nec.com/en/global/prod/expresscluster/en/support/Windows/W40_RG_EN_02.pdf#page=605) - P.610 Exec User Account (and around)

- ECX WebManager can have password for two purpose
  - prohibiting password free access
  - restricting access to reference mode only

  [Reference Guide - P.163 Control connection by using password](https://www.nec.com/en/global/prod/expresscluster/en/support/Windows/W40_RG_EN_02.pdf#page=163)
  
## Disk Encryption

#### BitLocker
ECX of Data Mirroring configuration can be used with BitLocker.
Note that Shared Disk configuration cannot.
For more detail, please refer to [BitLocker](https://github.com/EXPRESSCLUSTER/BitLocker) page.

## Network Encryption

Configure L2TP over IPsec between member nodes in the cluster, then configure interconnect and mirror-connect of the cluster to use the L2 tunnel.

----
2018.11.06 1st issue	Miyamoto Kazuyuki
