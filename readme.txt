# Cyber Security Internship - Task 1: Local Network Port Scan

## Objective
**Learn to discover open ports on devices in your local network to understand network exposure.**

## My Network
- **IP**: `192.168.220.228`
- **Subnet Mask**: `255.255.224.0` → `/19`
- **Gateway**: `192.168.192.1`
- **Scan Target**: `192.168.192.0/19` (8192 IPs)

## Tools Used
- **Nmap (via Zenmap GUI)** v7.98
- Windows 11

## Command Executed
```bash
nmap -T4 -F 192.168.192.0/19