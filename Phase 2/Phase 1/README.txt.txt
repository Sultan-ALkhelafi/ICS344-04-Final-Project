# 🛠️ Phase 1: Setup & Attack (Metasploit FTP Exploit)

This document provides step-by-step instructions for setting up a penetration testing environment and launching a sample FTP attack using Metasploit on Kali Linux against a vulnerable Metasploitable3 machine.

---

## 📦 1. Install Virtual Machines (VMs)

### ✅ Tools Needed:

- Oracle VirtualBox (or VMware)
- Kali Linux ISO (Attacker)
- Metasploitable3 (Victim)

### 🧑‍💻 Why?
- Kali Linux is a penetration testing OS
- Metasploitable3 is a purposely vulnerable machine

---

## 🌐 2. Set Network to Host-Only

Make sure both VMs are on the same network so they can communicate.

### 🛠️ In VirtualBox:

1. Select Kali VM → Settings → Network → Adapter 1: “Host-only Adapter”
2. Repeat for Metasploitable3 VM

3. Configured both VMs to use Host-Only networking
4. Verified IP connectivity between attacker and victim
5. Launched Metasploit in Kali and searched for FTP exploit
6. Set target IP and executed the exploit successfully
7. Wrote and executed a simple custom Python script on Kali

Included:
- setup_steps.txt: Instructions followed to install and configure the VMs
- metasploit_attack.txt: Steps and commands used to run the FTP attack
- custom_script.py: Sample custom script created for the attack
- 3 screenshots showing network setup, IP discovery, and attack result

