# Task1_by_abhyaskathuria
# Cyber Security Internship - Task 1: Local Network Port Scan

## Objective
**Learn to discover open ports on devices in your local network to understand network exposure.**

---

## My Network
- **My IP**: `192.168.220.228`  
- **Subnet Mask**: `255.255.224.0` → `/19`  
- **Default Gateway**: `192.168.192.1`  
- **Scan Target**: `192.168.192.0/19` → **8192 IP addresses**

---

## Tools Used
- **Nmap** (via **Zenmap GUI**) v7.98  
- **OS**: Windows 11  
- **Wireshark**: Not used (optional)

---

## Command Executed
```bash
nmap -T4 -F 192.168.192.0/19

Scan Results Summary
textNmap done: 8192 IP addresses (832 hosts up) scanned in 3250.24 seconds

Hosts with Open Ports: 236
Total Unique Services Found: 20+ (including Telnet, SMB, RDP, MySQL, RTSP, HTTP/HTTPS)


Critical Open Ports & Security Risks


IP AddressOpen PortsService(s)Risk LevelNotes192.168.220.228 (MY PC)135, 139, 445, 3306RPC, NetBIOS, SMB, MySQLHIGHSMB → EternalBlue risk; MySQL exposed → data theft192.168.192.3123, 80, 443Telnet, HTTP, HTTPSCRITICALTelnet = plaintext login192.168.195.8280, 443, 554, 3389HTTP, HTTPS, RTSP, RDPHIGHRDP → brute-force; RTSP → IP camera192.168.192.553, 88, 135, 139, 389, 445DNS, Kerberos, LDAP, SMBHIGHMultiple Windows services exposed192.168.223.2468888Sun AnswerbookMEDIUMLegacy serviceMany devices1900, 49152+UPnP, Unknown High PortsHIGHUPnP = DDoS risk
Telnet (23/tcp) found on 20+ devices (Edgecore switches) → MOST CRITICAL FINDING

Security Risks Identified

Telnet (23/tcp) → Passwords in plaintext → Sniffable
SMB (445/tcp) → Exploitable (WannaCry, EternalBlue)
MySQL (3306/tcp) → Database exposed → SQL injection / credential dump
RDP (3389/tcp) → Brute-force / BlueKeep
RTSP (554/tcp) → IP cameras with default passwords
UPnP (1900/tcp) → Device takeover / DDoS amplification


Mitigation Recommendations

Disable Telnet → Replace with SSH
Disable SMBv1, block externally
Bind MySQL to localhost (127.0.0.1)
Enable Windows Firewall → Block inbound
Use strong passwords + 2FA
Patch all systems (routers, PCs, IoT)
Segment network (IoT vs Workstations)


Step-by-Step: How I Completed the Task

Installed Nmap from nmap.org
Ran ipconfig → Found /19 subnet
Opened Zenmap → Set target: 192.168.192.0/19
Used Quick scan profile → nmap -T4 -F
Waited ~54 mins → 832 hosts up
Analyzed output → Noted Telnet, SMB, MySQL
Researched risks (e.g., Telnet = plaintext)
Saved:
task1scan.txt (raw output)
scan_results.xml (full scan)
Screenshot of results

Created GitHub repo → Uploaded all files


Files Included in This Repo

task1scan.txt → Full Nmap text output
scan_results.xml → Saved scan (open in Zenmap)
screenshot_results.png → Zenmap GUI with results
README.md → This file


Interview Questions – My Answers

Question,Answer
1. What is an open port?,"A port in listening state, accepting connections (e.g., 23/tcp on router)"
2. How does Nmap perform TCP SYN scan?,Sends SYN → Gets SYN-ACK = open; RST = closed. Stealthy
3. Risks of open ports?,Telnet → credential theft; SMB → ransomware; RDP → remote access
4. TCP vs UDP scanning?,"TCP reliable (handshake); UDP connectionless, slower, uses -sU"
5. How to secure open ports?,"Firewall, disable service, strong auth, patch"
6. Firewall's role?,Blocks unwanted inbound; allows only needed ports
7. Why do attackers port scan?,Reconnaissance → map services → find weak points
8. How does Wireshark complement?,Captures live packets on open ports → analyze traffic

Key Learnings

TCP SYN scan is fast and stealthy
Open SMB/MySQL on your own PC = major risk
Telnet should NEVER be exposed
Always scan your own network — you might be the weakest link
Firewalls + patching = first line of defense
