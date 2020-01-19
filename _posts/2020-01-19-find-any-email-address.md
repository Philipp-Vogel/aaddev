---
title: Find AD/Exchange objects by any proxyAddress
description: Find AD/Exchange objects by any proxyAddress
categories: General
---
# Find AD/Exchange objects by any email address

Sometime you want to search if an email address is used by anything, i.e. User, Contact, etc. and also want to include secondary email addresses.

## LDAP Query
```
(proxyAddresses=smtp:firstname.lastname@company.com)
```

## AD Powershell Cmdlets
```powershell
Get-ADObject -LDAPFilter "(proxyAddresses=smtp:firstname.lastname@company.com)"
```
```powershell
Get-ADObject -Filter "proxyAddresses -eq 'smtp:firstname.lastname@company.com'"
```

## Exchange Powershell
The Exchange Powershell Cmdlets also search for secondary E-Mail addresses when using the -Identity parameter
```powershell
Get-Recipient -Identity "firstname.lastname@company.com"
```
This will not include object which have the value in their proxyAddresses but are not mail enabled.
