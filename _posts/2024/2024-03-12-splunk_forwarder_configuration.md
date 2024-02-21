---
title: Configuring Splunk Forwarder on RHEL 9
date: 2024-03-12 01:00:00 -0500
categories: [splunk, rhel, linux]
tags: [splunk, rhel, linux]
---

![Configuring Splunk Forwarder on RHEL 9](/assets/img/posts/2024/splunk_forwarder_configuration/splunk_forwarder_configuration.jpg)


## Introduction:

Splunk is a powerful platform for searching, monitoring, and analyzing machine-generated data, and deploying Splunk forwarders allows you to extend its capabilities to collect data from various sources. This blog post provides a step-by-step guide on configuring a Splunk forwarder on a RHEL 9 host, enabling you to forward log data to a centralized Splunk instance for analysis.

This post is an extension of my previous post about [Splunk Configuration Details](https://blog.johnsonpremier.net/splunk_configuration_details/).


## Prerequisites:

Before diving into the configuration process, ensure the following prerequisites are met:

### 1. **Splunk Instance**
   - Have a running Splunk instance to forward the data to.
   - Obtain the Splunk instance IP address or hostname.

### 2. **Splunk Forwarder Package**
   - Download the Splunk Universal Forwarder package compatible with RHEL 9 from the [official Splunk website](https://www.splunk.com/en_us/download/universal-forwarder.html ).


## Installation:

### 1. **Transfer the Splunk Forwarder Package**
   - Use a secure method (e.g., SCP) to transfer the Splunk Universal Forwarder package to your RHEL 9 host.

### 2. **Install Splunk Forwarder**
   - Navigate to the directory where the Splunk package is located.
   - Install Splunk Forwarder with the following commands:
     ```bash
     sudo rpm -i splunkforwarder-<version>-<build>.rpm
     ```

## Configuration:

### 1. **Access the Splunk Web Interface**
   - Open a web browser and access the Splunk Web Interface by entering the Splunk instance IP address or hostname and the default port (usually 8000).

### 2. **Login to Splunk Web**
   - Log in to the Splunk Web Interface using your credentials.

### 3. **Set Up Forwarding**
   - Navigate to **Settings > Forwarding and Receiving > Forwarding**.
   - Click on **Add New** to add a new forwarding configuration.
   - Enter the Splunk instance IP address or hostname and the receiving port.

### 4. **Configure Splunk Forwarder**
   - On the RHEL 9 host, navigate to the Splunk bin directory:
     ```bash
     cd /opt/splunkforwarder/bin
     ```
   - Configure the Splunk forwarder to send data to the specified Splunk instance:
     ```bash
     ./splunk add forward-server <Splunk_instance_IP>:<receiving_port>
     ```
   - Restart the Splunk forwarder:
     ```bash
     ./splunk restart
     ```

### 5. **Verify Configuration**
   - Return to the Splunk Web Interface.
   - Go to **Settings > Forwarding and Receiving > Forwarding** to verify that the RHEL 9 host appears as a connected forwarder.

## Testing:

To ensure that the Splunk forwarder is successfully sending data, you can perform the following test:

### 1. **Generate Log Data**
   - Generate some log data on the RHEL 9 host (e.g., by creating a new log file).

### 2. **Search in Splunk**
   - Access the Splunk Web Interface.
   - Go to the **Search & Reporting** app.
   - Search for the generated log data to verify its presence.

## Conclusion:

Configuring a Splunk forwarder on a RHEL 9 host allows you to efficiently collect and forward log data to a centralized Splunk instance. By following the steps outlined in this guide, you can seamlessly integrate your RHEL 9 host into the Splunk environment, enhancing your ability to monitor and analyze machine-generated data.




📝 For more information about the Splunk Forwarder, you can refer to the [Forwarder Manual](https://docs.splunk.com/Documentation/Forwarder/9.2.0/Forwarder/Abouttheuniversalforwarder).
