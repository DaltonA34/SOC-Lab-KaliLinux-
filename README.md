# Analyzing BFD Authentication in Network Traffic Using Wireshark

## Overview
This lab analyzes BFD (Bidirectional Forwarding Detection) protocol traffic captured in a .pcap file to observe raw authentication exchanges, identify potential security issues, and learn how authentication mechanisms are exposed or protected in network protocols.

---

## Introduction
- What is BFD?
  - BFD (Bidirectional Forwarding Detection) is a network protocol used to detect faults between two forwarding engines (like routers or switches) across any type of media (physical or virtual) very quickly—often within milliseconds.

- Why is authentication important in routing protocols?
  - Authentication in routing protocols is crucial for securing the integrity and reliability of a network. Without authentication, attackers can manipulate routing information, leading to man-in-the-middle attacks, denial of service, traffic interception, or blackholing.
  
- Overview of raw authentication (vs MD5 or SHA auth).
  - Raw authentication sends a plain text password in routing protocol messages, making it simple but highly insecure, as the password can be easily captured with packet sniffing tools like Wireshark. In contrast, MD5 authentication uses a cryptographic hash to obscure the password, offering better protection but still being vulnerable to certain cryptographic attacks. HMAC-SHA (e.g., SHA-256) provides the strongest security by generating a keyed hash that ensures both the integrity and authenticity of routing messages, making it the recommended choice for modern, secure networks.

---

## Setup
- Tools
  - Kali Linux (2024.1)
  - Wireshark
  - [Wireshark Sample Captures](https://wiki.wireshark.org/SampleCaptures#sample-captures)
- File: [bfd-raw-auth-simple.pcap](bfd-raw-auth-simple.pcap)
- Steps:
  1. Startup and log into you Kali Linux Virtual Machine
  2. Go to [Wireshark Sample Captures](https://wiki.wireshark.org/SampleCaptures#sample-captures)
  3. Download the [bfd-raw-auth-simple.pcap](bfd-raw-auth-simple.pcap) file
  4. Once downloaded, drag the file to your desktop
  5. Right click the file and then let click 'Open With "wireshark"'
- [Image showing how to open with wireshark](SS1-Lab1.png)

---

## Analysis
- Filter the log data using udp.port == 3784
- Scroll down to the section named 'BFD Control message' and open the tab
- Scroll down further to see the 'Authentication' tab and open it
- The 'Authentication Type' here is 'Simple Password (1)'
- Further scrolling reveals the simple password to be the only authentication used
- The Password is 'secret'
- Authentication length: 9 bytes
- Authentication Key ID: 2
- [Image showing the Authentication section](SS4-Lab1.png)

---

## Security Implications
- Is this authentication method secure?
  - Using a simple password for authentication is not secure, especially in network protocols or systems exposed to the internet or untrusted networks. Simple passwords are vulnerable to brute force attacks, dictionary attacks, and eavesdropping if transmitted in plaintext or weakly protected forms.

- What are the risks of using raw authentication?
  - Using raw authentication, which sends passwords in plaintext, is risky because anyone capturing network traffic can easily see and steal the password. This allows attackers to impersonate trusted devices, intercept or modify messages, and inject false routing information, leading to network disruptions and security breaches. Since raw authentication provides no message integrity or encryption, it is highly insecure and should only be used in trusted or lab environments, never in production networks.

- What best practices (e.g., MD5/SHA auth, encryption) should be used instead?
  - Best practices for securing authentication in routing protocols include using cryptographic methods like MD5 or, preferably, HMAC-SHA (e.g., SHA-256) to ensure the password is never sent in plaintext. These methods generate a secure hash that verifies the authenticity and integrity of messages, protecting against tampering and replay attacks. Additionally, enabling encryption for routing traffic, using strong, complex passwords, and regularly rotating keys further strengthen security.

---

## Conclusion
- This lab demonstrates how insecure authentication mechanisms, such as raw or simple password authentication, can be easily exposed and analyzed using tools like Wireshark. By examining BFD traffic, we observed firsthand how sensitive information—like authentication credentials—can be captured in plaintext, underscoring the importance of implementing robust security measures in network protocols. For production environments, relying on weak authentication is unacceptable. Instead, cryptographically secure methods like HMAC-SHA should be adopted to protect routing infrastructure from unauthorized access, tampering, and network-based attacks. Through exercises like this, cybersecurity professionals can better understand the risks in legacy protocols and advocate for stronger security practices in real-world networks.

---

## Disclaimer
- This lab was conducted using publicly available packet capture files on a controlled, non-operational (dead/fake) network environment. No real-world or live production networks were accessed or affected during the analysis. The purpose of this lab is strictly educational and intended to promote a better understanding of network security practices. All analysis was performed in a safe, isolated environment to ensure no impact on actual network infrastructure or data privacy.














