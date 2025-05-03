# 🛡️ Phase 3: Defensive Strategy – Fail2Ban Implementation

This project demonstrates how to defend a vulnerable service (FTP on Metasploitable3) from brute-force attacks using Fail2Ban and compare system behavior before and after implementation.

---

## 📌 Objective

To implement a defensive mechanism that automatically detects and blocks brute-force FTP attacks using Fail2Ban, and to validate its effectiveness by repeating the attack.

---

## 🧪 Environment Setup

- 🐧 Victim Machine: Metasploitable3  
- 💻 Attacker Machine: Kali Linux  
- 🔒 Defense Tool: Fail2Ban  
- 📡 Service Attacked: FTP  
- 🕵️ Tool for Attack: Hydra  

---

# 🛡️ Phase 3 – All Commands and Queries

# ========================
# 📍 Step 1: Attack (Before Defense)
# ========================

# Run Hydra brute-force attack from Kali Linux:
hydra -l msfadmin -P /usr/share/wordlists/nmap.lst ftp://192.168.56.102

# ========================
# 📍 Step 2: Install and Configure Fail2Ban (on Metasploitable3)
# ========================

# Update and install Fail2Ban
sudo apt update
sudo apt install fail2ban -y

# Edit Fail2Ban jail configuration file
sudo nano /etc/fail2ban/jail.local

# Paste the following into jail.local
[vsftpd]
enabled = true
port    = ftp
filter  = vsftpd
logpath = /var/log/vsftpd.log
maxretry = 3
bantime = 600

# Save and close nano:
# Press Ctrl + O → press Enter to save
# Press Ctrl + X to exit nano

# Restart Fail2Ban service
sudo systemctl restart fail2ban

# ========================
# 📍 Step 3: Rerun Attack (After Defense Applied)
# ========================

# Try brute-force again from Kali Linux:
hydra -l msfadmin -P /usr/share/wordlists/nmap.lst ftp://192.168.56.102

# After 3 failed tries, the IP will be blocked by Fail2Ban

# ========================
# 📍 Step 4: Check Fail2Ban Status and Logs (on Metasploitable3)
# ========================

# View status of Fail2Ban jail for FTP (vsftpd)
sudo fail2ban-client status vsftpd

# Check the log for banned IPs
cat /var/log/fail2ban.log | grep Ban

# Optional: See all jails running
sudo fail2ban-client status

# Optional: Unban an IP (replace with actual IP)
sudo fail2ban-client set vsftpd unbanip 192.168.56.101

# ========================
# 📍 Step 5: Screenshot Suggestions
# ========================

# 1. Before attack success: Hydra shows password cracked
# 2. jail.local config file open in nano
# 3. After attack blocked: Hydra stops after 3 tries
# 4. fail2ban-client status shows banned IP
# 5. /var/log/fail2ban.log shows Ban
# 6. Side-by-side table showing Before vs After result
