---
title: How to Install Proxmox VE on Bare Metal
date: 2023-10-01 01:00:00 -0500
categories: [proxmox, virtualization]
tags: [proxmox, virtualization]
---

![How to Install Proxmox VE on Bare Metal](/assets/img/posts/2023/proxmox_install_bare_metal/proxmox_install_bare_metal1.jpg)


Proxmox Virtual Environment (Proxmox VE) is a versatile open-source virtualization platform that combines Kernel-based Virtual Machine (KVM) for virtual machines (VMs) and Linux Containers (LXC) for lightweight container-based virtualization. Whether for server consolidation or building cloud infrastructure, Proxmox VE is an excellent choice. This guide walks you through installing Proxmox VE on a bare-metal server.

## Prerequisites

Before you begin, ensure you have the following:

- A dedicated server or bare-metal machine with compatible hardware.
- A bootable USB drive or DVD containing the Proxmox VE ISO image. Download the latest ISO from the [official Proxmox website](https://www.proxmox.com/en/downloads).
- You may use [rufus](https://rufus.ie/en/) or [balenaEtcher](https://etcher.balena.io) as options to create the bootable USB drive.
- Physical or remote access to the server for installation.

![How to Install Proxmox VE on Bare Metal](/assets/img/posts/2023/proxmox_install_bare_metal/proxmox_install_bare_metal2.png)



## Step 1: Boot from the Proxmox VE Installation Media

- Insert the bootable USB drive or DVD into the server's USB port or DVD drive.
- Power on or reboot the server.
- Access the BIOS or UEFI settings during the boot process to set the server to boot from the installation media. Consult your server's documentation for specific instructions.
- Save the changes and exit the BIOS or UEFI settings.
- The server will now boot from the Proxmox VE installation media.




## Step 2: Proxmox VE Installation Wizard

1. The Proxmox VE installation wizard appears once the server boots from the installation media.

2. Choose your preferred language and press Enter to continue.

3. Select "Install Proxmox VE" and press Enter.

## Step 3: Accept the License Agreement

1. Read and review the Proxmox VE license agreement.

2. If you agree to the terms, select "I accept the terms of the Proxmox Virtual Environment License Agreement" and press Enter.

## Step 4: Select Target Disk

1. The installer will detect the available storage devices on your server.

2. Choose the target disk where you want to install Proxmox VE. Be cautious, as this process will erase all data on the selected disk.

3. Highlight the desired disk and press Enter to continue.

## Step 5: Set a Password

1. Enter and confirm the root password for your Proxmox VE server. This password is essential for accessing the Proxmox web interface and performing administrative tasks.

2. Press Enter to proceed.

## Step 6: Network Configuration

1. Configure the network settings for your Proxmox VE server. You can choose between DHCP and manual configuration.

   - For DHCP: If your network provides DHCP, select "Use DHCP" and proceed to the next step.

   - For manual configuration: If you prefer to set static IP settings, select "Static address configuration" and enter the IP address, subnet mask, gateway, and DNS server information.

2. Press Enter to continue.

## Step 7: Confirm Installation

1. Review the installation summary, which displays the installation options you've selected.

2. If everything looks correct, select "Install" and press Enter.

## Step 8: Installation Progress

1. The Proxmox VE installation process will begin, and you can monitor the progress on the screen.

2. After installation, remove the installation media (USB drive or DVD) and press Enter to reboot the server.

## Step 9: Initial Configuration

1. After the server reboots, a login prompt will appear.

2. Log in using the root username and the password you set during the installation.

3. Proxmox VE is now installed on your bare-metal machine. Access the web-based management interface by opening a web browser and entering the following URL: `https://<your-server-ip>:8006`. Replace `<your-server-ip>` with the IP address you configured during the installation.

4. Log in with the root username and password to begin configuring and managing your Proxmox VE server.

Congratulations! You've successfully installed Proxmox VE on a bare-metal machine. You can now create virtual machines, containers, and manage your virtualization environment using the powerful Proxmox VE interface.

This guide has covered the installation process for Proxmox VE on a bare-metal server. Proxmox VE offers a feature-rich virtualization platform suitable for a wide range of applications, from hosting virtual machines to creating scalable cloud environments. Enjoy harnessing the power of Proxmox VE for your virtualization needs!
