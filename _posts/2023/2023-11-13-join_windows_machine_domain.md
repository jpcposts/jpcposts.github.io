---
title: Join Windows Machine to Domain
date: 2023-11-13 01:00:00 -0500
categories: [active_directory, windows, windows_server]
tags: [active_directory, windows, windows_server]
---

![install_ad_ds0](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds0.png)


Joining a Windows machine to a domain is an essential step in integrating it into an Active Directory (AD) environment. This process ensures that the machine can authenticate users against the domain and access network resources. In this guide, we will explore two methods to join a Windows machine to a domain: using the GUI (Graphical User Interface) and PowerShell commands.


## Join Windows Machine to Domain via GUI

Log into the machine as a local administrator

Change DNS Settings to point to the Domain Controller

- Right click on `Settings`
- Click `Network Connections`
- Click `Ethernet`

![join_domain_gui0](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui0.png)
![join_domain_gui1](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui1.png)


Add the IP address of the domain controller in the `Preferred DNS` box, click `Save`

![join_domain_gui2](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui2.png)


Right click on Windows icon and select `System`, then Click `Domain or workgroup` link next to `Related links` section. You will be prompted for admin rights.

![join_domain_gui3](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui3.png)

In the `Computer Name` tab, select the `Change` button

![join_domain_gui4](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui4.png)


Check the `Domain` box and enter the domain information. Click `OK`

![join_domain_gui5](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui5.png)


Domain admin credentials are required.

![join_domain_gui6](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui6.png)

After successful authentication, a welcome message is displayed. Restart the machine.

![join_domain_gui7](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui7.png)
![join_domain_gui8](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui8.png)
![join_domain_gui9](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui9.png)

You may now authentication with any domain user. Click on `Other user` and authentication with a domain user account.

![join_domain_gui10](/assets/img/posts/2023/join_windows_machine_domain/join_domain_gui10.png)

<br>

## Join Windows Machine to Domain via Powershell

Login as a user who has local admin rights and launch powershell as admin

Display network interfaces
```powershell
Get-NetIPInterface -AddressFamily IPv4
```

![join_domain_powershell0](/assets/img/posts/2023/join_windows_machine_domain/join_domain_powershell0.png)


Change DNS setting to refer to AD DS domain controller
```powershell
Set-DnsClientServerAddress -InterfaceIndex 7 -ServerAddresses “192.168.1.113” -PassThru
```

![join_domain_powershell1](/assets/img/posts/2023/join_windows_machine_domain/join_domain_powershell1.png)

Join to the domain. 
- For `username` add the correct domain user
- For `userpassword` add the correct password for that user
```powershell
Add-Computer -DomainName “jpc.net” -Credential (New-Object PSCredential “username”, (ConvertTo-SecureString -AsPlainText “userpassword” -Force))
```

Restart the computer
```powershell
Restart-Computer -Force
```

After restarting, verify to logon as a domain user

![join_domain_powershell2](/assets/img/posts/2023/join_windows_machine_domain/join_domain_powershell2.png)

Make sure the domain information is registered correctly

![join_domain_powershell3](/assets/img/posts/2023/join_windows_machine_domain/join_domain_powershell3.png)



## Conclusion

Joining a Windows machine to a domain is a fundamental task when integrating Windows systems into an Active Directory environment. Whether you choose to use the GUI method or the PowerShell approach, ensure that your DNS settings are correct, and you have the necessary credentials.

The GUI method provides a user-friendly interface for domain joining and is recommended for users who prefer a graphical approach. On the other hand, the PowerShell method is ideal for automation or situations where you need to script the domain joining process.

Whichever method you choose, successfully joining a machine to a domain is an essential step in managing user accounts, security policies, and network resources in a Windows domain environment.

