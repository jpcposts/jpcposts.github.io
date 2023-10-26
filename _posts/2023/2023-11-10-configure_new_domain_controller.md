---
title: Configuring a New Domain Controller
date: 2023-11-10 01:00:00 -0500
categories: [active_directory, windows, windows_server]
tags: [active_directory, windows, windows_server]
---

![install_ad_ds0](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds0.png)


Configuring a new domain controller on Windows Server 2022 is a fundamental task when setting up an Active Directory environment. This process involves using Server Manager to promote the server to a domain controller, specifying domain details, functional levels, and other configurations. Once completed, your server will become a domain controller, allowing it to manage and control your network domain. This step-by-step guide will walk you through the process of configuring a new domain controller in Windows Server 2022.


## Configure the New Domain Controller

Launch Server Manager

Click `AD DS` / Click the flag icon on the top and select `Promote this server to a domain controller` link

![configure_dc0](/assets/img/posts/2023/configure_new_domain_controller/configure_dc0.png)

Check the box `Add a new forest` and input your desired domain name information in the `Root domain name` box. Click `Next`

![configure_dc1](/assets/img/posts/2023/configure_new_domain_controller/configure_dc1.png)


Select `Forest functional level` and `Domain functional level`, the latest available version currently is `Windows Server 2016`, select this option. Set a safe/secure password for Directory Services Restore Mode (DSRM). Click `Next`

![configure_dc2](/assets/img/posts/2023/configure_new_domain_controller/configure_dc2.png)


In the `DNS Options` section, leave all defaults, click `Next`

![configure_dc3](/assets/img/posts/2023/configure_new_domain_controller/configure_dc3.png)


Ensure a `NetBIOS domain name`, then click `Next`

![configure_dc4](/assets/img/posts/2023/configure_new_domain_controller/configure_dc4.png)


Leave the `Paths` section as default, click `Next`

![configure_dc5](/assets/img/posts/2023/configure_new_domain_controller/configure_dc5.png)


Review your configured settings and click `Next`

![configure_dc6](/assets/img/posts/2023/configure_new_domain_controller/configure_dc6.png)


Click `Install`, after the install finishes, the system will reboot automatically.

![configure_dc7](/assets/img/posts/2023/configure_new_domain_controller/configure_dc7.png)


After reboot, the logon named will be changed to `Domain name\` `User name`

![configure_dc8](/assets/img/posts/2023/configure_new_domain_controller/configure_dc8.png)


## Conclusion

Configuring a new domain controller on Windows Server 2022 is a critical step in establishing and managing your network's Active Directory. This process is essential for controlling user access, security policies, and other network-related configurations. By following these steps, you can efficiently set up a domain controller, laying the foundation for a secure and well-organized network infrastructure.

