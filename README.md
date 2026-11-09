# WEB_SHELL-DDOS-PROJECCT

# DOS-DDOS-ATTACK-INVESTIGATION
### Log Analysis & SIEM Traffic Investigation: DoS/DDoS Mitigation with Splunk

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [DoS/DDoS Concepts & Indicators of Compromise (IoCs)](#dosddos-concepts--indicators-of-compromise-iocs)
3. [Lab Walkthrough & Documentation](#lab-walkthrough--documentation)
4. [Tools & Technologies Used](#tools--technologies-used)
5. [Conclusion](#conclusion)

---

## 1. Project Overview
<a id="project-overview"></a>

This project documents a comprehensive hands-on investigation into Denial-of-Service (DoS) and Distributed Denial-of-Service (DDoS) attacks targeting a bicycle parts web service. The repository details manual web access log parsing (`access.log`) to identify brute-force login floods, target endpoints, and server error degradation, as well as advanced SIEM querying using **Splunk** to track botnet distributions, user-agent signatures, and peak traffic intervals.

---

## 2. DoS/DDoS Concepts & Indicators of Compromise (IoCs)
<a id="dosddos-concepts--indicators-of-compromise-iocs"></a>

* **Attack Vector Classification:** Examines Slowloris, HTTP Floods, Cache Bypasses, Oversize Queries, and Login/Form Abuse.
* **Key IoCs Tracked:**
  * **High Request Rate:** Heavy resource endpoints (such as `/login`) flooded with rapid queries.
  * **Odd User-Agents:** Outdated or automated user-agent signatures (e.g., `Java/1.8.0_181`).
  * **Burst Timestamps:** Unnatural request spikes clustered within tight one-second windows.
  * **Server Error Surges:** Tracking the escalation to `503 Service Unavailable` responses.

---

## 3. 📑 Lab Walkthrough & Documentation
<a id="lab-walkthrough--documentation"></a>

The complete step-by-step forensic breakdown, Splunk SPL queries, timechart metrics, and investigation answers have been compiled into a dedicated walkthrough file:

👉 **[Read the Full Step-by-Step Investigation Walkthrough](./Dos-DDoS-Investigation-Walkthrough.md)**

---

## 4. Tools & Technologies Used
<a id="tools--technologies-used"></a>

* **Linux Terminal & Log Parsing** (`cat`, `grep`)
* **Apache Access Logs** (`access.log`)
* **Splunk Enterprise** (Search & Reporting, SPL querying, timechart visualization)

---

## 5. Conclusion
<a id="conclusion"></a>

> **Detecting DoS and DDoS threats requires recognizing automated traffic patterns, user-agent anomalies, and resource endpoint flooding. Leveraging SIEM platforms like Splunk allows security analysts to quickly isolate botnet IPs and measure traffic impact during active incidents.**
