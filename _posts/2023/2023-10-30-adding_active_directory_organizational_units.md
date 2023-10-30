---
title: Adding Active Directory Organization Units 
date: 2023-10-30 01:00:00 -0500
categories: [active_directory, windows, windows_server]
tags: [active_directory, windows, windows_server]
---

![install_ad_ds0](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds0.png)


Managing your Active Directory structure is essential for efficient user and resource management. This guide explains two methods for adding Active Directory Organizational Units (OUs): using the GUI (Graphical User Interface) and PowerShell commands.


## Add Active Directory Organizational Units (OUs) via GUI

Launch `Active Directory Users and Computers`

Right click on your domain name on the left tree and select `New` then `Organizational Unit`

![add_ou_gui0](/assets/img/posts/2023/adding_active_directory_organizational_units/add_ou_gui0.png)

Create a name for your OU, then click `OK`

![add_ou_gui1](/assets/img/posts/2023/adding_active_directory_organizational_units/add_ou_gui1.png)

A new OU called `Testing` is now created.

![add_ou_gui2](/assets/img/posts/2023/adding_active_directory_organizational_units/add_ou_gui2.png)

<br>

## Add Active Directory Organizational Units (OUs) via PowerShell

Launch PowerShell as Admin

Show the current list of AD groups
```powershell
Get-ADOrganizationalUnit -Filter * | Format-Table DistinguishedName
```

![add_ou_powershell0](/assets/img/posts/2023/adding_active_directory_organizational_units/add_ou_powershell0.png)

Add the `testing2` organizational unit
```powershell
New-ADOrganizationalUnit Testing2 `
-Path “DC=jpc,DC=net” `
-ProtectedFromAccidentalDeletion $True
```

![add_ou_powershell1](/assets/img/posts/2023/adding_active_directory_organizational_units/add_ou_powershell1.png)

Verify the creation of the Organizational Unit

![add_ou_powershell2](/assets/img/posts/2023/adding_active_directory_organizational_units/add_ou_powershell2.png)


## Conclusion

Active Directory Organizational Units (OUs) play a crucial role in organizing and managing your domain structure. Whether you opt for the GUI method for simplicity or PowerShell for automation, these tools enable you to create and manage OUs efficiently.

The choice between the two methods depends on your specific requirements and preferences. The GUI is intuitive and easy to use, while PowerShell provides greater flexibility for more complex OU management tasks.

By leveraging these methods, you can effectively structure your Active Directory for improved user and resource management.