---
title: How to Upload ISO Files to Proxmox Servers
date: 2023-07-11 01:00:00 -0500
categories: [proxmox, hypervisor]
tags: [proxmox, hypervisor]
---

![How to Upload ISO Files to Proxmox Servers](/assets/img/posts/2023/upload_iso_to_proxmox_server/upload_iso_to_proxmox_server.jpg)


Proxmox Virtual Environment (Proxmox VE) is a powerful platform for managing virtual machines and containers. One common task is uploading ISO files for virtual machine installations. However, some users encounter issues with the GUI-based upload process, where the upload gets stuck. In this guide, we'll show you an alternative method to upload ISO files to your Proxmox server.

## The GUI Upload Issue

The Proxmox web interface provides a convenient way to upload ISO files directly to the server. However, in some cases, users may encounter problems where the upload process gets stuck or takes an exceptionally long time. This can be frustrating, especially when you need to quickly deploy a new virtual machine. So we must find an alternative method.

## Using SCP or WinSCP

To bypass the GUI upload issue, you can use the command line or a graphical SCP (Secure Copy Protocol) client like WinSCP to transfer ISO files directly to the Proxmox server. Here's a step-by-step guide:

### Step 1: Prepare Your ISO File

Make sure you have the ISO file you want to upload to your Proxmox server stored on your local computer, USB drive, or network storage device.

### Step 2: Connect to Your Proxmox Server

#### Using SCP (Command Line):

Open a terminal or command prompt on your local computer.

Run the following command, replacing `<your-server-ip>` with your Proxmox server's IP address, `<your-username>` with your username, and `<your-iso-file.iso>` with the name of the ISO file:

```bash
scp -r /path/to/your/iso/<your-iso-file.iso> <your-username>@<your-server-ip>:/var/lib/vz/template/iso/
```

You will be prompted to enter your password.

#### Using WinSCP (Graphical):

Download and install WinSCP on your local computer if you haven't already.

Open WinSCP and configure a new session with your Proxmox server's IP address, username, and password.

Navigate to the /var/lib/vz/template/iso/ directory on the Proxmox server in the right-hand panel.

In the left-hand panel, browse to the location of your ISO file on your local computer.

Drag and drop the ISO file from your local directory to the remote directory on your Proxmox server.

### Step 3: Verify the Upload
Once the transfer is complete, you can verify that the ISO file is in the /var/lib/vz/template/iso/ directory on your Proxmox server.

You may also confirm in the GUI by going to `/proxmoxserver/local/`

# Conclusion
Uploading ISO files to your Proxmox server is a crucial task for setting up virtual machines. If you encounter issues with the GUI-based upload process, using SCP or WinSCP provides a reliable alternative. This method allows you to quickly and efficiently transfer ISO files directly to your Proxmox server's /var/lib/vz/template/iso/ directory, making them accessible for virtual machine installations.

By following these steps, you can overcome upload issues and streamline your virtualization workflow on Proxmox.


📝 For more information and detailed about proxmox, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).

