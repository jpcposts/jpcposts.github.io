---
title: Join CentOS 9 / RHEL 9 to Active Directory Domain
date: 2023-10-20 01:00:00 -0500
categories: [centos, rhel, active_directory, windows_server, integration]
tags: [centos, rhel, active_directory, windows_server, integration]
---

![Join CentOS 9 / RHEL 9 to Active Directory Domain](/assets/img/posts/2023/join_centos_rhel_to_domain/join_centos_rhel_to_domain.jpg)


Before we begin, it's crucial to ensure that your CentOS 9 or RHEL 9 machine is configured to use the Windows Server 2022 domain controller's IP address as the DNS server. This ensures proper domain resolution and is a prerequisite for joining the machine to the Active Directory domain.

Integrating CentOS 9 or RHEL 9 with a Windows Server 2022 Active Directory domain can streamline user management and enhance security. In this step-by-step guide, we'll walk you through the process of joining a CentOS 9 or RHEL 9 machine to a Windows Server 2022 Active Directory domain. This enables you to use Active Directory credentials for authentication and access control on your Linux system.

**Note:** Before you begin, make sure you have administrative access to both the Linux machine and the Windows Server 2022 domain controller.

**Note:** We are going to use `ABC.NET` as the domain name and `abcdc01.abc.net` as hostname of the domain controller.

## Step 1: Gather Information

First, gather the necessary information:

- **Domain Name:** You'll need the name of your Active Directory domain (e.g., ABC.NET).
- **Administrator Username:** The username of an Active Directory administrator.
- **Administrator Password:** The password for the administrator account.
- **Domain Controller IP or Hostname:** The IP address or hostname of your Windows Server 2022 domain controller.

## Step 2: Install Required Packages

Open a terminal on your CentOS 9 or RHEL 9 machine and enter the following command to install the required packages:

```bash
sudo dnf install -y realmd sssd oddjob oddjob-mkhomedir adcli samba-common-tools krb5-workstation
```

This command installs the necessary tools for integrating with Active Directory.

## Step 3: Join the Domain

Use the `realm join` command to join the Linux machine to the Active Directory domain. Replace the placeholders with your domain information:

```bash
sudo realm join -U ADMIN_USERNAME@DOMAIN_NAME DC_HOSTNAME -v
```

For example:

```bash
sudo realm join -U Administrator@ABC.NET abcdc01.abc.net -v
```

You'll be prompted to enter the administrator password. This step establishes the connection to the Active Directory domain.


## Step 4: Configure krb5.conf

Create a custom krb5.conf file to configure Kerberos authentication. Use the following command to create and edit the file:

```bash
sudo nano /etc/krb5.conf
```

Paste the following configuration into the file, adjusting the realm and server details to match your environment:

```bash
[libdefaults]
    default_realm = ABC.NET
    dns_lookup_realm = true
    dns_lookup_kdc = true

[realms]
    YOUR_DOMAIN = {
        kdc = abcdc01.jpc.net
        admin_server = abcdc01.jpc.net
        default_domain = abcdc01.jpc.net
    }
```

Save and exit the text editor.

## Step 5: Restart the SSSD Service

Restart the System Security Services Daemon (SSSD) service to apply the changes:

```bash
sudo systemctl restart sssd
```

## Step 6: Test Login

You can now test the Active Directory integration by logging in with an AD username. Use the id command:

```bash
id YOUR_DOMAIN\\AD_USERNAME
```

Replace `YOUR_DOMAIN` with your Active Directory domain and `AD_USERNAME` with the username you want to test.

# Conclusion

Congratulations! You've successfully integrated your CentOS 9 or RHEL 9 machine with a Windows Server 2022 Active Directory domain. This allows you to use Active Directory credentials for authentication and access control on your Linux system, simplifying user management and enhancing security.

Remember that proper access control and security configurations are essential when integrating Linux systems with Active Directory. Always follow best practices to protect your environment.

- To login via the GUI on Linux machine do the following `ABC\user.name`
- To login via the terminal on Linux machine do the following `su JPC\\user.name`


### Below is a script that will help you join to the domain 


```bash
#
#
#
# - IN SUMMARY - This script does the following ...
#... prompts you for the domain name, e.g., ABC.NET, Domain Admin Username, Domain Admin Password, DC IP address ...
#... installs the required packages ...
#... joins the domain using realm ...
#... creates a custom /etc/krb5.conf file ...
#... restarts the sssd service and gives you the opportunitiy to log into AD with a AD user account for testing ...
#
# *** To login via the GUI on Linux machine do the following [ABC\user.name] ***
# *** To login via the terminal on Linux machine do the following [su ABC\\user.name] ***
#
#!/bin/bash

# Prompt the user for Active Directory domain name, Administrator username, and password
read -p "Enter the Active Directory domain name ex: ABC.NET: " DOMAIN_NAME
read -p "Enter the Administrator username: " ADMIN_USERNAME
read -s -p "Enter the Administrator password: " ADMIN_PASSWORD
echo  # Add a newline after password input

# Prompt the user for the IP address or hostname of the domain controller
read -p "Enter the IP address or hostname of the domain controller: " DC_HOSTNAME

# Install required packages
sudo dnf install -y realmd sssd oddjob oddjob-mkhomedir adcli samba-common-tools krb5-workstation

# Join the Active Directory domain using realm
sudo realm join -U $ADMIN_USERNAME@$DOMAIN_NAME $DC_HOSTNAME -v

# Create a custom krb5.conf file
cat <<EOL | sudo tee /etc/krb5.conf
[libdefaults]
    default_realm = ABC.NET
    dns_lookup_realm = true
    dns_lookup_kdc = true

[realms]
    JPC.NET = {
        kdc = abcdc01.jpc.net
        admin_server = abcdc01.jpc.net
        default_domain = abcdc01.jpc.net
    }
EOL

# Restart sssd service
sudo systemctl restart sssd

# Perform a test login using an AD username
read -p "Enter an AD username for testing: " AD_USERNAME
id $DOMAIN_NAME\\$AD_USERNAME

# Display completion message
echo "Configuration completed. You can now log in with AD credentials."
```