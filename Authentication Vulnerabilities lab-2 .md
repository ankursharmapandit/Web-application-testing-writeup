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

![Picture12](https://github.com/user-attachments/assets/6be69016-4651-48c4-a9ee-4cb245735bea)
![Picture13](https://github.com/user-attachments/assets/e73a97d4-1975-4062-ac02-5a9fc233b940)
![Picture14](https://github.com/user-attachments/assets/f7474385-18c4-400f-b0f9-faed0cd605f3)
![picture 15 1](https://github.com/user-attachments/assets/8aa75bd0-76c5-484d-bbcf-6c4d3ab42542)
![Picture15](https://github.com/user-attachments/assets/31e21b7c-4805-488b-bd46-bc42f6da8dd6)


