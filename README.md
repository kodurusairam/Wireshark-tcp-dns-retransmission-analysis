Wireshark Network Traffic Analysis – SOC Mini Project
Project Overview

This project demonstrates offline PCAP analysis using Wireshark to understand normal network behavior and distinguish benign anomalies from malicious activity.
The analysis was performed from a SOC analyst perspective using real user-generated traffic.

Objective

Capture live network traffic and save it as a PCAP file

Perform offline packet analysis using Wireshark

Analyze TCP sessions, DNS queries, and retransmissions

Validate whether observed anomalies are benign or malicious

Tools Used

Wireshark

Web browser (for traffic generation)

Traffic Generated

The following legitimate user activities were performed during capture:

YouTube video streaming

LinkedIn browsing

Job search activity (SOC L1 roles)

This ensured realistic enterprise-style encrypted web traffic.

1️⃣ PCAP File Capture and Upload

Network traffic was captured and saved as a PCAP file

The PCAP was later opened in Wireshark for offline analysis

Offline analysis allows evidence preservation and deeper inspection without live traffic impact

Outcome:

PCAP file successfully loaded

Packet list populated with TCP, UDP, DNS, TLS, and STUN traffic

2️⃣ TCP Analysis and TCP Stream (Handshake Validation)
TCP Analysis

Applied the display filter:

tcp


Observed TCP packets using port 443 (HTTPS)

Verified normal TCP session behavior and acknowledgements

TCP Stream Analysis

Followed a TCP stream using:

Follow → TCP Stream


Observed encrypted client–server communication

Outcome:

TCP three-way handshake behavior validated

Encrypted HTTPS traffic confirmed

No plaintext data exposed (expected behavior)

3️⃣ DNS Analysis and LinkedIn Verification
DNS Filtering

Applied the display filter:

dns


Observed DNS queries and responses between the local system and DNS resolver

Domain Verification

Used string search with the keyword:

linkedin


Identified DNS queries for:

merchantpool1.linkedin.com


Verified that the domain was resolved through standard DNS workflow

Outcome:

DNS queries were user-initiated

Domains belonged to legitimate services (LinkedIn, Google)

No suspicious or algorithmically generated domains observed

4️⃣ TCP Retransmission Analysis (Benign Anomaly)
Retransmission Detection

Applied the display filter:

tcp.analysis.retransmission


Observed multiple TCP retransmission packets highlighted in red

Verification

Destination port: 443 (HTTPS)

Destination IPs: public cloud/CDN addresses

Occurred during video streaming and browsing activity

Outcome:

Retransmissions attributed to normal network conditions
(e.g., congestion, Wi-Fi interference, high-bandwidth traffic)

No indicators of compromise detected

Key Findings

Traffic consisted of normal encrypted HTTPS communication

DNS queries resolved legitimate domains

TCP retransmissions were benign and expected

No malicious activity or threat indicators were identified
