# Web Application Testing Writeup

## 📌 Overview
Web application testing involves assessing security vulnerabilities, authentication mechanisms, and potential attack vectors that can be exploited by malicious actors. This write-up focuses on **authentication vulnerabilities** found in PortSwigger Labs, outlining their risks, exploitation methods, and mitigation strategies.

## ⚠️ Authentication Vulnerabilities
Authentication flaws allow attackers to bypass security controls and gain unauthorized access to sensitive data. Common vulnerabilities include:

- **Brute-force attacks** 🔓
- **Username enumeration** 🕵️‍♂️
- **Logic flaws in authentication mechanisms** ⚠️

### 🔍 How Authentication Vulnerabilities Arise
- 🔄 **Logic flaws** in authentication workflows.
- 🔑 **Weak credential policies** (e.g., weak passwords allowed).
- 🚫 **Lack of account lockout mechanisms**, making brute-force attacks feasible.
- ❗ **Inconsistent response messages**, enabling username enumeration.

## 📑 Table of Contents
1. [Lab 1: Username Enumeration via Different Responses](#-lab-1-username-enumeration-via-different-responses)
2. [Step-by-Step Exploitation](#-step-by-step-exploitation)
3. [Impact of Exploiting This Vulnerability](#-impact-of-exploiting-this-vulnerability)
4. [Mitigation Strategies](#-mitigation-strategies)

## 🏴‍☠️ Lab 1: Username Enumeration via Different Responses

### 🔍 Overview
This lab demonstrates a vulnerability where an application provides different responses based on whether a username exists. Attackers exploit this behavior to enumerate valid usernames and perform brute-force attacks.

🔗 **Lab Link:** [PortSwigger Authentication Labs](https://portswigger.net/web-security/all-labs#authentication)

## 🚀 Step-by-Step Exploitation

### 🔹 Step 1: Identify Predictable Usernames
Attackers use common usernames such as:
```plaintext
carlos
admin
peter
winner
```
These can be guessed manually or extracted from public wordlists like SecLists.

### 🔹 Step 2: Enumerate Valid Usernames Using Burp Suite

#### 1️⃣ Intercept the Login Request
- Open **Burp Suite** and navigate to **Proxy > Intercept**.
- Capture a failed login request with a sample username and incorrect password.

#### 2️⃣ Analyze the Response
- Observe how the application responds to incorrect usernames.
- Compare it with the response for an incorrect password but a valid username.

#### 3️⃣ Automate Username Enumeration with Intruder
- Go to **Intruder > Positions** and select the username field.
- Choose **Attack Type: Sniper**.
- Load a wordlist and start the attack.

#### 4️⃣ Interpret the Results
- If responses differ, the listed usernames exist in the system.
- Extract the valid usernames for the next phase.

### 🔹 Step 3: Password Brute-Forcing

#### 1️⃣ Set Up Burp Intruder for Password Attacks
- Select a **valid username** and set the attack position on the password field.
- Load a password wordlist (e.g., `rockyou.txt`).

#### 2️⃣ Run the Attack
- Start the attack and monitor responses.
- A successful login will return a different response (e.g., **status 200 OK** or a redirect).

## ⚠️ Impact of Exploiting This Vulnerability
- Attackers can **enumerate all valid users** 👤
- With a valid username, they can **execute brute-force attacks** 🚀
- If **MFA is not enforced**, the attack may lead to **full account takeover** 🛑

## 🔒 Mitigation Strategies
✅ Implement **consistent error messages** for incorrect usernames and passwords.
✅ Enforce **account lockouts** after multiple failed login attempts.
✅ Require **Multi-Factor Authentication (MFA)** 🔑.
✅ Monitor and **rate-limit authentication requests** to detect brute-force attempts.

---
![pitcur 1](https://github.com/user-attachments/assets/41d43ce0-6a8c-4b89-9d93-4b74379b38e1)
![Picture2](https://github.com/user-attachments/assets/557c6fac-2163-4fc9-880d-9b7a398cd0f0)
![Picture3](https://github.com/user-attachments/assets/1d0239b6-d6ce-4781-8153-3c98fc8b511a)


✍️ **Author:** Ankur Sharma  
📅 **Last Updated:** 3/19/2025

