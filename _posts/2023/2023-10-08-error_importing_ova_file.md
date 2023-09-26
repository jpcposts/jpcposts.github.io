---
title: How to Fix the "Invalid OVF Checksum Algorithm" Error When Importing an OVA Package into vCenter
date: 2023-10-08 01:00:00 -0500
categories: [virtual machine, vcenter, virtualization]
tags: [virtual machine, vcenter, virtualization]
---

![How to Fix the "Invalid OVF Checksum Algorithm" Error When Importing an OVA Package into vCenter](/assets/img/posts/2023/error_importing_ova_file/error_importing_ova_file1.png)


If you've encountered the error message "The provided manifest file is invalid: invalid ovf checksum algorithm: sha 256" while trying to import an OVA package into vCenter or vSphere, don't worry; we've got you covered. This error typically occurs due to compatibility issues between the OVA package and the virtualization platform. Here's a step-by-step guide to help you resolve this issue.

![How to Fix the "Invalid OVF Checksum Algorithm" Error When Importing an OVA Package into vCenter](/assets/img/posts/2023/error_importing_ova_file/error_importing_ova_file2.png)


## Resolution:

To resolve this error, we'll use VirtualBox as an intermediary to import and then re-export the OVA package using the "Open Virtualization 1.0" format, which is more compatible with vCenter and vSphere.

### Step 1: Download and Install VirtualBox and Microsoft Visual C++ Redistributable Packages

- Start by downloading and installing VirtualBox from the official website: [Downloads – Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads).
- Additionally, download and install the required Microsoft Visual C++ Redistributable packages. You can find the latest supported packages on the [Microsoft Learn website](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-160).

### Step 2: Import the OVA File into VirtualBox

- Launch VirtualBox once it's installed.
- Navigate to the "File" menu and select "Import Appliance."
- Click the folder icon and choose the OVA file that you previously couldn't import into vCenter.
- Follow the import wizard's instructions to complete the process.

### Step 3: Export the VM Using the "Open Virtualization 1.0" Format

- In VirtualBox, select the imported VM from the list.
- Go to the "Tools" menu and choose "Export."
- Select the VM you want to export and click "Next."
- Choose the "Open Virtualization 1.0" format from the options.
- Follow the export wizard's prompts to complete the export process. This may take a few minutes, so be patient and look for a status indicator.

### Step 4: Import the New OVA File into vCenter/vSphere

- Log in to your vCenter.
- Select the ESXi host where you want to deploy the OVF template.
- Right-click on the ESXi host and choose "Deploy a virtual machine from OVF or OVA file."
- Click "Choose Files" and upload the newly created OVA file.
- Select the compute resource and click "Next."
- Review the details and click "Next."
- Accept the license agreement.
- Choose a datastore for the new VM and click "Next."
- Configure the network settings and click "Next."
- Review the summary and click "Next."

Congratulations! You've now successfully imported the OVA file that previously had compatibility issues with vCenter and vSphere environments. This workaround using VirtualBox as an intermediary should allow you to work with the OVA package seamlessly.








