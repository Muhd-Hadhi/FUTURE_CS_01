# FUTURE_CS_01
Future Intern Cybersecurity Task 1 : Vulnerability Assessment Report for a Live Website
Security Assessment Report: testphp.vulnweb.com
This repository contains the findings of a professional security consulting engagement conducted to analyze the public-facing website  for common security weaknesses. The assessment utilized a strictly ethical, read-only methodology to identify risks such as misconfigured headers, outdated frameworks, and unintentional information exposure.

Project Overview
Target URL:  
Prepared By: Muhammed Hadhi K P 
Date: March 2, 2026 
Project ID: 001 

Methodology & Tools :
The assessment followed standard penetration testing phases: Planning, Discovery, Attack, and Reporting.

The following industry-standard tools were used for scanning and validation:
1.Nuclei 
2.OpenVAS 
3.Burpsuite 
4.Gobuster 

Summary of Findings
The audit identified a total of 9 major records categorized by severity based on CVSSV3 scores:

Key Vulnerabilities Identified :
1. SQL Injection (Critical)
The login page and various parameters (e.g., product.php?pic=1) were found vulnerable to SQL injection.
Impact: Attackers can bypass authentication using commands like ' or '1'='1 and access sensitive database tables, including user credentials and credit card numbers.

2. Sensitive Information Disclosure (Critical/High)
Multiple instances of sensitive data exposure were discovered:
Credentials in Plaintext: User login credentials were found in a publicly accessible credentials.txt file and displayed openly on the signup page.
Directory Indexing: The /admin and /CVS directories were visible, exposing organizational logs and history.
System Files: It was possible to obtain the /etc/passwd file by manipulating the showimage.php file parameter.

3. Reflected Cross-Site Scripting (Critical)
The search bar was vulnerable to reflected XSS using payloads.
Impact: Attackers could run malicious code in a victim's browser to steal session information or redirect users to malicious sites.

4. Broken Authentication & Weak Policy (High)
Brute-force: The login page lacked rate-limiting, allowing for successful trial-and-error attacks.
Weak Passwords: The system allowed four-character passwords and lacked Multi-Factor Authentication (MFA).

General Recommendations :
Input Validation: Implement parameterized queries and prepared statements to prevent SQL injection.
Access Control: Remove publicly accessible credential files and restrict access to sensitive directories like /admin.
Encryption: Transition the website from HTTP to HTTPS to ensure all data is transmitted in encrypted form.
Authentication Hardening: Implement account lockout thresholds, enforce strong password policies (minimum 8 characters with symbols), and enable MFA.

Disclaimer: This penetration test is a snapshot in time. Findings reflect the security posture at the time of testing and do not account for modifications made after March 15, 2026.
