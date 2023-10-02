---
title: Install and Use xfreerdp in RHEL 9
date: 2023-10-26 01:00:00 -0500
categories: [rhel, centos, rdp]
tags: [rhel, centos, rdp]
---

![Install and Use xfreerdp in RHEL 9](/assets/img/posts/2023/install_configure_xfreerdp/install_configure_xfreerdp.jpg)


**xfreerdp** is a powerful open-source remote desktop protocol (RDP) client that allows you to connect to Windows systems from a Linux command line. Whether you need to manage remote Windows servers or access your Windows desktop from a Linux machine, xfreerdp is a versatile solution.

In this guide, we'll walk you through the process of installing and using xfreerdp on a Red Hat Enterprise Linux 9 (RHEL 9) system.

## Prerequisites

Before you begin, ensure you have the following:

- A RHEL 9 system up and running.
- Access to a Windows system that you want to connect to.

## Step 1: Install xfreerdp

You can easily install xfreerdp using the `dnf` package manager. Open your terminal and run the following command:

```bash
sudo dnf install -y freerdp
```

This command will download and install the xfreerdp client on your RHEL 9 system.

## Step 2: Connect to a Windows System

Now that xfreerdp is installed, you can connect to a Windows system using the following syntax:


```bash
xfreerdp /u:<Username> /v:<IP_Address_or_Hostname>
```

- Replace `<Windows_IP_or_Hostname>` with the IP address or hostname of the Windows system you want to connect to.
- Replace `<Username>` with your Windows username.


## Step 4: Connect and Enjoy!

Once you've entered the appropriate command with your desired options, press Enter. xfreerdp will initiate the RDP connection to the Windows system, and you'll be prompted to enter your Windows password.

After a successful login, you'll have remote access to the Windows system from your RHEL 9 terminal. You can perform tasks, manage the remote desktop, and use applications just as if you were physically at the Windows machine.


## Conclusion

xfreerdp is a powerful tool that simplifies remote desktop access from your RHEL 9 system to Windows. With its various options, you can customize your remote sessions to suit your needs. Whether you're a system administrator managing remote servers or simply need occasional access to your Windows desktop, xfreerdp may be a great tool for you.

📝 For more information about xfreerdp, visit the [xfreerdp man page](https://linux.die.net/man/1/xfreerdp).