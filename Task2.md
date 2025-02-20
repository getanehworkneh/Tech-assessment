### Task2: Network Configuration - Subnet Calculation (192.168.0.0/24)

### ****1\. Usable IP Addresses in 192.168.0.0/24****

- **Subnet Mask**: /24 means the first 24 bits are for the network, leaving 8 bits for hosts.
- **Total IPs**: 2<sup>8</sup>\=256 addresses.
- **Usable IPs**: Subtract 2 (network and broadcast addresses).
  - **Usable IPs**: 256−2=254.

### ****2\. Dividing into Two Subnets (/25)****

- **New Subnet Mask**: /25 means the first 25 bits are for the network, leaving 7 bits for hosts.
- **Total IPs per Subnet**: 2<sup>7</sup>\=128 addresses.
- **Usable IPs per Subnet**: Subtract 2 (network and broadcast addresses).
  - **Usable IPs**: 128−2=126 in each network
- Subnet 1: 192.168.0.0/25 (126 usable IPs).
- Subnet 2: 192.168.0.128/25 (126 usable IPs)

**Note:** Each /25 subnet can accommodate **126 usable hosts**.

### ****3\. Brief Explanation of Subnet****

**Subnet calculation** is the process of dividing a larger IP network into smaller, more manageable sub-networks (subnets). It involves calculating:

- **Subnet Mask**: Determines the network and host portions of an IP address (e.g /24, /25).
- **Network Address**: Identifies each subnet.
- **Broadcast Address**: Used to communicate with all devices in a subnet.
- **Range of IPs**: Assignable IP addresses within each subnet.

**Benefits**:

-  Improves network performance by reducing congestion.
    - Enhances security by isolating traffic.
    - Efficiently allocates IP addresses.
