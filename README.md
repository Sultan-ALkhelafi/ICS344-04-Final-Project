# ICS344 – Information Security  
## Project Title: Vulnerability Exploitation, SIEM Analysis & Defense Strategy

### Student Information
- **Name**: Sultan Alkhelaifi  
- **Student ID**: 202040260  
- **Course Section**: 04  

---

## 📘 Project Summary

This project consists of three main phases: exploiting a vulnerable SSH service, analyzing the attack using a SIEM tool, and implementing a defense strategy.

---

## ⚙️ Phase 1: Setup & Exploitation

### Environment Setup
- **Victim Machine**: Metasploitable3 (VirtualBox)
- **Attacker Machine**: Kali Linux

### Targeted Service
- **Service**: SSH (port 22)

### Tools Used
- **Metasploit Framework**
- **Custom Python script for brute force attack**

### Execution Overview
- Exploitation performed using `msfconsole` and the `auxiliary/scanner/ssh/ssh_login` module.
- Discovered valid credentials: `vagrant:vagrant`.
- Session elevated to Meterpreter shell.
- A custom Python script was written to automate brute-force SSH logins.

---

## 📊 Phase 2: SIEM Analysis Using Splunk

### Tool
- **Splunk v9.3.2**

### Setup
- Logs forwarded from the victim VM to Splunk.
- Focused on SSH-related login attempts.

### Visualizations
Used Splunk search queries to build dashboards:
```spl
index=* "Failed password" | timechart count
index=* "Failed password" | stats count by host
