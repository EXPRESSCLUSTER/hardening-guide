# EXPRESSCLUSTER Hardening Guide

This guide describes how to hardening configuration of EXPRESSCLUSTER from security perspective.

## Firewall

Configuring firewall so that open minimum ports.

1. Close all the port.
2. Open the port which the system uses for fundamental services. (e.g. NTP)
3. Open the port which the application uses.
4. Open the port which ECX uses. Find the below manual describing port number for ECX.

	[Getting Started Guide - P.87 Communication port number](https://www.nec.com/en/global/prod/expresscluster/en/support/Windows/W40_SG_EN_02.pdf#page=87)

## HTTPS

Configuring ECX Manager to use HTTPS.

1. Get and install [OpenSSL](https://slproweb.com/download/Win64OpenSSL_Light-1_0_2p.exe) to all the member node in the cluster. Win32 OpenSSL is distributed at [here](https://slproweb.com/products/Win32OpenSSL.html).

2. Create the certification file for WebManager (https) server.

3. Configure the cluster with referring [Reference Guide - P.161 WebManager tab](https://www.nec.com/en/global/prod/expresscluster/en/support/Windows/W40_RG_EN_02.pdf#page=161)

## Password

- ECX is ran as one of Windows services and the executing user name is "SYSTEM" which is built-in user.
There is no effect for ECX to change the password of "Administrator".

- ECX configuration can have "user account" information for application execution in "application resource". When the password of the user account is changed on the operating system, ECX configuration need to be changed according to the password change.

	[Reference Guide - P.605 Understanding application resources](https://www.nec.com/en/global/prod/expresscluster/en/support/Windows/W40_RG_EN_02.pdf#page=605) - P.610 Exec User Account (and around)

<!--
## Encrypting communication

Configure L2TP over IPsec between member nodes in the cluster, then configure interconnect and mirror-connect of the cluster to use the L2 tunnel.
-->

----
2018.11.06 1st issue	Miyamoto Kazuyuki