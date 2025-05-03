# 📊 Phase 2: SIEM Dashboard Analysis using Splunk

This phase demonstrates how to collect, analyze, and visualize logs from both an attacker and a victim machine using Splunk to identify and understand cyberattack patterns.

---

## 🎯 Objective

To integrate logs from both attacker (Kali Linux) and victim (Metasploitable3) environments into Splunk, visualize the attack patterns, and verify data correlation across systems.

---

## 🧰 Environment Setup

- 📌 SIEM Tool: Splunk
- 💻 Attacker Machine: Kali Linux
- 🖥️ Victim Machine: Metasploitable3
- 📁 Log Files:
  - kali_attack.log (attacker side)
  - victim_log.txt (victim side)

---

## 🧪 Step-by-Step Implementation

### 🔧 Step 1: Install Splunk on Kali Linux

- Downloaded Splunk Enterprise .deb package from the official website
- Installed using:

```bash
sudo dpkg -i splunk-<version>.deb
sudo /opt/splunk/bin/splunk start --accept-license


# 📄 Phase 2: Splunk SIEM Queries and Notes

=========================================
🔍 Log Query 1: Combine both log sources
=========================================
sourcetype="attacker_log" OR sourcetype="victim_log"

# Description:
# This query pulls events from both logs — Kali (attacker) and Metasploitable3 (victim)

-----------------------------------------

=========================================
🔍 Log Query 2: View only attacker log entries
=========================================
sourcetype="attacker_log"

# Description:
# Shows only logs from the attacker (Kali Linux)

-----------------------------------------

=========================================
🔍 Log Query 3: View only victim log entries
=========================================
sourcetype="victim_log"

# Description:
# Shows only logs from the victim (Metasploitable3)

-----------------------------------------

=========================================
🔍 Optional Query: Filter by a specific keyword
=========================================
sourcetype="victim_log" ftp OR login

# Description:
# Searches for FTP login attempts or related activity in victim logs

-----------------------------------------

=========================================
📊 Dashboard Notes
=========================================

Panel 1 – Attacker Logs Panel:
Query: sourcetype="attacker_log"
Type: Table or Time Chart

Panel 2 – Victim Logs Panel:
Query: sourcetype="victim_log"
Type: Table or Time Chart

You can add filters such as:
host, _time, src_ip, message, etc.

-----------------------------------------

=========================================
📁 Source Types Used in Splunk
=========================================

attacker_log — for kali_attack.log  
victim_log — for victim_log.txt

Use these exact names when uploading logs into Splunk via "Add Data".

-----------------------------------------

=========================================
📸 Recommended Screenshots for Report
=========================================

1. Screenshot of Splunk Web running (localhost:8000)
2. Screenshot of log files being uploaded with source types set
3. Screenshot of the combined query result (Query 1)
4. Screenshot of the dashboard with 2 panels

=========================================
✅ END OF FILE
=========================================
