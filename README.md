# PCAP Analysis Project - Credential Extraction

![Image](https://github.com/Andre2404/PCAP-traffic-analysis/blob/main/Wireshark%20Capture.PNG)

## Project Overview
This project demonstrates network forensic analysis capabilities by extracting clear-text credentials from PCAP files using Wireshark. The analysis successfully identified multiple user credentials transmitted over unencrypted HTTP protocols, highlighting critical security vulnerabilities in network communications.

## Project Objectives
- Identify and extract username/password credentials from network traffic
- Demonstrate proficiency in Wireshark for packet analysis
- Analyze security vulnerabilities in network protocols
- Document forensic methodology and findings

## Tools Used
- **Wireshark** - Primary packet analysis tool
- **Display Filters** - Targeted traffic filtering
- **HTTP Stream Analysis** - Credential extraction
- **Protocol Analysis** - Multiple protocol examination

## Key Findings

### Extracted Credentials
Successfully identified 3 sets of valid credentials from DVWA (Damn Vulnerable Web Application):

| Username | Password | Status | Session ID |
|----------|----------|---------|------------|
| admin | password | Successful Login | PHPSESSID=26t6nrhp1mb3fe5vdfliva81q2 |
| gordonb | abc123 | Successful Login | PHPSESSID=4t0stf9o5ikr0gj09tkvrf25cs |
| pablo | letmein | Successful Login | PHPSESSID=r3rlac15d230uep3spt1e1qgk8 |

### Security Vulnerabilities Identified
- **Clear-text Transmission**: Credentials sent via unencrypted HTTP
- **Lack of HTTPS**: No encryption for sensitive data
- **Multiple Exposure**: Three different accounts compromised
- **Network Sniffing Vulnerability**: Easy credential interception

## Methodology

### Step 1: Initial Analysis
- Opened PCAP file in Wireshark
- Conducted general traffic observation
- Identified relevant protocols

### Step 2: Targeted Filtering
```wireshark
http.request.method == "POST"
