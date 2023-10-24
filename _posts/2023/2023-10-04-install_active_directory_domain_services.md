---
title: Install Active Directory Domain Services
date: 2023-10-04 01:00:00 -0500
categories: [active_directory, windows, windows_server]
tags: [active_directory, windows, windows_server]
---

![install_ad_ds0](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds0.png)


Active Directory Domain Services (AD DS) is a core component of Microsoft Windows Server that enables centralized management of users, groups, computers, and other network resources within an organization. It plays a pivotal role in creating and maintaining a secure, organized, and efficient network environment. Installing AD DS on a Windows Server 2022 is a crucial step in establishing a domain controller that can provide essential authentication, authorization, and directory services to users and devices in your network.


## Prerequisites
Before you embark on installing Active Directory Domain Services (AD DS) on a Windows Server 2022, ensure you have met these prerequisites:

**A Fresh Installation of Windows Server 2022:** Make sure your server is installed with a fresh copy of Windows Server 2022. This guide assumes a clean slate with no existing roles or configurations.

**Static IP Address:** Configure a static IP address for your server. Dynamic IP addresses are not recommended for domain controllers.

**Server Naming:** Choose an appropriate and unique name for your server. This name will be used as the server's hostname within your domain.

**Administrator Credentials:** You should have local administrator credentials for your Windows Server 2022 machine.

**Network Configuration:** Ensure your server has access to the internet and can resolve DNS queries. You may need to set up DNS server addresses, or if you're planning to use this server as a DNS server, configure it accordingly.

**Windows Updates:** Before you start, ensure that your server has the latest Windows updates and patches installed.

**A FQDN (Fully Qualified Domain Name):** Decide on a domain name you wish to use, e.g., `jpc.net`. It should be unique on your network.

**DNS Resolution:** You should have a working DNS server or DNS service. This can be installed on the same server but should be properly configured.

**Static DNS Record:** Create a static DNS record for the future domain controller in your DNS server or service.

**Domain Controller Site:** Plan your Active Directory Sites and Services structure to ensure efficient replication and authentication within your network.


## Install Active Directory Domain Services (AD DS)

Launch Server Manager
Click `Manage` / `Add Roles and Features`

![install_ad_ds1](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds1.png)

Click `Next`

![install_ad_ds2](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds2.png)

Select `Role-based or feature based installation` then click `Install`

![install_ad_ds3](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds3.png)

Select the host in which you would like to add AD DS / Click `Next`

![install_ad_ds4](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds4.png)

Check the box `Active Directory Domain Services`

![install_ad_ds5](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds5.png)

Additional features are requested to install AD DS. Click `Add Features`

![install_ad_ds6](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds6.png)

Click `Next`

![install_ad_ds7](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds7.png)

Click `Next`

![install_ad_ds8](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds8.png)

Click `Install`

![install_ad_ds9](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds9.png)

After the installation is finished click `close`

![install_ad_ds10](/assets/img/posts/2023/install_active_directory_domain_services/install_ad_ds10.png)

You have now successfully configured Active Directory Domain Servers (AD DS) on Windows Server 2022.


## Conclusion

Installing Active Directory Domain Services (AD DS) on a Windows Server 2022 is a fundamental step in setting up a secure and organized network environment. It empowers organizations to manage users, devices, and resources efficiently. By adhering to the prerequisites and following the installation process, you can establish a robust foundation for your network, enhancing security, scalability, and centralized management. With a well-configured AD DS, you can implement advanced features like group policies, user authentication, and domain-wide security policies, providing a seamless experience for network users and administrators alike.

