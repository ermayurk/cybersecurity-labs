# 🛠️ HTB Starting Point Labs – Summary

Hello there! 👋  

This file contains a summary of the **Hack The Box – Starting Point** labs. These beginner-level challenges introduce real-world attack vectors, services, and tools that form the foundation for more advanced labs.  

🔸 **Skipping these labs is a mistake.**  
🔸 **Writing full reports for each? Also unnecessary.**  

So here's the balanced middle ground — a **crisp summary** of what I’ve learned, along with the key tools and commands used.

---

## 🔰 Tier 0 – Basic Remote Access

In this tier, we gained initial access through weak or misconfigured services.

### 🧪 Techniques Explored
- Anonymous login to **FTP**
- Accessing **Telnet** with default credentials
- Discovering open **SMB** shares
- Connecting to exposed **Redis** servers

### 🛠️ Tools Used

```bash
# Nmap – Scan all ports with scripts and service detection
nmap -sC -sV -p- <IP>

# FTP – Connect using anonymous login
ftp <IP>

# SMBClient – List available shares
smbclient -L //<IP>/ -N

# SMBClient – Connect to specific share
smbclient //<IP>/sharename -N

# Telnet – Connect to service
telnet <IP>

# Redis CLI – Access Redis server
redis-cli -h <IP>
```

### 🧠 Key Takeaways
- How nmap scans ports, detects services, and identifies misconfigurations.
- Risks of exposing FTP, Telnet, SMB, and Redis without authentication.
- How attackers exploit such services to gain initial system access.
- Basics of interacting with remote services via CLI tools.


## 🧩 Tier 1 – Web & Service Enumeration
Here we shifted focus toward deeper enumeration and web-based discovery.

### 🧪 Techniques Explored
```
# Increasing packet send rate in Nmap:
nmap --min-rate 1000 -sV -p- <IP>

# Using Gobuster for brute-forcing hidden directories:
gobuster dir -u http://<IP> -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

# Filtering file types in Gobuster:
gobuster dir -u http://<IP> -x php,txt,html -w <wordlist>

# Connecting to MySQL using valid credentials:
mysql -u <user> -p -h <IP>

# Understanding the role of /etc/hosts file (Entry in the /etc/hosts file):
echo "<target_ip> <domain_name>" |sudo tee -a /etc/hosts

# Using Responder to capture broadcast network traffic:
sudo responder -I <interface>
```

### 🧠 Key Takeaways
- Optimizing nmap speed using flags like --min-rate.
- Discovering web server directories and sensitive files with Gobuster.
- How attackers interact with databases via command line.
- Manual hostname resolution via the hosts file.
- Capturing NTLM and broadcast traffic using Responder for potential credential leaks.

## 🚀 Why This Matters
"Fundamentals are the building blocks of fun and elite performance."

These labs may be labeled "beginner," but they simulate real-world attack surfaces. Misconfigured services, weak credentials, and improper access control are still the root cause of many breaches today.

Mastering these basic techniques prepares me for:

Real-world CTFs 🧠

Penetration testing jobs 🔐

Advanced red team exercises 🎯

