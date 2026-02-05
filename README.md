# Wireshark Network Traffic Analysis Project

## Objective
To understand how normal network traffic works by capturing and analyzing live packets using Wireshark, focusing on DNS and TCP behavior.

## Tools Used
- Wireshark
- Windows OS

## Steps Performed

### 1. Packet Capture
- Captured live traffic during normal browsing (YouTube, LinkedIn).

### 2. DNS Analysis
- Applied filter: `dns`
- Observed DNS queries and responses
- Identified domain name resolution process

### 3. TCP Analysis
- Applied filter: `tcp`
- Studied TCP 3-way handshake
- Analyzed TCP stream using **Follow → TCP Stream**

### 4. TCP Retransmission Analysis
- Applied filter: `tcp.analysis.retransmission`
- Identified retransmissions caused by normal network latency
- Confirmed traffic was **not malicious**

## Findings
- DNS traffic resolved domains correctly
- TCP connections followed expected handshake patterns
- Retransmissions observed were normal and common in real-world traffic

## Conclusion
This project helped me understand how normal network traffic behaves and how to distinguish expected retransmissions from suspicious activity — a key skill for SOC analysts.
