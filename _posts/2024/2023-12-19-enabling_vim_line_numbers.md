---
title: Enabling Line Numbers in Vim
date: 2023-12-19 01:00:00 -0500
categories: [linux, rhel, texteditor]
tags: [linux, rhel, texteditor]
---

![Enabling Line Numbers in Vim](/assets/img/posts/2024/enabling_vim_line_numbers/enabling_vim_line_numbers.png)


Vim, a powerful text editor, offers various customization options to suit users' preferences. Enabling line numbers can significantly aid navigation and reference while editing files. Here's how to set up Vim to display line numbers automatically.

## Enabling Line Numbers in Vim by Default

To have line numbers displayed by default in Vim, follow these steps:

### Editing the Vim Configuration File

**Locate the `/etc/vimrc` File:**
   ```bash
   sudo vim /etc/vimrc
   ```
**Add Line Number Configuration:**

Within the `/etc/vimrc` file, add the following line : 

   ```bash
    set nu
```
This command tells Vim to always display line numbers when you open files in the editor.
3. Save the changes and either restart Vim or open a new file to see line numbers enabled by default.


## Enabling Line Numbers Temporarily

You can also enable line numbers temporarily within the Vim editor by entering the following command within Vim:
  ```bash
    :set numbers
```

This command enables line numbers for the current session but doesn't save the setting for future use.


## Conclusion

Customizing Vim settings can significantly enhance your editing experience. Enabling line numbers by default is a practical configuration for better navigation and reference while working with multiple files. Utilize this method to streamline your workflow and increase productivity within the Vim text editor.


📝 For more information about Vi/Vim, refer to the  [Vi Man Page](https://linux.die.net/man/1/vi).


