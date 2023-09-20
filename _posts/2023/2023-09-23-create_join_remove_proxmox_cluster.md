---
title: Creating, Joining, and Removing Nodes in a Proxmox Cluster
date: 2023-09-23 01:00:00 -0500
categories: [proxmox, hypervisor]
tags: [proxmox, hypervisor]
---

![Creating, Joining, and Removing Nodes in a Proxmox Cluster](/assets/img/posts/2023/create_join_remove_proxmox_cluster./create_join_remove_proxmox_cluster1.jpg)



Proxmox VE offers powerful clustering capabilities, allowing you to build and manage a cluster of Proxmox nodes for enhanced performance and high availability. In this guide, we'll walk through the process of creating a Proxmox cluster, adding nodes to it, and removing a node when needed.

## Create a Proxmox Cluster

### Step 1: Create a Cluster (On `proxmox1`)

1. Navigate to **Datacenter** > **Cluster** > **Create Cluster** on `proxmox1`.
2. Provide a **Cluster Name**, such as `ABCcluster`.
3. Click the **Create** button to create the cluster.

### Step 2: Retrieve Join Information

1. In the newly created cluster, navigate to **Datacenter** > **Cluster** > **Create Cluster**.
2. Click the **Join Information** button.
3. Copy the provided cluster join information to your clipboard.

### Step 3: Join a Cluster (On `proxmox2` or Target Node)

1. On the node you want to add to the cluster (e.g., `proxmox2`), navigate to **Datacenter** > **Cluster** > **Create Cluster**.
2. Click the **Join Cluster** button.
3. Paste the copied cluster join information from `proxmox1`.
4. Enter the password for `proxmox1`.
5. Click **Join 'ABCcluster'** to initiate the joining process.

**Note**: The "Join Cluster" window may appear to hang, but the cluster join process typically takes only about 30-60 seconds. To confirm if `proxmox2` has successfully joined the cluster, check `proxmox1`.

![Creating, Joining, and Removing Nodes in a Proxmox Cluster](/assets/img/posts/2023/create_join_remove_proxmox_cluster./create_join_remove_proxmox_cluster2.jpg)


## Remove a Node from a Proxmox Cluster

### Step 1: Prepare the Node

Before removing a node from the cluster, make sure to:

- Delete or migrate any VMs that reside on the node you want to remove.

### Step 2: SSH into a Running Node

SSH into a working/running node within the cluster, such as `proxmox1`:

```bash
ssh root@IPADDRESS
```
### Step 3: Check Online Nodes

Check which nodes are currently online in the cluster:

```bash
pvecm nodes
```

### Step 4: Remove Offline Nodes

To remove the offline node, use the following command, replacing `node name` with the actual name of the node you want to remove:

```bash
pvecm delnode <node name>
```

After executing this command, you will need to refresh the Proxmox GUI to complete the removal process fully.

Managing a Proxmox cluster provides flexibility and resilience to your virtualization infrastructure. By following these steps, you can efficiently create, expand, and manage your Proxmox cluster as your needs evolve.


📝 For more information about Proxmox, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).
