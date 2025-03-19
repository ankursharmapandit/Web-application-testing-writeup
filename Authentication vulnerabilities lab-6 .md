# 🔑 Professional Approach to Solving '2FA Broken Logic' Lab

📌 **Author:** Ankur Sharma  
📅 **Date:** 03/19/2025  

## 🚀 Objective
The goal of this lab is to **exploit a flawed two-factor authentication (2FA) mechanism** to gain unauthorized access to **Carlos's account** by bypassing weak security controls.

---

## 🛠 Step 1: Log in with Provided Credentials
1️⃣ Navigate to the lab's **login page**.  
2️⃣ Use the provided test credentials:
   - **Username:** `wiener`  
   - **Password:** `peter`  
3️⃣ Open **Burp Suite** and enable **Intercept** in the **Proxy** tab.  
4️⃣ Capture the login request and analyze its structure.  
   - Identify the **parameters** used in authentication.
   - Look for any **hidden fields** that might affect the login flow.

💡 **Tip:** Always review the request-response behavior before proceeding to exploitation.

---

## 🔍 Step 2: Identifying the 2FA Mechanism
1️⃣ Observe the authentication process after logging in.
2️⃣ Identify the request that is sent for **2FA verification**.
3️⃣ Submit **incorrect codes** and note how the system responds:
   - Does the response contain any **error messages**?
   - Are there any **response time differences**?
   - Does the system **lock out** users after multiple failed attempts?

📌 **Key Insight:** Many broken 2FA implementations rely on **short numeric codes** without proper rate-limiting, making them vulnerable to brute-force attacks.

---

## 🎯 Step 3: Exploiting 2FA via Brute Force
Now that we understand the 2FA mechanism, let's attempt a **brute-force attack** using Burp Suite Intruder.

1️⃣ **Send the captured 2FA request to Burp Suite Intruder:**  
   - Right-click the request → **Send to Intruder**.
2️⃣ **Configure the attack:**  
   - **Attack Type:** Sniper (best for testing a single parameter).  
   - **Payload Position:** Insert the payload in the **2FA code parameter**.
3️⃣ **Load a numeric payload:**  
   - Use a **4-digit numeric range (0000-9999)** as the payload.
4️⃣ **Start the Intruder attack:**  
   - Monitor the **response patterns**.
   - Look for a **different response length** or a **status code 200 OK/302 Redirect** to identify the correct 2FA code.

🚨 **Warning:** Brute-force attacks on real-world applications without permission are illegal. Always obtain **explicit authorization** before performing security tests.

---

## 🔓 Step 4: Using the Correct 2FA Code
1️⃣ Once the **valid 2FA code** is identified, manually enter it on the login page.  
2️⃣ Successfully **log in as Carlos** and navigate to his **account page** to confirm access.  
3️⃣ 🎉 **Lab successfully completed!**  

---

## 🌟 Key Takeaways
✔ **Weak 2FA implementations** that rely on short numeric codes are highly susceptible to brute-force attacks.  
✔ **Burp Suite Intruder** automates testing for all possible 2FA codes efficiently.  
✔ **Identifying response variations** (status codes, response length) helps in detecting successful authentication.  
✔ **Proper security measures** should enforce:
   - **Rate limiting** on failed 2FA attempts.
   - **Account lockout mechanisms** after multiple incorrect tries.
   - **Additional verification layers**, such as CAPTCHA or device-based authentication.

💡 **Pro Tip:** A secure 2FA implementation should use **time-based OTPs (TOTP)** or **hardware-based authentication**, making brute-force attacks nearly impossible.

---

## 🔒 Prevention Techniques
To **prevent** such vulnerabilities, developers should:
✔️ Implement **rate-limiting** to restrict multiple failed attempts.  
✔️ Require **multi-factor authentication (MFA)** using secure methods.  
✔️ Enforce **progressive delays** or **account lockout** after failed login attempts.  
✔️ Use **TOTP (Time-Based One-Time Passwords)** instead of static numeric codes.
✔️ Monitor **login attempts** and alert users on suspicious activities.

---

## 📜 Disclaimer
This guide is for **educational purposes only**. Unauthorized security testing on real systems is illegal. Always obtain **explicit legal permission** before performing penetration testing.

🚀 **Happy Ethical Hacking!** 🔥

![Picture32](https://github.com/user-attachments/assets/b6764679-5c7b-4aad-ba4f-4ab3b1686c62)
![Picture33](https://github.com/user-attachments/assets/6e90944c-34ec-41a3-abc1-d670ae24e4e0)
<img width="468" alt="Picture34" src="https://github.com/user-attachments/assets/d7c136cc-41d5-4300-9c45-5bca2c4753d1" />
<img width="468" alt="Picture35" src="https://github.com/user-attachments/assets/634809ad-dc8f-434a-9d13-ee902ea5c3b6" />
![Picture36](https://github.com/user-attachments/assets/a68ae3c5-fb86-41c9-9552-1f85966f63fd)
