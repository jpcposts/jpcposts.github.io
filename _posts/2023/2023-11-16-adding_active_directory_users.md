---
title: Adding Active Directory Users 
date: 2023-11-16 01:00:00 -0500
categories: [active_directory, windows, windows_server]
tags: [active_directory, windows, windows_server]
---

![install_ad_ds0](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds0.png)


Adding Active Directory Users to Active Directory is a vital task that helps in effective user management and access control. This guide explores two methods for adding Active Directory users: using the GUI (Graphical User Interface) and PowerShell commands.


## Add Active Directory Users via GUI

Launch Server Manager

Click `Tools` / `Active Directory users and Computers`

![add_user_gui0](/assets/img/posts/2023/add_active_directory_users/add_user_gui0.png)

Right click on `Users` on the left and select `New` / `User`

![add_user_gui1](/assets/img/posts/2023/add_active_directory_users/add_user_gui1.png)

Input username and logon for the new user. Click `Next`

![add_user_gui2](/assets/img/posts/2023/add_active_directory_users/add_user_gui2.png)

Set the initial password for the new User. Click `Next`

![add_user_gui3](/assets/img/posts/2023/add_active_directory_users/add_user_gui3.png)

Confirm the details, then click `Finish`

![add_user_gui4](/assets/img/posts/2023/add_active_directory_users/add_user_gui4.png)

A new user has now been added to the domain. This user can now log into any machine that is joined to the domain.

## Add Active Directory Users via Powershell

Launch PowerShell as admin

Show the current list of AD users

```powershell
Get-ADUser -Filter * | Format-Table DistingusihedName
```

![add_user_powershell0](/assets/img/posts/2023/add_active_directory_users/add_user_powershell0.png)

Add a new user, this user will be named `JPCuser`

![add_user_powershell1](/assets/img/posts/2023/add_active_directory_users/add_user_powershell1.png)

Verify the account creation

```powershell
Get-ADUser -Identity JPCuser
```

![add_user_powershell2](/assets/img/posts/2023/add_active_directory_users/add_user_powershell2.png)

### Additional PowerShell Commands

Reset an existing users password

```powershell
Set-ADAccountPassword -Identity JPCuser `
-NewPassword (ConvertTo-SecureString -AsPlainText “0qpvP45Y4DZm29t8” -Force) `
-Reset
```

![add_user_powershell3](/assets/img/posts/2023/add_active_directory_users/add_user_powershell3.png)

Delete a user account

```powershell
Remove-ADUser -Identity “CN=JPCuser,CN=Users,DC=JPC,DC=net”
```

**Select the `Yes to All` option.**

![add_user_powershell4](/assets/img/posts/2023/add_active_directory_users/add_user_powershell4.png)

## Conclusion

Adding users to Active Directory is a fundamental task for network administrators. Whether you choose the GUI or PowerShell method depends on your preferences and specific use cases. The GUI offers simplicity and visual guidance, while PowerShell is powerful for automation and bulk operations.

By following the steps provided in this guide, you can effectively add and manage user accounts in your Active Directory domain!
