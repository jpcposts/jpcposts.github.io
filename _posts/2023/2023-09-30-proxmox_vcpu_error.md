---
title: How to Resolve "TASK ERROR - MAX 2 vcpus allowed per VM on this node" in Proxmox
date: 2023-09-30 01:00:00 -0500
categories: [proxmox, virtualization, troubleshooting]
tags: [proxmox, virtualization, troubleshooting]
---

![How to Resolve "TASK ERROR - MAX 2 vcpus allowed per VM on this node](/assets/img/posts/2023/proxmox_vcpu_error/proxmox_vcpu_error1.jpg)


If you're encountering the error message "TASK ERROR: MAX 2 vcpus allowed per VM on this node" in Proxmox while trying to start a virtual machine (VM), don't worry; this issue has a straightforward solution. This error typically occurs when you try to assign more than two virtual CPUs (vCPUs) to a VM on a node that has a limitation of two vCPUs per VM. In this guide, we'll walk you through the steps to resolve this error and get your VM up and running.

## Understanding the Error

Proxmox imposes a limit of two vCPUs per VM by default on certain node types, which can be a sensible constraint for resource management. However, there are scenarios where you may need to assign more vCPUs to a VM, such as running CPU-intensive applications. If you attempt to allocate more than two vCPUs on such a node, you'll encounter the "TASK ERROR: MAX 2 vcpus allowed per VM on this node" error as shown below.

![How to Resolve "TASK ERROR - MAX 2 vcpus allowed per VM on this node](/assets/img/posts/2023/proxmox_vcpu_error/proxmox_vcpu_error2.png)


## Resolution Steps


### Adjust the VM Configuration

Modify your VM's configuration to use two or fewer vCPUs. Here's how:

- **Log in to the Proxmox web interface** using your credentials.
- **Navigate to your VM** that's encountering the error.
- **Click on the "Hardware" tab** to access the VM's hardware settings.
- **Adjust the "Sockets" and "Cores" values** to use a maximum of two vCPUs under the `Processors` section.
- **Click "Apply"** to save the changes.
- **Start the VM** again.

This adjustment will align your VM with the node's vCPU limitation, allowing it to start without errors.

## Conclusion

Encountering the "TASK ERROR: MAX 2 vcpus allowed per VM on this node" error in Proxmox is a common issue that can be resolved adjusting your VM's configuration. Choose the solution that best fits your hardware and resource requirements to ensure smooth VM operation on your Proxmox cluster.


📝 For more information about Proxmox, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).


📝 Visit this [proxmox forum](https://forum.proxmox.com/threads/how-to-know-how-many-vcpu-i-can-use-for-creating-vms.117832/) and this [proxmox forum](https://forum.proxmox.com/threads/sockets-vs-cores-vs-vcpus.56339/) for more details about sockets, cores, vcpus, and much more.









