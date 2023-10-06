---
title: RHEL 9 Networking Changes
date: 2023-10-29 01:00:00 -0500
categories: [rhel, networking]
tags: [rhel, networking]
---

![RHEL 9 Networking Changes](/assets/img/posts/2023/rhel9_networking_changes/rhel9_networking_changes1.png)



**Red Hat Enterprise Linux 9 (RHEL 9)** introduces significant changes in the realm of networking configuration. One of the most notable changes is the shift from traditional ifcfg-files to keyfiles. These alterations streamline network configuration and management, offering more flexibility and simplicity.

In this guide, we will explore the changes in RHEL 9 networking and understand how to work with keyfiles for configuring network interfaces.

## The Evolution of Network Configuration

For many years, Linux distributions, including RHEL, relied on ifcfg-files for network configuration. These files were located in `/etc/sysconfig/network-scripts/` and were used to define network interfaces and their settings. While ifcfg-files served their purpose, they had certain limitations, especially in complex networking environments.

RHEL 9 brings a fundamental change to the network configuration paradigm by introducing keyfiles. Keyfiles are YAML-formatted configuration files that offer several advantages over the traditional ifcfg-files.

## Benefits of Keyfiles

### 1. Simplicity and Clarity

Keyfiles are human-readable and use a structured YAML format. This simplicity makes it easier to understand and modify network configurations.

### 2. Flexibility

Keyfiles support more flexible configurations. They can define multiple addresses, routes, and rules for a single network interface, allowing for complex setups without duplicating files.

### 3. Consistency

Keyfiles provide a consistent format for all network configuration, simplifying administration and troubleshooting.

### 4. NetworkManager Integration

Keyfiles are fully integrated with NetworkManager, the default network management tool in RHEL 9. This integration enhances network configuration, especially for desktop and laptop users.

## Working with Keyfiles

Let's explore how to work with keyfiles for network configuration:

### Create a Keyfile

This should already be created in your RHEL9 configuration, however, this is an example. To create a keyfile, navigate to the `/etc/NetworkManager/system-connections/` directory and create a new file with a `<name>.nmconnection` naming convention. For example:

```bash
/etc/NetworkManager/system-connections/ens192.nmconnection
```

### How to Modify Interface Settings

Whether you opt to continue using ifcfg-rh files (though it's not recommended) or embrace key files, altering interface settings such as IP addresses can be achieved in two ways:

#### Tool-Based:

 Utilize graphical tools like nm-connection-editor or the nmcli command-line tool. One notable advantage is that these tools validate your commands' syntax, ensuring accuracy. For instance, you can refer to the man nmcli for helpful examples like:

```bash
nmcli con mod enp2s0 ipv4.addr "10.0.0.x/24"
nmcli con down enp2s0
nmcli con up enp2s0
```

#### File-Based:

Alternatively, you can use a text editor to modify the key file located in /etc/NetworkManager/system-connections or the ifcfg-rh file found in /etc/sysconfig/network-connections. After making the changes, you should notify NetworkManager of the updates. Here's an example:

```bash
vi /etc/NetworkManager/system-connections/<name>.nmconnection
nmcli connection load /etc/NetworkManager/system-connections/<name>.nmconnection
nmcli connection up /etc/NetworkManager/system-connections/<name>.nmconnection
```
The `nmcli connection load [..]` command reloads a specific NetworkManager profile. Alternatively, you can use `nmcli connection reload` command to reload all profiles or `nmcli general reload` to refresh settings system-wide. The latter acts like sending a signal hangup (SIGHUP) to NetworkManager.

While the `ifcfg-` and `key file` formats do not have the same syntax, they mostly represent similar data about the interface configuration. Below is a comparison of both formats, which was pulled from the [RedHat Site](https://www.redhat.com/rhdc/managed-files/rhel-9-networking-changes-image1.png).


![RHEL 9 Networking Changes](/assets/img/posts/2023/rhel9_networking_changes/rhel9_networking_changes2.png)


### Why make the change?

In the past, managing interface configurations on Linux involved navigating various locations depending on the distribution: Debian and its derivatives relied on `/etc/network/interfaces`, while CentOS and similar distros favored `/etc/sysconfig/network-scripts`, among others. However, with an increasing number of distributions adopting NetworkManager, keyfiles in `/etc/NetworkManager/system-connections` have emerged as the new central hub for network connections on Linux.

This transformation made its debut in Fedora 33 and has now found its way into RHEL 9. Major releases such as RHEL 9 serve as the ideal platform for implementing substantial changes like this, even if they might disrupt existing scripts and workflows. Considering RHEL's strategy to offer a decade of minor releases, it's a **wise move** to acquaint yourself with this evolution and begin integrating it into your projects, this change is here to stay.

## Conclusion

RHEL 9's transition from ifcfg-files to keyfiles marks a significant improvement in network configuration. Keyfiles offer simplicity, flexibility, consistency, and NetworkManager integration, making network management more efficient and user-friendly.

As you migrate to RHEL 9, embrace the new keyfiles for network configuration. They represent a positive shift toward modernizing and streamlining network administration in your Linux environment.


📝 For more information about RHEL9 Networking, visit the [RHEL9 Configuring and managing networking documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/configuring_and_managing_networking/index).