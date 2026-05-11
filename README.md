# File-and-Data-Integrity-Checks

Packet Tracer – File and Data Integrity Checks
Cybersecurity Investigation & Integrity Verification Project

This project demonstrates practical cybersecurity skills in file recovery, integrity verification, hashing, HMAC validation, and incident escalation using Cisco Packet Tracer and a Linux security environment.

The lab simulates a real-world cyberattack scenario where company files may have been altered after a compromise. The investigation focuses on identifying tampered files using cryptographic hashing techniques and validating sensitive financial data using HMAC authentication.

Project Overview
Scenario

A company experiences a suspected cyberattack affecting archived client records stored on its network. As the security analyst, your responsibility is to:

Recover archived files
Verify file integrity using MD5 hashes
Identify compromised files
Escalate suspicious findings
Validate sensitive financial records using HMAC-SHA256

The environment includes:

Branch Office systems
HQ backup servers
FTP services
Linux forensic workstation (CSE-LABVM)
Objectives
Part 1 — Recover Files After a Cyberattack
Access backup servers
Download archived files via FTP
Prepare forensic verification environment
Part 2 — Verify File Integrity Using Hashing
Generate MD5 hashes
Compare hashes against original archives
Detect altered files
Report findings to management
Part 3 — Verify File Integrity Using HMAC
Generate SHA256 HMAC signatures
Validate sensitive financial documents
Understand why HMAC is more secure than traditional hashing
Tools & Technologies Used
Tool	Purpose
Cisco Packet Tracer	Network simulation
VirtualBox	Running security VM
OpenSSL	HMAC generation
Linux Terminal	Hash generation
MD5 Hashing	File integrity checks
HMAC-SHA256	Authenticated integrity verification
FTP	File retrieval
Email Client	Incident escalation
Part 1 — File Recovery Investigation
Step 1 — Access Branch Server

Connected to:

http://branch.corp

Downloaded the latest archived client files.

Step 2 — Obtain Original Hash Values

Accessed:

http://hq.corp

Copied original file hashes for comparison.

Step 3 — Download Backup Files via FTP
FTP Connection
ftp hq.corp
Credentials
Username: mike
Password: cisco123
Retrieve Files
get NEclients.txt
get NWclients.txt
get Nclients.txt
get SEclients.txt
get SWclients.txt
get Sclients.txt
Verify Downloads
dir
Part 2 — Hashing & File Integrity Validation
MD5 Hash Verification
Command Used
echo -n 'file-content' | md5sum

Each downloaded file was hashed and compared against the original archived hash values.

Investigation Findings
Integrity Verification Results
File	Status
NEclients.txt	Valid
NWclients.txt	Valid
Nclients.txt	Valid
SEclients.txt	Tampered
SWclients.txt	Valid
Sclients.txt	Valid
Security Incident Detected

The file:

SEclients.txt

produced a different MD5 hash value compared to the archived original.

This indicates:

Unauthorized modification
Possible malware injection
Data corruption
Insider manipulation
Integrity compromise
Incident Escalation

An email notification was sent to:

sally@branch.corp

to report:

Suspected compromise
File integrity failure
Need for forensic analysis
Evidence Preservation

The compromised file was securely transferred to Sally’s workstation for deeper forensic investigation.

FTP Commands
ftp hq.corp
Credentials
Username: sally
Password: cisco321
Download Tampered File
get SEclients.txt
Part 3 — HMAC Integrity Verification
Objective

Verify the integrity of a sensitive financial document:

income.txt

using authenticated hashing.

HMAC Generation

OpenSSL Command

openssl dgst -sha256 -hmac cisco123 income.txt

# Why HMAC Is More Secure Than Standard Hashing

# Traditional Hashing (MD5/SHA)

Verifies integrity only

Cannot confirm authenticity

Vulnerable if attacker recalculates hashes

# HMAC

Uses a secret cryptographic key

Verifies:

Integrity

Authenticity

Prevents attackers from generating valid signatures without the secret key

# Cybersecurity Concepts Demonstrated

Digital Forensics

Incident Response

File Integrity Monitoring

Secure Backup Verification

Cryptographic Validation

Hash-Based Authentication

Evidence Preservation

Security Escalation Procedures

Security Lessons Learned

# Key Findings

Hash verification is critical after cyber incidents

Even a one-character change alters the hash completely

HMAC provides stronger integrity assurance than regular hashing

Backups should always be verified before restoration

# Recommendations
Improve Organizational Security By:

Implementing automated File Integrity Monitoring (FIM)

Using SHA256 instead of MD5

Enforcing secure backup policies

Monitoring unauthorized file modifications

Encrypting sensitive archives

Deploying centralized logging and SIEM solutions

Applying strict access control to FTP servers
