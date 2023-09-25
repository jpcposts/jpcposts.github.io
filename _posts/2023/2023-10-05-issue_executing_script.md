---
title: How to Fix '\r' - Command Not Found Issue in RHEL
date: 2023-10-05 01:00:00 -0500
categories: [linux, rhel]
tags: [linux, rhel]
---

![How to Fix '\r': Command Not Found Issue in RHEL](/assets/img/posts/2023/issue_executing_script/issue_executing_script.jpg)


If you're encountering the '\r': command not found error while trying to execute a script in RHEL that was originally created on a Windows machine, you're not alone. This issue arises due to the differences in line endings between Windows and Linux systems. Windows uses '\r\n' (carriage return and line feed) as line endings in text files, while Linux systems like RHEL use '\n' (line feed) only.

When you attempt to run a script with Windows line endings on a Linux system, it interprets the '\r' (carriage return) character as part of the command, leading to the error message. Fortunately, this issue is easily fixable, and here's how to do it:

## Method 1: Using dos2unix

The simplest way to resolve this problem is by using the `dos2unix` command, which converts text files with Windows line endings to Unix/Linux line endings. If it's not already installed, you can install it with the following command:

```bash
sudo dnf install dos2unix -y
```

Once installed, navigate to the directory where your script is located and run dos2unix followed by the name of your script:

```bash
dos2unix your_script.sh
```

This command will replace the Windows line endings with Linux line endings, effectively fixing the '\r': command not found issue.

## Method 2: Using sed

Alternatively, you can use the sed command to remove the '\r' characters from your script. Here's the command:

```bash
sed -i 's/\r$//' your_script.sh
```

This command instructs sed to edit the file in-place (-i) and substitute (s/) all '\r' characters at the end of lines ($) with nothing (''). It essentially removes the carriage return characters from the file.

After applying either of these methods, you should be able to run your script without encountering the '\r': command not found error.

By following these straightforward steps, you can seamlessly execute Windows-created scripts on your RHEL system without any issues related to line endings.







