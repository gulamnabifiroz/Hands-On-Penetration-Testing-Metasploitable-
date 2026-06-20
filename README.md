# SSH and FTP Penetration Testing Report

## Introduction

This project focuses on performing a security assessment of SSH and FTP services running on a target machine. The objective is to identify potential vulnerabilities, misconfigurations, and security weaknesses that could be exploited by attackers. The assessment was conducted in a controlled and authorized environment for educational and security testing purposes.

---

# Scope

The following services were included in the assessment:

| Service | Port | Purpose               |
| ------- | ---- | --------------------- |
| FTP     | 21   | File Transfer Service |
| SSH     | 22   | Secure Remote Access  |

---

# Methodology

The assessment was performed using a standard penetration testing methodology:

1. Information Gathering
2. Service Enumeration
3. Vulnerability Identification
4. Security Analysis
5. Documentation and Reporting

---

# Tools Used

The following tools were used during the assessment:

* Nmap
* Netcat
* FTP Client
* SSH Client
* Metasploit Framework (where applicable)
* Linux Terminal Utilities

---

# FTP Security Assessment

## Overview

FTP (File Transfer Protocol) is used for transferring files between systems. Traditional FTP does not encrypt data, making it vulnerable to interception and unauthorized access if not properly configured.

### Service Information

* Port: 21/TCP
* Service: FTP
* Version: vsftpd 2.3.4

---

## Enumeration

Initial enumeration was performed to identify the service version and available features.

### Findings

* FTP service was accessible from the network.
* Version information was successfully obtained.
* Service responded to connection requests.

---

## Anonymous Login Testing

### Objective

To determine whether users can access the FTP server without valid credentials.

### Result

* Anonymous Login: Enabled / Disabled
* Access Level: Read Only / Read-Write

### Security Impact

Anonymous access may expose sensitive files and directories to unauthorized users.

---

## Credential Security Assessment

### Objective

To identify weak, default, or easily guessable credentials.

### Result

* No weak credentials found / Weak credentials identified.

### Risk

Weak passwords can allow attackers to gain unauthorized access to files stored on the server.

---

## File Permission Review

### Objective

To verify access controls on files and directories.

### Findings

* Publicly accessible directories identified.
* Sensitive files exposed / No sensitive files exposed.

### Risk

Improper permissions may allow unauthorized users to read, modify, or delete important data.

---

## FTP Recommendations

* Disable anonymous login unless absolutely necessary.
* Enforce strong password policies.
* Restrict directory permissions.
* Use SFTP or FTPS instead of plain FTP.
* Regularly update FTP software.

---

# SSH Security Assessment

## Overview

SSH (Secure Shell) is a secure protocol used for remote administration and management of systems. Proper configuration is essential to prevent unauthorized access.

### Service Information

* Port: 22/TCP
* Service: SSH
* Version: OpenSSH

---

## Enumeration

The SSH service was enumerated to gather version and configuration information.

### Findings

* SSH service detected successfully.
* Version information collected.
* Service available for remote connections.

---

## Authentication Security Testing

### Objective

To assess the strength of authentication mechanisms.

### Findings

* Password authentication enabled.
* Default credentials not identified.
* Multi-factor authentication not configured (if applicable).

### Risk

Weak authentication mechanisms may increase the risk of unauthorized access.

---

## Root Login Assessment

### Objective

To determine whether direct root login is permitted.

### Findings

* Root Login: Enabled / Disabled

### Risk

Allowing direct root login increases the attack surface and can lead to complete system compromise if credentials are obtained.

---

## SSH Configuration Review

### Areas Reviewed

* Password Authentication
* Root Login Settings
* Supported Encryption Algorithms
* Login Restrictions
* Session Timeout Configuration

### Findings

The SSH configuration was reviewed against common security best practices.

---

## SSH Recommendations

* Disable direct root login.
* Use SSH key-based authentication.
* Implement account lockout policies.
* Restrict SSH access to authorized users.
* Change default configurations where appropriate.
* Keep OpenSSH updated with the latest security patches.

---

# Risk Summary

| Finding                   | Severity |
| ------------------------- | -------- |
| Anonymous FTP Access      | Medium   |
| Weak Credentials          | High     |
| Improper File Permissions | Medium   |
| Root SSH Login Enabled    | High     |
| Outdated Service Version  | Medium   |

---

# Conclusion

The security assessment successfully evaluated the SSH and FTP services running on the target system. Several security checks were performed, including service enumeration, authentication testing, permission review, and configuration analysis. Any identified vulnerabilities should be remediated according to the recommendations provided in this report to improve the overall security posture of the system.

This assessment was conducted for educational and authorized penetration testing purposes only.
