---
title: Migrating a Proxmox VM from One Node to Another
date: 2023-09-23 01:00:00 -0500
categories: [proxmox, hypervisor]
tags: [proxmox, hypervisor]
---

![Migrating a Proxmox VM from One Node to Another](/assets/img/posts/2023/proxmox_vm_migration/proxmox_vm_migration.jpg)


Migrating a virtual machine (VM) between Proxmox nodes is a common task in managing virtualized environments. Whether you want to balance resource usage or perform maintenance on a node, Proxmox makes VM migration straightforward. In this guide, we'll walk through the steps to migrate a VM from one Proxmox node to another.

## Prerequisites

Before we begin, ensure you have the following in place:

- **Two Proxmox Nodes**: Source node (the one currently hosting the VM) and target node (the destination for the VM).
- **Shared Storage**: Both nodes should have access to the same shared storage (e.g., NFS, Ceph) where VM disks are stored. This ensures seamless migration.

## Migrate a Proxmox VM

### Step 1: Log in to the Proxmox Web Interface

- Open your web browser and log in to the Proxmox web interface of the source node.

### Step 2: Select the VM to Migrate

- In the Proxmox web interface, navigate to the **Datacenter** section.
- Click on the down arrow to view the available nodes.
- Select the source node where your VM is currently running.

### Step 3: Start the Migration Wizard

- Click on the VM you want to migrate to select it.
- Right click on the VM and then select **Migrate**.

### Step 4: Configure Migration Settings

- In the Migration Wizard, you'll see the following options:
   - **Target Node**: Choose the target node where you want to migrate the VM.
   - **Storage**: Select the storage on the target node where you want to store the VM's disk files.
   - **Full Clone**: If you want to create a full clone of the VM on the target node, check this option.
   - **Online**: To perform an online migration (VM remains running during migration), ensure this option is checked.
   - **With local storage**: Enable this option if the target node uses local storage.
   - **Tunnel**: Configure the migration tunnel settings if required (usually for remote migrations).

- Review and confirm your settings.

### Step 5: Start the Migration

- Click the **Start** button to begin the migration process.

### Step 6: Monitor the Migration Progress

- You can monitor the migration progress in the Proxmox web interface. The status will change from "migrate" to "running" once the migration is complete.

### Step 7: Verify the Migration

- Log in to the Proxmox web interface of the target node.
- Navigate to the **Datacenter** section.
- Click on the **Nodes** tab and select the target node.
- You should see the migrated VM listed in the VM list.

### Step 8: Post-Migration Checks

- After migrating the VM, perform any necessary post-migration checks to ensure it operates as expected on the new node.

Congratulations! You've successfully migrated a Proxmox VM from one node to another. This process allows you to optimize your resource utilization and maintain high availability for your virtualized environment.

Remember that proper planning, shared storage, and network connectivity between nodes are essential for smooth VM migrations in Proxmox.


📝 For more information about Proxmox, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).
