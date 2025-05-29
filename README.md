
# 🔍 Metasploitable2 Nmap Recon Project

## 📌 Objective

Perform a full port scan and service enumeration of the Metasploitable2 virtual machine using Nmap, and map the findings to MITRE ATT&CK techniques.

---

## 💻 Lab Setup

- **Attacker Machine**: Kali Linux (VirtualBox)
- **Target Machine**: Metasploitable2 (VirtualBox)
- **Network Mode**: Internal Network Adapter
- **Target IP**: `192.168.1.20`

---

## 🧰 Tools Used

- **Nmap v7.95**  
  commands:
  ```bash
  # 1. Ping sweep
  nmap -sn 192.168.1.0/24

  # 2. TCP SYN scan
  nmap -sS 192.168.1.20

  # 3. Version detection
  nmap -sV 192.168.1.20

  # 4. OS detection
  nmap -O 192.168.1.20

  # 5. Aggressive scan
  nmap -A 192.168.1.20

  # 6. Vuln script scan
  nmap --script vuln 192.168.1.20

  # 7. Full port scan (TCP and UDP)
  nmap -p- -sS -sV 192.168.1.20
  nmap -sU -T4 -F 192.168.1.20
  ```

---

## 📊 Summary of Results

| Port | Service     | Version/Notes                              |
|------|-------------|--------------------------------------------|
| 21   | FTP         | vsftpd 2.3.4 (Anonymous login allowed)     |
| 22   | SSH         | OpenSSH 4.7p1                              |
| 23   | Telnet      | Linux telnetd                              |
| 25   | SMTP        | Postfix (SSLv2 supported)                  |
| 80   | HTTP        | Apache 2.2.8                               |
| 139  | SMB         | Samba smbd 3.0.20                          |
| 445  | SMB         | Samba smbd 3.0.20                          |
| 3306 | MySQL       | MySQL 5.0.51a                              |
| 5432 | PostgreSQL  | Version 8.3                                |
| 5900 | VNC         | Protocol 3.3 (No encryption)               |
| 8180 | HTTP        | Apache Tomcat 5.5 (Admin Panel Exposed)   |

---

## ⚠️ Notable Vulnerabilities (Mapped to MITRE ATT&CK)

| Service | Issue                              | MITRE ATT&CK Technique |
|---------|-------------------------------------|-------------------------|
| FTP     | Anonymous Login                     | [T1078.001](https://attack.mitre.org/techniques/T1078/001/) |
| Telnet  | Unencrypted Login Access            | [T1021.001](https://attack.mitre.org/techniques/T1021/001/) |
| SMB     | Exposed Shares (Potential Enum)     | [T1135](https://attack.mitre.org/techniques/T1135/) |
| VNC     | No Encryption / Weak Auth           | [T1021.005](https://attack.mitre.org/techniques/T1021/005/) |
| SMTP    | SSLv2 Enabled (Weak Encryption)     | [T1040](https://attack.mitre.org/techniques/T1040/) |

---

## 📁 Files in This Repo

- `README.md`: Project summary
- `ping-sweep.txt`: A basic sweep to check which hosts are online.
- `syn-scan.txt`: A SYN scan to identify open ports on the target system.
- `version-detection.txt`: A version detection scan to identify the services and versions running on open ports.
- `os-detection.txt`:  An OS detection scan to determine the operating system of the target machine.
- `aggressive-scan.txt`: A combination of multiple scans (including OS, version, and script scanning) to perform a more detailed security analysis.
- `vuln-scan.txt`: Scan for potential vulnerabilities using Nmap’s NSE (Nmap Scripting Engine).
- `full-tcp-scan.txt`:  A detailed scan of all TCP ports.
- `udp-scan.txt`: A scan of UDP ports to identify open services over UDP.

---

## 🧠 What I Learned

- How to perform OS and version detection using Nmap  
- How to identify vulnerable services  
- How to correlate recon data with real-world frameworks (MITRE ATT&CK)  
- How to document findings in a structured format  

---

