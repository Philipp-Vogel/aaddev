---
title: Find AD/Exchange objects by any proxyAddress
description: Find AD/Exchange objects by any proxyAddress
categories: General
---
# Find AD/Exchange objects by any email address

Sometimes you want to search for objects in your Active Directory by email address, including secondary email addresses (proxyAddresses).
Note: These checks will not include the mail attribute.
Also they are not suited to check if an email address is available, as there might be other factors to consider, like another domain, etc.

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
The Exchange Powershell Cmdlets also search for secondary email addresses when using the -Identity parameter.
```powershell
Get-Recipient -Identity "firstname.lastname@company.com"
```
This will not include objects which have the value in their proxyAddresses but are not mail enabled (for whatever reason).
