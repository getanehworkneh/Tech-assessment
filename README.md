# Tech Assessment - Integration Engineer

## Summary

This repository provides a structured approach to solving the Tech Assessment for Integration Engineer. Each task is broken down into clear steps, with explanations of the underlying concepts and thought processes. 

I have provided the answers in two different formats: 
1) Each task answer is stored in a separate markdown file.
2) A Word document is also attached, containing all the answers in one place.

## Task 1: Network Debugging

### Approach

Intermittent form submission failures can be tricky to diagnose because they may not occur consistently. The goal is to identify patterns or errors in the network requests and JavaScript execution. 

### Thought Process
- Focus on identifying patterns in network requests and responses.
- Use the Console tab to catch JavaScript errors that might not be obvious.
- CORS issues are common in modern web applications, so they should be checked early.

## Task 2: Network Configuration - Subnet Calculation (192.168.0.0/24)

### Approach
Subnetting is essential for efficient IP address allocation and network management. The task involves dividing the **192.168.0.0/24** network into smaller subnets.

### Thought Process
- Subnetting improves network performance and security.
- Calculating usable IPs ensures efficient allocation.
- Understanding **subnet masks** and **CIDR notation** is critical for network configuration.

## Task 3: File Management

### Approach
File management involves archiving, transferring, and extracting files securely. 

### Thought Process
- Archiving and compressing files reduces transfer size and time.
- Secure file transfer protocols like `scp` and `rsync` ensure data integrity.
- Resumable transfers are crucial for large files or unstable connections.

## Task 4: HTTPS Configuration

### Approach
Configuring HTTPS to support only **TLS 1.2** ensures secure communication. 

### Thought Process
- Disabling older protocols (**SSLv2, SSLv3, TLS 1.0, TLS 1.1**) improves security.
- Strong cipher suites ensure robust encryption.
- Testing the configuration ensures compliance with modern standards.

## Task 5: Troubleshooting Error Messages

### Approach
The error `curl: (7) Failed to connect to remote_server.com port 443: No route to host` indicates a connectivity issue. 

### Thought Process
- Start with basic connectivity checks (**ping, DNS resolution**).
- Firewall rules and server status are common culprits.
- Use tools like `telnet` to diagnose port level issues.
