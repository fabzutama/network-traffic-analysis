# Network Traffic Analysis using tcpdump
This project demonstrates how to capture and analyze network traffic using `tcpdump and wireshark` on Kali Linux.
### Network Traffic Analysis Report

**Capture File**: `traffic_capture.pcap`  
**Capture Time**: October 20, 2024, 03:51:20 - 03:52:00  
**Tools Used**: tcpdump

#### Key Observations

1. **Router Solicitation (IPv6)**:
   - **Time**: 03:51:20.782500
   - **Details**: A router solicitation message was sent from `fe80::e24b:a6ff:fe19:a3c8` to `ip6-allrouters`. This is part of the Neighbor Discovery Protocol (NDP) in IPv6, where a device requests router information.

2. **Multicast DNS Service Discovery (SSDP - UDP)**:
   - **Time**: Multiple entries (03:51:23.842369 to 03:51:24.617397)
   - **Details**: The host `192.168.18.1` sent multiple SSDP requests to `239.255.255.250`, indicating attempts to discover services on the local network.

3. **Neighbor Discovery (IPv6)**:
   - **Time**: 03:51:46.921541
   - **Details**: The capture includes several neighbor solicitation and advertisement messages:
     - `fe80::1` solicited the link-layer address of `fe80::6bee:61cb:9c59:8f81`.
     - The corresponding advertisement confirms this link-layer address.

4. **ARP Requests**:
   - **Time**: 03:51:46.924519
   - **Details**: The host `192.168.18.1` attempted to resolve `192.168.18.77` using ARP (Address Resolution Protocol), indicating it was looking for the MAC address associated with this IP.

5. **NetBIOS Name Service (UDP)**:
   - **Time**: 03:51:51.090453, 03:51:51.842830, and 03:51:52.593528
   - **Details**: Multiple broadcasts from `192.168.18.77` to the NetBIOS broadcast address `192.168.18.255` for name resolution, typical for Windows devices in local networks.

#### Summary

- The capture demonstrates typical local network activity, including neighbor discovery (both IPv4 and IPv6), service discovery via SSDP, and NetBIOS name resolution.
- The presence of both ARP and IPv6 NDP suggests that the network supports both IP versions, which is standard in modern networks.
- No anomalies or malicious activities were detected in the captured traffic, as it aligns with expected behavior for devices communicating within a local subnet.

#### Recommendations

- Continue monitoring for unusual patterns, especially in multicast and service discovery traffic, to enhance security.
- Regularly review network configurations to ensure optimal performance and adherence to security best practices, especially in mixed IP environments.

## Project Structure
- `captures/`: Captures Directory

This directory contains network traffic captures in `.pcap` format.

## Files

- **`traffic_capture.pcap`**: This file includes captured network traffic data taken from the network at a specific time. The capture contains various protocols, including ICMPv6, ARP, and UDP.

## Analysis

The traffic capture can be analyzed using tools like Wireshark or the provided scripts in the `scripts/` directory.
- `scripts/`:  Scripts Directory

This directory contains Bash scripts to automate network traffic capture and analysis.

## Scripts

- **`start_capture.sh`**: Starts capturing network traffic.
- **`stop_capture.sh`**: Stops the ongoing traffic capture.
- **`analyze_capture.sh`**: Analyzes a specified `.pcap` file and generates a report.

## Usage

Ensure that i have the necessary permissions to run these scripts. i may need to execute them with `sudo` depending on your system's configuration.

Example usage:
```bash
bash start_capture.sh output.pcap
bash stop_capture.sh
bash analyze_capture.sh output.pcap analysis_report.md
- `docs/`: ### Scripts

The `scripts/` directory contains the following scripts:
- **`start_capture.sh`**: 
  - Starts the network traffic capture using tcpdump.
  - Usage: `bash start_capture.sh [output_file]`
  
- **`stop_capture.sh`**:
  - Stops the ongoing traffic capture.
  - Usage: `bash stop_capture.sh`

- **`analyze_capture.sh`**:
  - Analyzes the captured traffic and generates a report.
  - Usage: `bash analyze_capture.sh [input_file] [output_report]`

### Documentation

The `docs/` directory contains the analysis report and related diagrams:
- **`analysis_report.md`**: This report summarizes the analysis of the captured traffic, highlighting key findings and potential issues.
- **`network_traffic_diagram.png`**: Visual representation of the traffic flows in the network, aiding in understanding the interactions between devices.

## Requirements

- **tcpdump**: For capturing network traffic.
- **Wireshark/tshark**: For analyzing `.pcap` files.
- **Bash**: For executing scripts.


