# Nmap Scan – Internal Vulnerability Assessment (Home Lab)

## Overview

This project demonstrates the use of Nmap to perform a basic vulnerability scan against a deliberately vulnerable virtual machine in a private lab environment. The goal was to identify open ports, running services, and potential attack surfaces in preparation for further enumeration and exploitation.

---

## 🖥️ Lab Environment

| Component        | Details                           |
|------------------|-----------------------------------|
| Scanner Machine  | Kali Linux (Virtual Machine)      |
| Target Machine   | Metasploitable2 (Virtual Machine) |
| Network Type     | NAT/Host-Only (Private IPs)       |
| Scan Date        | July 2025                         |

---

## Scan Command Used

bash nmap -sS -sV -0 -T4 192.168.56.101

-sS: SYN scan
-sV: Detect service versions 
-O: Attempt OS detection
-T4: Aggressive timing for quicker scans

---

## Sanitized Scan Output

Starting Nmap 7.93 ( https://nmap.org ) at 2025-07-17 14:42 UTC
Nmap scan report for target.local (192.168.56.101)
Host is up (0.00023s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp   open  telnet
25/tcp   open  smtp        Postfix smtpd
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
139/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp  open  microsoft-ds Samba smbd 3.X (workgroup: WORKGROUP)
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5

MAC Address: [REDACTED]
OS details: Linux 2.6.24 - 2.6.35
Network Distance: 1 hop

Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

---

## Analysis

The scan revealed multiple open services, including:

FTP (vsftpd 2.3.4) – known for past vulnerabilities.

Apache HTTP (port 80) – useful for web enumeration.

Samba/SMB (ports 139 & 445) – can be tested using enum4linux.

MySQL (port 3306) – typical for backend SQL enumeration.

The OS fingerprinting suggests a Linux-based system, likely Ubuntu.

These services provide entry points for tools like Nikto, Hydra, Dirb, and Metasploit in further stages of testing.

---

## Next Steps

Enumerate web directories with gobuster or dirb.

Run enum4linux for SMB enumeration.

Test weak credentials on FTP, SSH, and MySQL.

Map service versions to known CVEs (Common Vulnerabilities and Exposures)

---

## Skills Demonstrated

Network scanning with Nmap

Interpreting port, version, and OS fingerprinting results

Understanding common attack surfaces in vulnerable environments

Following ethical hacking best practices in isolated labs

---

##  Disclaimer

This project was created for educational purposes only. All scans were conducted in a controlled, isolated environment. Unauthorized scanning of networks is illegal and unethical.

