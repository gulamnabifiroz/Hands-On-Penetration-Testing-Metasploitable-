# Hands-On-Penetration-Testing-Metasploitable-
A cybersecurity portfolio demonstrating hands-on penetration testing methodologies against Metasploitable. Developed custom automation scripts and proof-of-concept exploits to target vulnerable network services and ports.
## Metasploitable Service Exploitation Lab
A security research portfolio demonstrating hands-on penetration testing methodologies against Metasploitable. This project focuses on vulnerability assessment, custom script development, and the exploitation of vulnerable network services across various open ports.

## Executive Summary

* **Objective:** Conduct authorized penetration testing to identify and exploit network vulnerabilities.
* **Scope:** Metasploitable environment targeting legacy protocols (FTP, SSH, HTTP, SMB).
* **Outcome:** Developed custom automated scripts and documented reproducible proof-of-concept (PoC) attacks.

## Technical Stack

* **Languages:** Python, Bash, Ruby
* **Tools:** Nmap, Metasploit Framework, Netcat, Wireshark
* **Environment:** Kali Linux, Metasploitable 2/3, VirtualBox

## Repository Structure

```text
├── exploits/               # Custom exploit scripts categorized by port
│   ├── port-21-ftp/        # Backdoor exploitation logic
│   └── port-22-ssh/        # Automated brute-force utilities
├── scanner/                # Nmap NSE scripts and automated port scanners
└── docs/                   # Detailed write-ups and mitigation strategies
```

## Methodology & Key Deliverables

#### 1. Reconnaissance & Port Scanning
Utilized advanced Nmap scanning techniques to map network topology, perform banner grabbing, and enumerate active services operating on open ports.

#### 2. Exploitation & Access Gaining
* **Port 21 (FTP):** Exploited the Vsftpd 2.3.4 backdoor to gain root shell access.
* **Port 22 (SSH):** Developed Python scripts to identify weak administrative credentials via brute-force simulation.
* **Port 80 (HTTP):** Leveraged web application flaws to execute remote code execution (RCE).

#### 3. Reporting & Mitigation
Documented root-cause analysis for each vulnerability and provided actionable remediation steps to secure the underlying operating systems.

#### -Disclaimer-

This repository is created strictly for educational purposes and professional portfolio demonstration. All testing was performed within an isolated, authorized lab environment.

## EXPLOITATION OF PORT-21 USING VSFTPD 2.3.4 BACKDOOR
1. Turn the METASPLOITABLE machine on.
<img width="1622" height="898" alt="image" src="https://github.com/user-attachments/assets/ee81d91e-46d0-4b23-a8e9-447aee62ef94" />
2. Find out the IP address of the machine.
COMMAND - "ip a"
<img width="1612" height="859" alt="image" src="https://github.com/user-attachments/assets/520e97e2-1b5e-4ea4-a31a-0e78c8036b54" />
4. Note down its IP address and then go to your kali linux and ping it to see if the victim machine is ACTIVE. The ping command will send ICMP packets to the host and find its status.
COMMAND - "ping (ip address of the victim)"
<img width="1605" height="794" alt="image" src="https://github.com/user-attachments/assets/b52e7d0a-bc82-4f2a-9011-73169cad33f5" />
5. Using the NMAP tool scan for the open ports in the victim's machine.
COMMAND - "nmap -p- (ip address)"
<img width="1606" height="852" alt="image" src="https://github.com/user-attachments/assets/3450768b-c1b0-449b-bbdf-b29b2cc90f78" />
6. As we can see all the ports have been scanned and a number of ports are open. We need a more detailed scan in order to exploit these. COMMAND - "nmap -sV -p- (ip address)"
<img width="1618" height="802" alt="image" src="https://github.com/user-attachments/assets/0a4132bc-8912-4215-b72f-64e4ca9e3ecb" />
7. AS we can see the FTP version running on the machine is highly vulnerable due to the backdoor that was discovered in VSFTPD version 2.3.4.
<img width="875" height="234" alt="image" src="https://github.com/user-attachments/assets/8dc51d42-fbe6-4035-b57e-b742cdec8c1a" />
8. Now let us exploit port 21 - FTP using the tool msfconsole in KALI LINUX. COMMAND - "msfconsole" 
<img width="1622" height="886" alt="image" src="https://github.com/user-attachments/assets/bbc8e309-fba3-4c51-82e0-626bc32261d8" />
9. Search for the VSFTPD backdoor in msfconsole. COMMAND - "search vsftpd 2.3.4"
<img width="1596" height="815" alt="image" src="https://github.com/user-attachments/assets/4b0948ac-023a-4684-9de9-2432de2fcfc4" />
11. To initiate that tool type "use" and the number of the tool. COMMAND - "use 0"
<img width="1620" height="186" alt="image" src="https://github.com/user-attachments/assets/7498b8fd-7447-4283-85ae-744eff3e98c7" />
12. Now set the Target host's ip address and the listener's ip address here. COMMAND - "set rhost (target ip) & set lhost(your ip)"
<img width="1620" height="823" alt="image" src="https://github.com/user-attachments/assets/15db9cce-c9a7-4753-866e-b91462118759" />
13. Now type the run command.
<img width="1622" height="160" alt="image" src="https://github.com/user-attachments/assets/c6d914bb-e3df-4733-b187-f3b812094a22" />
14. Now we can remotely access the root directories of the target & easily tamper,delete,use it.
<img width="1614" height="616" alt="image" src="https://github.com/user-attachments/assets/134b9468-d391-4ff5-b331-50db2a7ca7c4" />

#### In order to avoid these kind of attacks, Organizations must keep their important files inacessable to the public and patch their systems to the latest verison. To avoid public exposure, configure the vsftpd.conf file to completely disable unauthorized entries by setting anonymous_enable=NO. Next, jail legitimate users to their specific home directories with chroot_local_user=YES, preventing lateral system navigation.Because standard FTP transmits data in plaintext, you must enforce TLS encryption using ssl_enable=YES. This wraps credentials and files safely in transit. Finally, configure a firewall to restrict access to trusted IPs, define precise passive port ranges, and deploy Fail2ban to block automated brute-force attacks. Regularly patch the host operating system to eliminate daemon vulnerabilities.

# THANK YOU !!









