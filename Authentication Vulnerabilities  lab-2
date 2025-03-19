# 🔓 PortSwigger Lab - 2FA Simple Bypass

**Author:** Ankur Sharma  
**Date:** March 19, 2025  

## 📝 Overview
This lab demonstrates a vulnerability in two-factor authentication (2FA) that allows an attacker to bypass the second authentication layer. In this scenario, we already possess valid credentials but do not have access to the user's 2FA verification code. The objective is to successfully bypass 2FA and gain unauthorized access to **Carlos's account page**. 🚀

## 🔑 Provided Credentials
- **🕵️ Attacker's Credentials:** `wiener:peter`
- **🎯 Target's Credentials:** `carlos:montoya`

## 🛠️ Steps to Bypass 2FA

### 1️⃣ Capturing Authentication Requests with Burp Suite
1. 🏁 Launch **Burp Suite** and configure the proxy to intercept HTTP traffic.
2. 🔍 Log in using the attacker's credentials (`wiener:peter`) to analyze the authentication flow.
3. 📡 Observe the request structure when submitting the username and password.
4. 🚨 Identify the **2FA verification request** that follows the credential submission.

### 2️⃣ Understanding the 2FA Mechanism
1. 🔢 The lab implements a basic **4-digit numeric 2FA code**.
2. ✉️ This code is submitted via a separate **POST request** after successful login.
3. 🎰 Since there are only **10,000 possible codes (0000-9999)**, a brute-force attack is highly feasible.

### 3️⃣ Exploiting the 2FA Bypass via Brute Force
1. 🎭 Log in using **Carlos's credentials (`carlos:montoya`)** and intercept the 2FA request.
2. 🛑 Identify the parameter responsible for submitting the 2FA code (e.g., `POST /verify`).
3. 🚀 Forward this request to **Burp Intruder** to automate brute-force attempts.
4. ⚙️ Configure **Burp Intruder**:
   - 🔫 Set the attack type to **Sniper mode**.
   - 🎯 Select the **2FA code field** as the payload position.
   - 🔢 Use a sequential payload list ranging from **0000 to 9999**.

### 4️⃣ Executing the Brute Force Attack
1. ▶️ Start the attack using **Burp Intruder**.
2. 📡 Monitor responses and look for a **200 OK status** or a **redirect to the user dashboard**, indicating a successful 2FA bypass.
3. 🔓 Once the valid **2FA code** is identified, manually submit it to access **Carlos’s account page**.

### 5️⃣ Confirming the Exploit
✅ Upon successful authentication, navigate to **Carlos’s account page** and verify unauthorized access.
⚠️ This confirms that the 2FA mechanism has been successfully bypassed.

## 🛡️ Mitigation Strategies
To prevent similar vulnerabilities in real-world applications, the following security measures should be implemented:

1. 🚧 **Rate-Limiting:** Restrict the number of login attempts to mitigate brute-force attacks.
2. 🔑 **Strong 2FA Codes:** Use **alphanumeric OTPs** instead of predictable numeric codes.
3. 📲 **User Interaction:** Require additional verification through email or mobile device.
4. 🚫 **Account Lockout Mechanisms:** Temporarily lock accounts after multiple failed authentication attempts to deter automated attacks.
5. 🕵️ **Behavioral Analysis:** Implement anomaly detection to identify suspicious login patterns.

By adopting these best practices, organizations can significantly improve their security posture and prevent **2FA bypass attacks**. 🔒

![Picture12](https://github.com/user-attachments/assets/912525ad-384c-4904-84f4-7e17dae6e661)
![Picture13](https://github.com/user-attachments/assets/1c605a1e-0703-4f1a-ae71-12a17fe3cfca)
![Picture14](https://github.com/user-attachments/assets/a4025a7d-f2e5-446f-b5fc-57f9c97e7827)
![picture 15 1](https://github.com/user-attachments/assets/17c99585-848d-41f9-b24f-d9eec5a2e925)
![Picture15](https://github.com/user-attachments/assets/c4b24793-eb44-40f4-97ab-7b5f8c62fb99)


