
# Nmap Project

![Nmap Logo](https://bing.com/th?id=OIP.eyAOP7zitSh4qfuA3EJz6gAAAA)

## Overview
Nmap (Network Mapper) is a powerful open-source network scanning tool used for discovering hosts, services, and vulnerabilities on a network. It provides various scanning techniques and features to help you assess and secure your network.

## Features
1. **Types of Scanning**:
    - **TCP Connect Scans (-sT)**: Initiates a TCP 3-way handshake to determine open ports.
        - Command: `nmap -sT <target>`
        - Example: `nmap -sT scanme.nmap.org`
    - **UDP Scans (-sU)**: Scans for open UDP ports.
        - Command: `nmap -sU <target>`
        - Example: `nmap -sU scanme.nmap.org`
    - **Comprehensive Scan (-A)**: Enables "aggressive" scanning, including OS detection (-O), version scanning (-sV), script scanning (-sC), and traceroute (--traceroute).
        - Command: `nmap -A <target>`
        - Example: `nmap -A scanme.nmap.org`
    - **Custom Port Range Scan (-p)**: Specify a range of ports to scan.
        - Single Port: `nmap -p 80 <target>`
        - Port Range: `nmap -p 1-100 <target>`
        - All Ports: `nmap -p- <target>`
    - **Nmap Scripting Engine (NSE)**: Allows you to write custom scripts (using Lua) to automate various networking tasks.
        - Run Default Scripts: `nmap -sC <target>`
        - Specify Scripts: `nmap --script <filename>|<category>|<directory>/|<expression>[,...] <target>`

---

2. **Host Discovery**:
    - Nmap identifies active hosts using various techniques, including ICMP ping, TCP SYN, and ARP scans.
    - Customize host discovery options based on your needs.
    - Certainly! Let's delve into the details of host discovery using Nmap, covering various scenarios such as scanning network ranges, IP lists, multiple IPs, and single IPs.

  2.1. **Scan Network Range**
To scan a range of IP addresses, you can use the following command:

```bash
nmap 192.168.1.1-254
```

This command will scan all IP addresses from `192.168.1.1` to `192.168.1.254`. Nmap will perform a TCP SYN connection scan on the most common ports (default 1000) and an ICMP echo request to determine if a host is up.

   2.2. **Scan IP List**
If you have a list of IP addresses in a file (let's say `targets.txt`), you can scan them using the `-iL` option:

```bash
nmap -iL targets.txt
```

The `targets.txt` file should contain one IP address per line.

   2.3. **Scan Multiple IPs**
You can specify multiple IP addresses separated by spaces to scan them together:

```bash
nmap 192.168.1.1 192.168.1.2 192.168.1.3
```

This command will scan the specified IP addresses individually.

   2.4. **Scan Single IP**
For scanning a single IP address, simply provide the IP as an argument:

```bash
nmap 192.168.1.1
```

Nmap will run a TCP SYN connection scan (default) on the most common ports and an ICMP echo request to determine if the host is up.

---

3. **Host and Port Scanning**:

Certainly! Let's dive into the details of host and port scanning, including open ports, service versions, and the different states for scanned ports.


Open Ports and Services


When Nmap identifies an open port, it means that a service is actively listening on that port. Here are some common open ports and their associated services:



Port 80 (HTTP)**:
    - Service: Web server (usually Apache, Nginx, or IIS)
    - Information: Hosts websites and serves web pages over HTTP.

Port 443 (HTTPS)**:
    - Service: Secure web server (usually using TLS/SSL)
    - Information: Hosts secure websites with encrypted communication.

Port 22 (SSH)**:
    - Service: Secure Shell (SSH) server
    - Information: Allows secure remote access to the system via command-line interface.

Port 21 (FTP)**:
    - Service: File Transfer Protocol (FTP) server
    - Information: Used for transferring files between systems.

Port 25 (SMTP)**:
    - Service: Simple Mail Transfer Protocol (SMTP) server
    - Information: Handles outgoing email communication.

Port 53 (DNS)**:
    - Service: Domain Name System (DNS) server
    - Information: Resolves domain names to IP addresses.

Service Versions
Nmap can often determine the version of a service running on an open port. For example, it can identify the specific web server software (e.g., Apache, Nginx) or the SSH server version (e.g., OpenSSH).

To retrieve service versions, use the `-sV` flag:

```bash
nmap -sV target_ip
```

Operating System Detection
Nmap can also attempt to identify the operating system (OS) running on the target host. It analyzes network responses and compares them against known OS fingerprints.

To perform OS detection, use the `-O` flag:

```bash
nmap -O target_ip
```

Different States for Scanned Ports
Nmap categorizes scanned ports into different states:

**Open**: A service is actively listening on the port, and it is accessible.
 
 **Closed**: No service is listening on the port, and it is not accessible.

**Filtered**: A firewall or filter is blocking connections to the port.

**Unfiltered**: The port is neither open nor closed; Nmap cannot determine its state.

**Open|Filtered**: Nmap cannot conclusively determine if the port is open or filtered.

---

4. **Saving the Results**:
    - Save scan results in different formats:
        - **Normal Nmap Output**: `nmap -oN results.txt target`
        - **Grepable Nmap Output**: `nmap -oG results.grep target`
        - **XML Format**: `nmap -oX results.xml target`

## Installation
1. Install Nmap on your system:
    - On Ubuntu: `sudo apt-get install nmap`
    - On Kali Linux: Nmap is pre-installed.

## Usage
1. Basic Scan:
    - `nmap target_ip`

2. Advanced Scan:
    - Specify ports: `nmap -p 80,443 target_ip`
    - Use NSE scripts: `nmap --script vuln target_ip`

## Configuration
1. Customize Nmap behavior:
    - Modify scan options in the command line.
    - Explore NSE scripts for specific tasks.

## Contributing
1. Contribute to Nmap development:
    - Visit the [official Nmap website](https://nmap.org/) for details.

## Note
1. Always use Nmap responsibly and with proper authorization.
2. Understand the impact of your scans on the target network.
3. Keep your Nmap installation up-to-date.
