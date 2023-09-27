---
title: Building a Backup Server with Amanda on RHEL 9
date: 2023-09-26 01:00:00 -0500
categories: [backup, rhel, server]
tags: [backup, rhel, server]
---

![Building a Backup Server with Amanda on RHEL 9](/assets/img/posts/2023/building_amanda_backup_server/building_amanda_backup_server.png)


Data is the lifeblood of any organization, and ensuring its safety is paramount. To achieve robust data protection, building a backup server is a wise decision. In this guide, we'll explore how to set up a backup server using the Amanda backup software on Red Hat Enterprise Linux 9 (RHEL 9). Amanda is a reliable open-source backup solution that simplifies data backup and recovery processes.

## Prerequisites

Before we begin, ensure you have the following:

- A server running Red Hat Enterprise Linux 9 (RHEL 9).
- Sufficient storage capacity for your backups.
- Root or sudo access to the server.

## Step 1: Install Amanda

To install Amanda on RHEL 9, open a terminal and run the following commands:

```bash
sudo dnf install amanda-server amanda-client -y
```
This command installs the Amanda server and client components.

Amanda is pulled from the `EPEL repository`, so ensure that this is configured first. If you need EPEL configured on a RHEL machine that is conencted to the internet, run the following comamnd : 

```bash
sudo dnf install \
https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm
```

## Step 2: Configure Amanda

**Edit Amanda Configuration:** Open the Amanda configuration file for editing. The main configuration file is usually located at /etc/amanda/your-config-name.conf. You can use a text editor like nano or vim.

```bash
sudo nano /etc/amanda/DailySet1/amanda.conf
```

**Set Configuration Options:** Customize the configuration file according to your backup requirements. Ensure you specify the following:
- org (organization name).
- mailto (email address to receive backup reports).
- dumpuser (the user under which Amanda runs backups).
- dumpcycle (defines how frequently backups are run).
- tapecycle (defines how frequently tapes are recycled).

Save your changes and exit the editor.

**Set Up Disklist:** Create a disklist file that specifies the systems and directories you want to back up. This file is typically located at /etc/amanda/DailySet1/disklist. Add entries in the following format:

```bash
<system-name> <disk-device> [<mount-point>] [<dump-type>] 
```
For Example:

```bash
myserver /mnt/data comp-root-tar
```

Save the disklist file.

## Step 3: Configure Amanda Tape Storage

Amanda uses tapes or disk files for storing backups. You can configure tape storage or use disk files as storage.

### For Tape Storage:

Ensure your tape drive is properly connected and recognized by RHEL 9.
Edit the Amanda amanda.conf file to specify the tape device:

```bash
tapedev "your-tape-device"
```

Save your changes.

### For Disk File Storage:

Create a directory to store backups:

```bash
sudo mkdir /backup
```

Configure Amanda to use this directory as the backup storage. Edit the amanda.conf file:

```bash
infofile "/var/lib/amanda/<your-config-name>/curinfo"  # Use a directory on your backup storage disk.
logdir   "/var/lib/amanda/<your-config-name>/log"      # Use a directory on your backup storage disk.
indexdir "/var/lib/amanda/<your-config-name>/index"    # Use a directory on your backup storage disk.
tapelist "/var/lib/amanda/<your-config-name>/tapelist"  # Use a directory on your backup storage disk.
```

Save your changes.


## Step 4: Create Amanda User and Group

Amanda should run under its own user and group. Run these commands:

```bash
sudo groupadd -r amanda
sudo useradd -g amanda -r amanda
```

## Step 5: Initialize Amanda

Initialize Amanda to set up the necessary directories and files:

```bash
sudo amcheck <your-config-name>
```

## Step 6: Run Your First Backup

Now, you're ready to perform your first backup:

```bash
sudo amdump <your-config-name>
```

## Conclusion

Setting up a backup server with Amanda on RHEL 9 is a valuable investment in data protection. With this robust backup solution in place, your organization can rest assured that critical data is safe and recoverable in case of unexpected events. Regularly monitor and maintain your backup server to ensure the integrity and availability of your backups.



📝 For more information about Amanda Backups, visit the [official Amanda Network Backup page](https://amanda.org).












