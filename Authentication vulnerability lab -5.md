# ⏳ Username Enumeration via Response Timing - PortSwigger Lab

📌 **Author:** Ankur Sharma  
📅 **Date:** 03/19/2025  

## 🔐 Overview
This repository is dedicated to solving authentication vulnerability labs from **PortSwigger**, specifically focusing on **username enumeration via response timing**. The goal is to:
✅ Exploit a **response timing vulnerability** to enumerate valid usernames.  
✅ Perform a **password brute-force attack** on the identified username.  
✅ Successfully log in and gain access to the account page.  

---

## 🚀 Steps to Solve the Lab

### 🛠 Step 1: Initial Login & Request Interception
1️⃣ Log in using the provided test credentials:
   - **Username:** `wiener`  
   - **Password:** `peter`  
2️⃣ Open **Burp Suite** and enable **Intercept** in the **Proxy** tab.  
3️⃣ Attempt to log in with **random credentials** (e.g., `randomuser:randompass`) and **capture the request**.  
4️⃣ Send the captured request to **Repeater**:  
   - Right-click → **Send to Repeater**.

---

### 🔍 Step 2: Analyze the Login Request
1️⃣ Observe the **HTTP request structure**, which usually includes:
   - **Username** and **password** fields in the request body.
   - Potential **response time differences** when testing with different usernames.
2️⃣ If there is **no immediate difference** in responses, introduce an **X-Forwarded-For** header to manipulate request flow.

💡 **Why use X-Forwarded-For?** Some web applications process login requests differently based on IP addresses. By modifying this header, we can create artificial delays, making enumeration easier.

---

### 🎯 Step 3: Username Enumeration via Response Timing
1️⃣ **Send the request to Intruder:**  
   - Right-click → **Send to Intruder**.
2️⃣ **Configure the attack:**  
   - **Attack Type:** **Pitchfork** (allows testing two payloads at the same time).  
   - **Payload Positions:**  
     - Insert a **payload position** in the `X-Forwarded-For` header.
     - Insert a **payload position** in the `username` field.
3️⃣ **Set up the payloads:**  
   - **Payload 1 (X-Forwarded-For Header):** Use a **numeric range (1-100)** to introduce artificial delays.
   - **Payload 2 (Username List):** Load a **wordlist** containing potential usernames.
4️⃣ **Start the Intruder Attack:**  
   - Observe the **response times** — a **valid username** will show a **longer response time** than invalid ones.
   - Identify the **valid username** based on timing variations.

💡 **Tip:** If response time differences are subtle, try increasing the numeric range for X-Forwarded-For payloads.

---

### 🔑 Step 4: Brute-Forcing the Password
Now that we have a **valid username**, the next step is to brute-force the password.

1️⃣ **Send the request to Intruder again:**  
   - Right-click → **Send to Intruder**.
2️⃣ **Set Attack Type to Pitchfork** (allows testing multiple usernames and passwords simultaneously).  
3️⃣ **Configure payload positions:**  
   - **First Payload (Username Field):** Use the **valid username** found in Step 3.
   - **Second Payload (Password Field):** Use a **common password wordlist**.
4️⃣ **Load the payloads:**  
   - **Payload 1 (Username):** The valid username obtained from enumeration.
   - **Payload 2 (Passwords):** Use a known password list (e.g., `rockyou.txt`, `top1000.txt`).
5️⃣ **Start the attack:**  
   - Look for a **200 OK response** or **change in response content**, indicating a successful login.

🚨 **Warning:** Brute-force attacks are unethical unless performed with legal authorization for security testing.

---

### ✅ Step 5: Logging In & Verifying Access
1️⃣ Use the discovered **username** and **password** to manually log in.  
2️⃣ Navigate to the **account page** to confirm successful access.  
3️⃣ 🎉 **Lab successfully completed!**  

---

## 🌟 Key Takeaways
✔ **Response Timing Analysis** is an effective technique for username enumeration.  
✔ **X-Forwarded-For Header Manipulation** can be leveraged to introduce artificial delays.  
✔ **Burp Suite Intruder (Pitchfork Attack)** efficiently automates username and password brute-forcing.  
✔ **A systematic approach** ensures a structured and professional penetration testing methodology.  

💡 **Pro Tip:** When securing applications, developers should implement **consistent response times**, rate-limiting, and CAPTCHA mechanisms to prevent enumeration attacks.

---

## 🔒 Prevention Techniques
To **prevent** such attacks, developers should:
✔️ Implement **consistent error messages and response times** for both valid and invalid usernames.  
✔️ Use **rate-limiting** to block multiple failed login attempts.  
✔️ Enforce **account lockout** after several incorrect attempts.  
✔️ Require **multi-factor authentication (MFA)** to strengthen security.  
✔️ Monitor logs to detect and block **brute-force attempts**.

---

## 📜 Disclaimer
This guide is for **educational purposes only**. Do not attempt unauthorized access to any system. Always obtain **legal permission** before performing security testing.

🚀 **Happy Ethical Hacking!** 🔥
![Picture25](https://github.com/user-attachments/assets/458ae49b-78d9-473b-965b-48a1f3abb980)
<img width="468" alt="Picture26" src="https://github.com/user-attachments/assets/ba01afd0-2af7-4b4c-a1c0-a5af0e082b32" />
<img width="468" alt="Picture27" src="https://github.com/user-attachments/assets/4952e72f-27fb-4e0b-b538-5ee2d30f3cc5" />
<img width="468" alt="Picture28" src="https://github.com/user-attachments/assets/5b3f179c-268d-42e0-85fb-18a22b6573a0" />
<img width="468" alt="Picture29" src="https://github.com/user-attachments/assets/036a5aea-bb13-42b8-9419-2053017248ee" />
<img width="468" alt="Picture30" src="https://github.com/user-attachments/assets/b6ecfbfd-af22-459b-abae-e3c3791bb151" />
![Picture31](https://github.com/user-attachments/assets/4915bbf5-2076-466e-bac9-0e1525da7810)

