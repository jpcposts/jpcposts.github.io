---
title: Join CentOS 9 / RHEL 9 to Active Directory Domain
date: 2023-10-20 01:00:00 -0500
categories: [centos, rhel, active_directory, windows_server, integration]
tags: [centos, rhel, active_directory, windows_server, integration]
---

![Join CentOS 9 / RHEL 9 to Active Directory Domain](/assets/img/posts/2023/join_centos_rhel_to_domain/join_centos_rhel_to_domain.jpg)


<script src="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.js"></script>

<pre>
    <code id="code-block">
        sudo dnf install amanda-server amanda-client
    </code>
</pre>
<button class="btn" data-clipboard-target="#code-block">Copy</button>

<script>
    var clipboard = new ClipboardJS('.btn');
    clipboard.on('success', function(e) {
        e.clearSelection();
        alert('Code copied to clipboard!');
    });
</script>
