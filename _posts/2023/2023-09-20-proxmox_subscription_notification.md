---
title: Removing the Proxmox Subscription Notice Popup
date: 2023-09-20 01:00:00 -0500
categories: [proxmox, hypervisor]
tags: [proxmox, hypervisor]
---

![Removing the Proxmox Subscription Notice Popup](/assets/img/posts/2023/proxmox_subscription_notification/proxmox_subscription_notification1.jpg)


When managing your Proxmox server, you might encounter the "You do not have a valid subscription for this server" popup message upon login. While subscriptions provide valuable benefits, you may want to suppress this message for various reasons. In this guide, we'll show you how to remove the Proxmox subscription notice.


![Removing the Proxmox Subscription Notice Popup](/assets/img/posts/2023/proxmox_subscription_notification/proxmox_subscription_notification2.png)


Please note that this modification is intended for versions 5.1 and newer of Proxmox and has been tested up to the version mentioned in the title. Keep in mind that when you update your Proxmox server and the update includes the `proxmox-widget-toolkit` package, you will need to repeat this process.

**Disclaimer**: Removing this notice may have implications for your Proxmox server. Proceed with caution, and make sure you understand the potential consequences.

## Manual Steps to Remove the Subscription Notice

### Step 1: Access the Server

You can perform these steps by SSH-ing into your Proxmox server or using the node console through the PVE web interface.

### Step 2: Change to the Working Directory

Navigate to the `proxmox-widget-toolkit` directory using the following command:

```bash
cd /usr/share/javascript/proxmox-widget-toolkit
```

### Step 3: Create a Backup

Before making any changes, it's essential to create a backup of the proxmoxlib.js file:

```bash
cp proxmoxlib.js proxmoxlib.js.bak
```

### Step 4: Edit the File

Edit the proxmoxlib.js file. You can use your preferred text editor; for example:

```bash
nano proxmoxlib.js
```

### Step 5: Locate the Code

Inside the proxmoxlib.js file, locate the following code. You can use `CTRL + W` in nano to search for "No valid subscription":

```java
Ext.Msg.show({
  title: gettext('No valid subscription'),
```

### Step 6: Replace the Code

Replace the entire code block with the word `void`, and add `//` like the below line :

```java
void({ //Ext.Msg.show({
  title: gettext('No valid subscription'),
```

### Step 7: Restart the Proxmox Web Service

After making the change, restart the Proxmox web service:

```bash
systemctl restart pveproxy.service
```

Also, make sure to clear your browser cache. Depending on your browser, you may need to open a new tab or restart the browser.


### If you ever need to revert the changes, you have three options:

**1st Option - Manual Edit:** Manually edit the proxmoxlib.js file to undo the changes you made.

**2nd Option - Restore Backup:** Restore the backup file you created from the proxmox-widget-toolkit directory:

```bash
mv proxmoxlib.js.bak proxmoxlib.js
```

**3rd Option - Reinstall Package:** Reinstall the proxmox-widget-toolkit package from the repository:

```bash
apt-get install --reinstall proxmox-widget-toolkit
```

Please exercise caution when modifying system files, and consider the implications of removing the subscription notice. Always ensure you have a backup and understand how this change may affect your Proxmox environment.

Remember that subscriptions support the development of Proxmox, so consider obtaining one to access additional features and support.


📝 For more information about Proxmox, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).
