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

---


