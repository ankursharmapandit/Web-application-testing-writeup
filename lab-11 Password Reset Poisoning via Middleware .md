# 🔐 Lab: Password Reset Poisoning via Middleware

## 🎯 Objective
This lab is vulnerable to **password reset poisoning**, allowing an attacker to manipulate the password reset functionality to gain access to a victim's account. The target user, **Carlos**, is known to click on any link received via email.

Our goal is to **exploit the vulnerability** and successfully log in to Carlos's account. 🚀

---

## 🛠 Steps to Solve the Lab

### 1️⃣ Log in to Your Own Account
1. Navigate to the **login page**.
2. Use the provided credentials to log in:
   - **Username**: `wiener`
   - **Password**: `peter`
3. Once logged in, open the **email client** on the exploit server to intercept and view emails.

---

### 2️⃣ Initiate the Password Reset Process
1. On the login page, click **"Forgot Password"** to initiate the reset process.
2. Enter the username: `wiener`.
3. A **password reset email** will be sent to the email client on the exploit server.

---

### 3️⃣ Capture and Modify the Password Reset Request
1. Use **Burp Suite** or another proxy tool to **capture the forgot password request**.
2. Locate the `Host` and `X-Forwarded-Host` headers.
3. Modify the **X-Forwarded-Host** header to point to the **exploit server URL**.

---

### 4️⃣ Change the Target Username to Carlos
1. Resend the **modified request** using the Repeater tool.
2. Verify that the response returns **200 OK**.
3. Open the **email client** on the exploit server and check for a **new password reset email** (meant for Carlos). 📩

---

### 5️⃣ Extract and Use the Reset Token
1. Retrieve the **password reset link** from Carlos’s email.
2. Copy the **reset token** from the link.
3. Use the **modified reset token** to access the password reset page.

---

### 6️⃣ Reset Carlos's Password and Log In
1. Enter a **new password** for Carlos’s account.
2. Use the **new credentials** to log in as Carlos.
3. Successfully access Carlos’s account and **complete the lab**! ✅

---

## 🏁 Conclusion
By leveraging **password reset poisoning** via the `X-Forwarded-Host` header, we successfully hijacked Carlos's password reset process. 🔓

### 🔥 Key Takeaways:
✔ **Middleware vulnerabilities** can be exploited to manipulate security mechanisms in web applications.
✔ **Email-based password reset** flows should be properly secured to prevent host header poisoning.
✔ **Burp Suite** is an essential tool for identifying and exploiting authentication vulnerabilities.
✔ **Always analyze response behaviors** to detect weak implementations in password reset mechanisms.

---

📌 **Author:** Ankur Sharma  
📅 **Date:** 19th March 2025  

![Picture43](https://github.com/user-attachments/assets/46312ca1-4ae6-4d95-8f8c-0d6ef2d9dbc5)
![Picture44](https://github.com/user-attachments/assets/c6b7a9f5-694e-41e7-829b-350c1ad3b49a)
<img width="468" alt="Picture45" src="https://github.com/user-attachments/assets/a517d4b4-7555-4341-b14e-c5a5a9bea398" />
<img width="468" alt="Picture46" src="https://github.com/user-attachments/assets/3f87f92f-bb11-4a57-ba21-09fe4ad089ff" />
![Picture47](https://github.com/user-attachments/assets/3746a2a6-2919-4d3f-94e3-3c8e6fd4a8f3)
<img width="468" alt="Picture48" src="https://github.com/user-attachments/assets/a5bdbd42-b40c-4ea2-8928-15c42e684615" />
<img width="468" alt="Picture49" src="https://github.com/user-attachments/assets/5458cb19-660e-47d1-9f30-de95954bc9cb" />
