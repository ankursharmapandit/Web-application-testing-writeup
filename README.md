# 🔐 Username Enumeration & Brute-Force Attack Lab - PortSwigger

## 📌 Overview
This repository is dedicated to solving authentication vulnerability labs from **PortSwigger**, focusing on **username enumeration** and **brute-force attacks**. The lab showcases how attackers exploit minor differences in login responses to discover valid usernames and subsequently brute-force passwords. 

---

## 🚀 Steps to Solve the Lab

### 🛠 Step 1: Understanding the Vulnerability
Some web applications provide **subtle differences** in login error messages or HTTP status codes, making it possible to:
- Enumerate valid usernames.
- Perform a **brute-force attack** to discover weak passwords.

Our approach will involve:
✅ Capturing a login request with fake credentials.
✅ Testing a list of possible usernames to identify a valid one.
✅ Performing a **password brute-force attack** on the valid username.

---

### 🔍 Step 2: Capturing & Analyzing the Login Request
1️⃣ Navigate to the **login page** and enter fake credentials (e.g., `fakeuser:fakepass`).
2️⃣ Use **Burp Suite** to **intercept** the login request.
3️⃣ Identify the **POST request** (e.g., `/login`).
4️⃣ Observe the **response message**:
   - If the response is `"Invalid username or password."`, it may indicate that the username is being checked first.
   - If different responses occur for valid and invalid usernames, enumeration is possible.

---

### 🎯 Step 3: Username Enumeration
Now, we will identify a valid username by testing different ones:

1️⃣ Send the captured request to **Intruder (Burp Suite)**.
2️⃣ Select **Sniper mode** (to test usernames one by one).
3️⃣ Set the **username field** as the **injection point**.
4️⃣ Load a **wordlist** of common usernames:
    ```
    carlos
    root
    admin
    test
    guest
    info
    adm
    mysql
    user
    administrator
    oracle
    ```
5️⃣ Configure **Grep - Match** to track the phrase **"Invalid username or password."**
6️⃣ Start the attack 🚀 and analyze the results:
   - If one username produces a **different response** (e.g., lacks an error message or returns an **HTTP 302 Redirect**), it is likely valid.

💡 **Pro Tip:** Some apps show an **identical error message** for valid and invalid usernames, but a slight difference in **response time** can still indicate valid users.

---

### 🔑 Step 4: Password Brute-Force Attack
Once a valid username is identified (e.g., `carlos`), we attempt to brute-force its password.

1️⃣ Send another login request using `carlos:fakepassword`.
2️⃣ Forward the request to **Intruder**.
3️⃣ Set the **password field** as the **payload position**.
4️⃣ Load a list of commonly used passwords:
    ```
    123456
    password
    12345678
    qwerty
    123456789
    12345
    1234
    111111
    1234567
    dragon
    123123
    baseball
    abc123
    ```
5️⃣ Adjust **Grep - Match** settings:
   - `"Invalid username or password."` (to filter failed attempts).
   - **HTTP 302 Redirect** (to identify a successful login).
6️⃣ Start the attack and **find the correct password**!

🚨 **Warning:** This method is unethical if used without permission. Always follow **ethical hacking** guidelines.

---

### ✅ Step 5: Logging In & Completing the Lab
1️⃣ Use the discovered **username** and **password** to log in.
2️⃣ Navigate to the **account page**.
3️⃣ 🎉 Successfully complete the lab!

---

## 🎓 Key Takeaways
💡 **Username enumeration** exploits slight differences in **error messages** or **response times**.
💡 **Brute-force attacks** work when **rate limiting** or **account lockout** policies are missing.
💡 **Burp Suite’s Intruder tool** is highly effective for automating these attacks.
💡 Always analyze the **response pattern** carefully to detect vulnerabilities.

---

## 🔒 Prevention Techniques
To **prevent** such attacks, developers should:
✔️ Use **generic error messages** (e.g., "Login failed.")
✔️ Implement **rate limiting** to block multiple failed login attempts.
✔️ Enforce **account lockout** after several failed attempts.
✔️ Require **multi-factor authentication (MFA)** for added security.
✔️ Monitor logs to detect and **block brute-force attacks**.

---

## 📜 Disclaimer
This guide is for **educational purposes only**. Do not attempt unauthorized access to any system. Always obtain **legal permission** before performing security testing.

🚀 **Happy Ethical Hacking!** 🔥

