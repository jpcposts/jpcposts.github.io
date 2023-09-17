---
title: Backup and Restore Proxmox Configuration Files
date: 2023-09-17 01:00:00 -0500
categories: [proxmox, hypervisor, backup]
tags: [proxmox, hypervisor, backup]
---

![Backup and Restore Proxmox Configuration Files](/assets/img/posts/2023/backup_restore_proxmox_config/backup_restore_proxmox_config.jpg)


Proxmox Virtual Environment (Proxmox VE) is a robust platform for managing virtual machines and containers. Safeguarding your server's configuration is essential, and in this guide, we'll show you how to create backups of Proxmox configuration files and restore them when needed. In this example, we are saving the configuration backup files to a Synology NAS.

## Backup Proxmox Configuration Files

### SSH into Proxmox Server

First, establish an SSH connection to your Proxmox server.

```bash
ssh user@IPADDRESS
```

### Create a Backup Script

Create a directory to store your backup scripts and create a backup script file.

```bash
mkdir /opt/backup_scripts
touch /opt/backup_scripts/vzdump_backup.sh
```

### Add Backup Script

Open the vzdump_backup.sh script file with your preferred text editor (e.g., vi or nano) and add the following content:

```bash
#!/bin/bash

# Set backup directory
BACKUP_DIR=/mnt/pve/SynologyNAS/Backups/Proxmox

# Set backup file name
BACKUP_FILE=proxmox-config-backup-$(date +%Y-%m-%d-%H-%M-%S).tar.gz

# Create backup file
tar -czvf $BACKUP_DIR/$BACKUP_FILE /etc/pve /etc/vzdump.conf

# Print success message
echo "Proxmox server configuration files backed up to $BACKUP_DIR/$BACKUP_FILE"
```

### Execute the Backup Script
Give execute permissions to the script and then run it:

```bash
chmod +x /opt/backup_scripts/vzdump_backup.sh
bash /opt/backup_scripts/vzdump_backup.sh
```

Check the /mnt/pve/SynologyNAS/Backups/Proxmox directory to confirm that the backup was created successfully.



## Restore Proxmox Configuration Files

### Rebuild Proxmox Server

If you need to restore your Proxmox server configuration after rebuilding it from an ISO, follow these steps:

### Configure Connection to Synology
- Navigate to Datacenter > Storage > Add > SMB/CIFS.
   - ID = SynologyNAS
   - Server = 192.168.x.x (Synology NAS IP)
   - Username = ****
   - Password = ****
   - Share = data
   - Content = Select All
   - Click OK.


Now, SSH into the NEW Proxmox server and access the SynologyNAS via the /mnt/pve/SynologyNAS directory.


### Create Restore Script

Create a directory to store your restore scripts and create a restore script file.
```bash
mkdir /opt/backup_scripts
touch /opt/backup_scripts/vzdump_restore.sh
```

### Add Restore Script

Open the vzdump_restore.sh script file with your preferred text editor (e.g., vi or nano) and add the following content:

```bash
#!/bin/bash

# Set backup file path
BACKUP_FILE=/mnt/pve/SynologyNAS/Backups/Proxmox/proxmox-config-backup-FILE-NAME-HERE.tar.gz

# Extract backup file
tar -xzvf $BACKUP_FILE -C /

# Restart Proxmox services
systemctl restart pve-cluster.service
systemctl restart pvedaemon.service
systemctl restart pveproxy.service

# Print success message
echo "Proxmox server configuration files restored from $BACKUP_FILE"
```

### Execute the Restore Script
Give execute permissions to the script and then run it:

```bash
chmod +x /opt/backup_scripts/vzdump_restore.sh
bash /opt/backup_scripts/vzdump_restore.sh
```

This will extract and restore the Proxmox server configuration files from your specified backup file.

### Verify Configuration

Check to ensure that you can log into the NEW Proxmox server with the restored configurations.


## Conclusion

Backing up and restoring Proxmox configuration files is crucial for ensuring the integrity of your virtualization environment. With these steps, you can confidently create backups and recover your Proxmox server configurations when needed.

Always maintain up-to-date backups to minimize potential data loss and streamline the recovery process.


📝 For more information about Proxmox, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).
