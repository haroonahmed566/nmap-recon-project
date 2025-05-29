
# 🔍 Metasploitable2 Nmap Recon Project

## 📌 Objective

Perform a full port scan and service enumeration of the Metasploitable2 virtual machine using Nmap, and map the findings to MITRE ATT&CK techniques.

---

## 💻 Lab Setup

- **Attacker Machine**: Kali Linux (VirtualBox)
- **Target Machine**: Metasploitable2 (VirtualBox)
- **Network Mode**: Host-Only Adapter
- **Target IP**: `192.168.1.20`

---

## 🧰 Tools Used

- **Nmap v7.95**  
  Full command:
  ```bash
  nmap -sS -sV -O -p- -T4 -A 192.168.1.20 -oN nmap_full.txt
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

- `nmap_full.txt`: Full scan results
- `README.md`: Project summary

---

## 🧠 What I Learned

- How to perform OS and version detection using Nmap  
- How to identify vulnerable services  
- How to correlate recon data with real-world frameworks (MITRE ATT&CK)  
- How to document findings in a structured, job-ready format  

---

## 🚀 Next Steps

- Enumerate SMB shares with `smbclient`  
- Connect to services and test credentials (FTP, Telnet)  
- Capture traffic with Wireshark  
- Move on to exploitation phase
