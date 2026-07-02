# APEXPLANET-Task-2-Network-Security-and-Scanning

# Network Security and Scanning using Kali Linux

## Objective

To perform network security assessment by identifying live hosts, grabbing service banners, performing TCP and UDP scans, analyzing publicly available information using Shodan, and configuring OpenVAS (Greenbone) vulnerability scanner.

---

## Tools Used

- VMware Workstation Pro
- Kali Linux
- Metasploitable2
- Nmap
- Netcat (nc)
- Shodan
- OpenVAS (Greenbone)

---

## Step 1: Launch VMware Workstation

VMware Workstation Pro was launched successfully.

<img width="1911" height="1008" alt="Screenshot 2026-06-27 203933" src="https://github.com/user-attachments/assets/201db531-c309-43c1-aa55-2ecc5f80c486" />

---

## Step 2: Start Kali Linux

Kali Linux virtual machine was powered on successfully.

<img width="1918" height="1013" alt="Screenshot 2026-06-27 204124" src="https://github.com/user-attachments/assets/11e38d65-31a9-4100-be42-24b5ad57d601" />

---

## Step 3: Start Metasploitable2

Metasploitable2 virtual machine was started successfully.

Default Credentials

Username:

```
msfadmin
```

Password

```
msfadmin
```

<img width="1918" height="1020" alt="Screenshot 2026-06-19 211843" src="https://github.com/user-attachments/assets/a8aca051-54a4-4848-b5e1-eaf85af015a9" />

---

## Step 4: Verify Network Connectivity

Command

```bash
ping 192.168.152.128
```

Result

- Host reachable
- Successful communication established

<img width="1918" height="551" alt="Screenshot 2026-06-19 212216" src="https://github.com/user-attachments/assets/df7ee10c-c59a-4045-a914-d4ec1087390c" />

---

## Step 5: FTP Banner Grabbing

Command

```bash
nc 192.168.152.128 21
```

Output

```
220 (vsFTPd 2.3.4)
```

Observation

The FTP server responded with its banner, revealing that the target machine is running **vsFTPd version 2.3.4** on port **21**.

<img width="276" height="91" alt="Screenshot 2026-07-01 214826" src="https://github.com/user-attachments/assets/afb4ac87-a24a-4216-bb53-00573f82c1c4" />

---

## Step 6: HTTP Banner Grabbing

Command

```bash
printf "HEAD / HTTP/1.0\r\n\r\n" | nc 192.168.152.128 80
```

Output

```
HTTP/1.1 200 OK
Server: Apache/2.2.8 (Ubuntu)
X-Powered-By: PHP/5.2.4-2ubuntu5.10
```

Observation

The web server responded successfully and revealed:

- Apache/2.2.8
- Ubuntu
- PHP/5.2.4

<img width="578" height="167" alt="Screenshot 2026-07-01 215236" src="https://github.com/user-attachments/assets/bcdc91af-3438-4a5f-85d5-7b16b6dd593d" />

---

## Step 7: TCP SYN Scan

Command

```bash
sudo nmap -sS 192.168.152.128
```

Purpose

Performed a TCP SYN Scan to identify open TCP ports on the target machine.

<img width="655" height="637" alt="Screenshot 2026-07-01 215649" src="https://github.com/user-attachments/assets/016ade94-1ef3-4b07-8200-c3a51d004c06" />

---

## Step 8: UDP Scan

Command

```bash
sudo nmap -sU 192.168.152.128
```

Purpose

Performed a UDP scan to identify open UDP services available on the target system.

<img width="497" height="242" alt="Screenshot 2026-07-01 223751" src="https://github.com/user-attachments/assets/87c2c7f3-ea85-4015-a391-5c7863a22710" />

---

## Step 9: Nmap Scan Analysis

Open Services Identified

| Port | Service |
|-------|----------|
| 21 | FTP |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 111 | RPC |
| 139 | NetBIOS |
| 445 | SMB |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 5900 | VNC |
| 8180 | HTTP |

The scan identified multiple services running on the target machine that may require further security assessment.

<img width="700" height="767" alt="Screenshot 2026-07-02 211834" src="https://github.com/user-attachments/assets/6d6b1b98-20d4-4dd8-a95d-17b667fab32e" />


---

## Step 10: Shodan Search

Visited the Shodan search engine and searched for:

```
scanme.nmap.org
```

Observation

- Search completed successfully.
- No indexed results were available at the time of testing.
- This demonstrates that not every public host is indexed by Shodan.

<img width="1918" height="987" alt="Screenshot 2026-07-01 224551" src="https://github.com/user-attachments/assets/95a23b2b-f664-4186-ba85-9e42fc189dbb" />

---

# Step 11: Vulnerability Assessment using Nessus Essentials

Login into Nessus Essentials.

Create a new Basic Network Scan.

Target

```
192.168.152.128
```

Start the vulnerability scan.

📷 **Screenshot:** `Step8_Nessus_Scan.png`

---

# Step 12: Nessus Scan Results

Example Vulnerabilities Found

| Severity | Vulnerability |
|------------|------------------------------|
| Critical | vsFTPd 2.3.4 Backdoor |
| High | SMB Signing Disabled |
| High | Apache Outdated Version |
| Medium | SSL Weak Cipher |
| Medium | Telnet Service Enabled |
| Low | ICMP Timestamp Response |

📷 **Screenshot:** `Step9_Nessus_Report.png`

---

# Step 13: Vulnerability Details

Example

### FTP Service

Service

```
vsFTPd 2.3.4
```

Risk

- Backdoor vulnerability
- Remote Code Execution

Recommendation

- Upgrade FTP Server
- Disable anonymous login
- Use SFTP instead of FTP

📷 **Screenshot:** `Step10_FTP_Vulnerability.png`

---

# Results

- Successfully configured the virtual lab.
- Verified communication between Kali Linux and Metasploitable2.
- Performed FTP and HTTP banner grabbing.
- Conducted TCP SYN Scan.
- Conducted UDP Scan.
- Identified multiple open services.
- Performed Shodan search.
- Configured OpenVAS (Greenbone).
- Successfully launched the  Nessus Essentials web interface.

---

# Conclusion

This task demonstrated practical network reconnaissance and vulnerability assessment techniques using Kali Linux. Banner grabbing, TCP and UDP scanning, Nmap analysis, Shodan reconnaissance, and  Nessus Essentials configuration provided hands-on experience in identifying exposed services and preparing a target system for security assessment.

---


