---
title: Setting up a Proxmox Node on a Physical Server
date: 2023-06-24 01:00:00 -0500
categories: [proxmox, hypervisor]
tags: [proxmox, hypervisor]
---

![Setting up a Proxmox Node on a Physical Server](/assets/img/posts/2023/proxmox_create_node/proxmox_create_node1.jpg)

Proxmox Virtual Environment (Proxmox VE) is a powerful, open-source server virtualization platform. It allows you to run virtual machines (VMs) and containers on a single physical server. Setting up a Proxmox node on your hardware is the first step to harnessing the capabilities of this versatile platform. In this guide, we'll walk you through the process step by step.

## Prerequisites

Before you begin, make sure you have the following:

- A physical server or machine with hardware virtualization support (Intel VT-x or AMD-V).
- A bootable USB drive with the Proxmox installation ISO. You can find the Proxmox ISO [here](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso), and you can use a tool like [balenaEtcher](https://blog.johnsonpremier.net/bootable_usb_balenaetcher/) to create the bootable USB drive.
- Basic knowledge of working in a Linux terminal.

## Step 1: Boot from the Proxmox ISO

- Insert the bootable USB drive into your server.
- Power on the server and boot from the USB drive. You may need to change the boot order in your server's BIOS settings to prioritize the USB drive.
- The Proxmox VE installation menu will appear. Select "Install Proxmox VE" and press Enter.

## Step 2: Proxmox Installation

- Choose your language and keyboard layout.
- Accept the license agreement.
- Select the target hard drive where you want to install Proxmox. Be cautious, as this process will erase all data on the selected drive.
- Set a strong password for the root user.
- Configure your network settings, including IP address, subnet mask, gateway, and DNS servers.
- Confirm your settings, and the installation process will begin. This may take a few minutes.
- Once the installation is complete, remove the USB drive and press Enter to reboot the server.

## Step 3: Accessing the Proxmox Web Interface

- After the server reboots, open a web browser on a computer connected to the same network.
- Enter the IP address you configured during installation in the browser's address bar, followed by the default port 8006. `IPADDRESS:8006` The Proxmox web interface should appear.
- Log in with the root username and the password you set during installation.

## Step 4: Configure Storage

- Before creating VMs or containers, you'll need to configure storage. Click on "Datacenter" in the left sidebar and then select the "Storage" tab.
- Click the "Add" button to add new storage. You can choose from various storage options, including local storage, NFS, or iSCSI, depending on your requirements.
- Follow the prompts to configure and add your chosen storage type.

## Step 5: Create Virtual Machines

- Now that your Proxmox node is set up and storage is configured, you can start creating virtual machines or containers. Click on "Create VM" or "Create CT" in the left sidebar to begin.
- Follow the wizard to configure the VM or container settings, including hardware resources, network settings, and the ISO image for installation.
- Start the VM or container, and you're all set!


![Setting up a Proxmox Node on a Physical Server](/assets/img/posts/2023/proxmox_create_node/proxmox_create_node2.jpg)

Congratulations! You've successfully set up a Proxmox node on your physical server. You can now create and manage virtual machines and containers to run various workloads and applications.

Proxmox VE offers a powerful and flexible virtualization platform suitable for both small-scale deployments and enterprise-level solutions. Explore its features and capabilities to make the most of your virtualization needs.

For more in-depth Proxmox guides and tips, stay tuned to our blog!

📝 For more information about Proxmox, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).



