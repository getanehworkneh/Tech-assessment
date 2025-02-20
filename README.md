# Tech Assessment - Integration Engineer

## Summary

This repository provides a structured approach to solving the Tech Assessment for Integration Engineer. Each task is broken down into clear steps, with explanations of the underlying concepts and thought processes. 

## Task 1: Network Debugging

### Approach

Intermittent form submission failures can be tricky to diagnose because they may not occur consistently. The goal is to identify patterns or errors in the network requests and JavaScript execution. Here's the step-by-step process:

#### Open Developer Tools
- Use the browser's developer tools to monitor network activity and console logs.
- Shortcut: **F12** or **Ctrl + Shift + I (Windows) / Cmd + Option + I (Mac).**

#### Check HTTP Request and Response Status Codes
- Reproduce the issue by submitting the form.
- Look for failed requests (**4xx or 5xx status codes**) in the Network tab.
- Intermittent failures may alternate between success (**2xx**) and failure (**4xx/5xx**).

#### Inspect Headers
- Verify that the **Content-Type** header matches the data being sent.
- Check response headers for errors or warnings.

#### Debug Potential CORS Issues
- Look for CORS errors in the Console tab.
- Ensure the server includes **Access-Control-Allow-Origin** in the response headers.

#### Use the Console Tab
- Check for JavaScript errors or warnings.
- Add `console.log()` statements to trace the form submission flow.

### Thought Process
- Focus on identifying patterns in network requests and responses.
- Use the Console tab to catch JavaScript errors that might not be obvious.
- CORS issues are common in modern web applications, so they should be checked early.

## Task 2: Network Configuration - Subnet Calculation (192.168.0.0/24)

### Approach
Subnetting is essential for efficient IP address allocation and network management. The task involves dividing the **192.168.0.0/24** network into smaller subnets.

#### Usable IP Addresses in 192.168.0.0/24
- **Subnet mask /24** allows **256 IP addresses**.
- Subtract **2** (network and broadcast addresses) to get **254 usable IPs**.

#### Dividing into Two Subnets (/25)
- Each **/25 subnet** has **128 IPs**, with **126 usable IPs**.
- **Subnet 1:** 192.168.0.0/25 (usable IPs: **192.168.0.1 to 192.168.0.126**).
- **Subnet 2:** 192.168.0.128/25 (usable IPs: **192.168.0.129 to 192.168.0.254**).

### Thought Process
- Subnetting improves network performance and security.
- Calculating usable IPs ensures efficient allocation.
- Understanding **subnet masks** and **CIDR notation** is critical for network configuration.

## Task 3: File Management

### Approach
File management involves archiving, transferring, and extracting files securely. Here's the process:

#### Archive and Compress a Directory
- Use `tar` to create a compressed archive:
  `tar -czvf logs.tar.gz logs/`

#### Securely Transfer to a Remote Server
- Use `scp` or `rsync` for secure file transfer:
  `scp logs.tar.gz user@remote_server:/path/to/destination/`
  or
  `rsync -avz --progress logs.tar.gz user@remote_server:/path/to/destination/`

#### Uncompress and Extract on the Remote Server
- SSH into the remote server and extract the archive:
  `tar -xzvf /path/to/destination/logs.tar.gz -C /path/to/customerlogs/`

#### Resuming an Interrupted Transfer
- Use `rsync --partial` to resume interrupted transfers.

### Thought Process
- Archiving and compressing files reduces transfer size and time.
- Secure file transfer protocols like `scp` and `rsync` ensure data integrity.
- Resumable transfers are crucial for large files or unstable connections.

## Task 4: HTTPS Configuration

### Approach
Configuring HTTPS to support only **TLS 1.2** ensures secure communication. Here's how to do it in Nginx:

#### Edit Nginx Configuration
- Locate the configuration file (e.g., `/etc/nginx/nginx.conf`).
- Add the following directives:
  ```nginx
  ssl_protocols TLSv1.2;
  ssl_ciphers 'ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256';
  ```

#### Reload Nginx
- Test the configuration and reload Nginx:
  ```
  sudo nginx -t
  sudo systemctl reload nginx
  ```

#### Verify Configuration
- Use tools like **SSL Labs** or `openssl` to verify TLS 1.2 support:
  `openssl s_client -connect yourdomain.com:443 -tls1_2`

### Thought Process
- Disabling older protocols (**SSLv2, SSLv3, TLS 1.0, TLS 1.1**) improves security.
- Strong cipher suites ensure robust encryption.
- Testing the configuration ensures compliance with modern standards.

## Task 5: Troubleshooting Error Messages

### Approach
The error `curl: (7) Failed to connect to remote_server.com port 443: No route to host` indicates a connectivity issue. Here's how to troubleshoot:

#### Check Network Connectivity
- Ping the host:
  `ping remote_server.com`

#### Verify DNS Resolution
- Use `nslookup` or `dig` to resolve the domain:
  `nslookup remote_server.com`

#### Check Firewall Rules
- Ensure port **443** is allowed:
  `sudo ufw allow 443`

#### Test Port Connectivity
- Use `telnet` or `nc` to check if port **443** is open:
  `telnet remote_server.com 443`

#### Verify Server Status
- Ensure the server is running and listening on port **443**.

### Thought Process
- Start with basic connectivity checks (**ping, DNS resolution**).
- Firewall rules and server status are common culprits.
- Use tools like `telnet` to diagnose port-level issues.
