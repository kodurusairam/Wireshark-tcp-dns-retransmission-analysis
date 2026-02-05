
# Project: Wireshark Network Traffic Analysis Project


## Overview

This project involves a comprehensive deep-dive into network traffic using **Wireshark**. The analysis covers the full lifecycle of a web request: from the initial DNS query and TCP handshake to identifying packet loss via retransmissions.

---

## 1. Data Source: PCAP Analysis

The foundation of this analysis is the provided `.pcap` (Packet Capture) file. This file contains raw frames captured from a network interface, allowing for the inspection of Layer 2 through Layer 7 protocols.

* **File Name:** `network_dump.pcap`
* **Tooling:** Wireshark / Windows os / Chrome Browser

---

## 2. TCP Handshake & Stream Analysis

To establish a reliable connection, the analysis focuses on the **TCP Three-Way Handshake**. By following the TCP stream, we can see the synchronization between the client and the server.

### The Handshake Process

1. **SYN:** Client sends a synchronization request.
2. **SYN-ACK:** Server acknowledges and sends its own sync request.
3. **ACK:** Client acknowledges the server, establishing the connection.

> **Note:** We utilized the **"Follow TCP Stream"** feature to isolate this specific conversation from background noise, ensuring the sequence numbers () and acknowledgment numbers () align correctly.

---

## 3. DNS Resolution & Service Verification (LinkedIn)

This phase demonstrates how domain names are resolved to IP addresses and how to filter specific traffic in a crowded capture.

* **DNS Query:** Looked for `Standard query 0x... A linkedin.com`.
* **Filtering:** Applied the display filter `dns || http || tls` to isolate the resolution and subsequent connection.
* **LinkedIn Verification:** * Filtered specifically for `ip.addr == [LinkedIn_IP]`.
* Verified the **Server Name Indication (SNI)** in the TLS Client Hello to confirm the traffic was successfully routed to LinkedIn.



---

## 4. TCP Retransmissions & Error Recovery

Network conditions aren't always perfect. This section documents the identification of **TCP Retransmissions**, which occur when a sender does not receive an ACK within the expected RTO (Retransmission Timeout).

* **Identification:** Used the filter `tcp.analysis.retransmission`.
* **Observation:** Highlighted packets marked in **Black/Red** by Wireshark, indicating that the original data segments were likely lost or delayed in transit.
* **Impact:** Analyzed how these retransmissions affected the overall throughput of the stream.

* ## Findings
- DNS traffic resolved domains correctly
- TCP connections followed expected handshake patterns
- Retransmissions observed were normal and common in real-world traffic

## Conclusion
This project helped me understand how normal network traffic behaves and how to distinguish expected retransmissions from suspicious activity — a key skill for SOC analysts.
