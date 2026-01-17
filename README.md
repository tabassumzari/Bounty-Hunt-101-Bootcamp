# Bounty-Hunt-101-Bootcamp
A comprehensive penetration testing report and lab setup for the Bounty Hunt 101 bootcamp. This repository documents the end-to-end bug bounty lifecycle—from reconnaissance with Nmap to exploiting XSS, SQL Injection and IDOR vulnerabilities in a containerized OWASP Juice Shop environment.


🛡️ Bug Bounty Project: Bounty-Hunt-101-Bootcamp
Author: Tabassum Jilani Zari

Target: OWASP Juice Shop (v14.3.1)

Tools: Nmap, Burp Suite Community Edition, Docker Desktop

Status: ✅ Project Completed

📋 Executive Summary
This project demonstrates the end-to-end bug bounty lifecycle conducted in a containerized environment. The objective was to identify and exploit critical vulnerabilities listed in the OWASP Top 10, ranging from reconnaissance to advanced broken access control.

🔍 Phase 1: Reconnaissance (Recon)
The first phase involved identifying open services and the technology stack of the target system.

Tool Used: Nmap.

Command: nmap -sV -p 3000 localhost.

Findings: Port 3000 was identified as open, running a Node.js/Express framework.

Proof of Concept:https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/Reconnaissance%20Nmap.png

🛠️ Phase 2: Vulnerability Research & Exploitation
1. Cross-Site Scripting (XSS)
Vulnerability Type: DOM-based XSS.

Attack Vector: Search Functionality.

Payload: <iframe src="javascript:alert('xss')">.

Description: The search parameter q is reflected in the DOM without proper sanitization, allowing for arbitrary JavaScript execution.

Proof of Concept:https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/xss1.png
                 https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/xss2.png

2. SQL Injection (SQLi)
Vulnerability Type: Authentication Bypass.

Attack Vector: Login Page.

Payload: ' OR 1=1 --.

Description: By injecting a logic bypass into the email field, the backend database query returns 'True' for all conditions, effectively bypassing the password check.

Impact: Gained complete Administrative access to the application.

Proof of Concept:https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/SQL%20Injection1.png
                 https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/SQL%20Injection2.png

3. Insecure Direct Object Reference (IDOR)
Vulnerability Type: Broken Access Control.

Tool: Burp Suite Repeater.

Method: I intercepted the request for Basket ID #6 and manually modified the "Direct Object Reference" to ID #4.

Description: The application fails to verify if the currently logged-in user has authorization to access the requested resource ID.

Proof of Concept:https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/Juiceshop.png
                https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/Actual%20Order%20History.png
                https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/Burpe%20suite-IDOR.png
                https://github.com/tabassumzari/Bounty-Hunt-101-Bootcamp/blob/7f6c7e59e84e5a7b5c4349e3306ec6c737e502a7/Repeater%206%20to%204.png

🏁 Phase 3: Final Achievements
The project was successfully completed with the following results:

Scoreboard Access: Successfully discovered the hidden scoreboard page.

Challenge Progress: Verified 1% of total challenges completed for the 5-day bootcamp milestone.
