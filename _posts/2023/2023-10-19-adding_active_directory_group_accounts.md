---
title: Adding Active Directory Group Accounts 
date: 2023-10-19 01:00:00 -0500
categories: [active_directory, windows, windows_server]
tags: [active_directory, windows, windows_server]
---

![install_ad_ds0](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds0.png)


Adding group accounts to Active Directory is a vital task that helps in effective user management and access control. This guide explores two methods for adding Active Directory group accounts: using the GUI (Graphical User Interface) and PowerShell commands.


## Add Active Directory Group Accounts via GUI

Launch `Active Directory Users and Computers`

Right click on `Users` , then click on `New` and select `Group`

![add_group_gui0](/assets/img/posts/2023/adding_active_directory_group_accounts/add_group_gui0.png)

 
Create a name for the group, then leave the Group scope default as `Global` and the Group type default as `Security`. Then press `OK`

![add_group_gui1](/assets/img/posts/2023/adding_active_directory_group_accounts/add_group_gui1.png)

Now when you navigate back to domain.name/Users you can see the newly created `testgroup` group.

![add_group_gui2](/assets/img/posts/2023/adding_active_directory_group_accounts/add_group_gui2.png)

Now, to add a user to the group, you may do the following : 
- Right click on the group and select `Properties`
- Select the [Member tab] and select the `Add` button
- Input the username for this group, click `Check Names` then click `OK`

![add_group_gui3](/assets/img/posts/2023/adding_active_directory_group_accounts/add_group_gui3.png)


## Add Active Directory Group Accounts via PowerShell

Launch PowerShell as admin

Show the current list of AD groups
```powershell
Get-ADGroup -Filter * | Format-Table DistinguishedName
```

![add_group_powershell0](/assets/img/posts/2023/adding_active_directory_group_accounts/add_group_powershell0.png)

Add a new group named `testgroup2`
```powershell
New-ADGroup testgroup2 `
-GroupScope Global `
-GroupCategory Security `
-Description “Testing Group 2”
```

Verify the creation of the group
```powershell
Get-ADGroup -Identity testgroup2
```

![add_group_powershell1](/assets/img/posts/2023/adding_active_directory_group_accounts/add_group_powershell1.png)


Delete a user from a group

```powershell
Remove-ADGroupMember -Identity testgroup2 -Members jamison.johnson
```

Delete a group

```powershell
Remove-ADGroup -Identity testgroup2johnson
```

## Conclusion

Adding group accounts to Active Directory is crucial for managing access control within your organization. The method you choose—GUI or PowerShell—depends on your specific requirements. The GUI provides a straightforward and visual way to create groups, while PowerShell offers powerful automation for more complex scenarios.

By following the steps provided in this guide, you can efficiently create and manage group accounts in your Active Directory domain.