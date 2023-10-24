---
title: Enabling Desktop Icons in RHEL 8
date: 2023-11-04 01:00:00 -0500
categories: [linux, rhel8]
tags: [linux, rhel8]
---

![Enabling Desktop Icons in RHEL 8](/assets/img/posts/2023/enabling_desktop_icons/enabling_desktop_icons.png)


Red Hat Enterprise Linux 8 (RHEL 8) offers a powerful and flexible desktop environment with GNOME as its default shell. However, by default, RHEL 8 doesn't display desktop icons. If you're used to having icons on your desktop and want to enable them, you can do so using the `desktop-icons` extension for the GNOME Shell. This extension provides the capability to add and manage icons on your GNOME desktop, making it more convenient for daily tasks.



## Prerequisites

### 1. Confirm that the AppStream Repository is Enabled:

To check if the AppStream repository is enabled on your system, you can use the following command:

```bash
sudo dnf repolist
```

*Look for the `rhel-8-for-x86_64-appstream-rpms` repository in the list. If it's enabled, you should see it in the list of repositories.*

### 2. Enable AppStream Repository:

If you don't see the AppStream repository in the list or if it's disabled, you can enable it by running the following command:

```bash
sudo subscription-manager repos --enable=rhel-8-for-x86_64-appstream-rpms
```

*This command will enable the `rhel-8-for-x86_64-appstream-rpms` repository, which contains the AppStream packages.*

### 3. Refresh Your Repository Cache:

After enabling or modifying repositories, it's a good practice to refresh the repository cache using the following command:

```bash
sudo dnf clean all
```

### 4. Verify the Configuration of the Repository:

You can run the dnf repolist command again to verify that the AppStream repository is enabled and listed.

```bash
sudo dnf repolist
```

Ensure that the `rhel-8-for-x86_64-appstream-rpms` repository is visible and is `enabled.`

By following these steps, you can ensure that the AppStream repository is configured and enabled on your Red Hat Enterprise Linux 8 system. This repository provides the desktop-icons GNOME tweaks and a wide range of software packages and application modules to extend the functionality of your RHEL 8 system.

<br>

# Below is A Guide to Enable Desktop Icons in RHEL 8:

<br>

## Step 1: Install GNOME Tweaks

Before enabling desktop icons, you'll need to have GNOME Tweaks installed on your system. GNOME Tweaks is a utility that allows you to customize various aspects of the GNOME desktop environment, including extensions.

If you haven't already installed GNOME Tweaks, you can easily do so using the terminal with the following command:

```bash
sudo dnf install gnome-tweaks
```

## Step 2: Enable the Desktop Icons Extension

Once GNOME Tweaks is installed, you can launch it from the Applications menu or by running the command gnome-tweaks in the terminal.

- Open GNOME Tweaks.
- In the left sidebar, click on `Extensions`
- Look for the `Desktop Icons` extension and toggle the switch to enable it.

With the `desktop-icons` extension enabled, your GNOME desktop will now display icons, providing you with easy access to your files and shortcuts. You can right-click on the desktop to add, remove, or manage these icons as needed.


## Step 3: Managing Desktop Icons

With the `desktop-icons` extension enabled, you have the flexibility to manage your desktop icons as per your preferences. You can:

- **Add Icons:** Easily add icons to your desktop by right-clicking on the desktop and selecting `New Document` or `New Folder.`
- **Remove Icons:** If you want to tidy up your desktop, right-click on the icon and select "Move to Trash."
- **Rearrange Icons:** Click and drag icons to arrange them to your liking. This helps you keep your desktop organized.
- **Create Shortcuts:** You can create shortcuts to your favorite applications or files by simply right-clicking on the icon and selecting "Add to Desktop."

By enabling desktop icons, you can streamline your workflow and have quick access to the files and applications you need.


# Conclusion

Enabling desktop icons on RHEL 8 using the `desktop-icons` extension is a straightforward process and can significantly enhance your desktop experience. Whether you prefer quick access to files, a clutter-free workspace, or easy management of shortcuts, desktop icons can make your daily tasks more convenient. By following these simple steps, you can customize your RHEL 8 desktop to suit your preferences and boost your productivity. Enjoy the added convenience and flexibility of desktop icons on your Red Hat Enterprise Linux 8 machine.