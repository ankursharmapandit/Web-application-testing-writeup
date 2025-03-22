# 🔐 Password Reset Broken Logic - Exploitation Guide

**📅 Last Edited:** March 19, 2025  
**✍️ Author:** Ankur Sharma  

## 🎯 Objective
The purpose of this lab is to identify and exploit a vulnerability in the password reset functionality. By leveraging this flaw, we will reset Carlos’s password and gain unauthorized access to his **"My Account"** page.

---

## 🔑 Lab Credentials
- **👤 Your Credentials:** `wiener:peter`
- **🎯 Victim's Username:** `carlos`

---

## 🚀 Step-by-Step Exploitation

### 1️⃣ Identifying the Vulnerability ⚠️
The password reset mechanism in this application is flawed due to:
- **❌ Lack of proper identity verification**, allowing unauthorized password resets.
- **🔓 Absence of token validation** or a secure authentication mechanism, making it susceptible to manipulation.

### 2️⃣ Initiating the Password Reset Process 🔄
1. Navigate to the **🔑 Login Panel** and locate the **Forgot Password** functionality.
2. Enter the username `wiener` and request a password reset.
3. This triggers an email containing a **🔗 password reset link**.

### 3️⃣ Capturing the Password Reset Request 🎯
To manipulate the request, use **Burp Suite**:
- 🛑 **Intercept** the request when submitting the password reset form.
- 🔍 Locate the reset request in **HTTP history** under the **Proxy** tab.
- 📤 Send the captured request to **Repeater** for modification.

### 4️⃣ Modifying the Request to Target Carlos 🎭
- Within the intercepted request, identify the **username parameter** (`wiener`).
- ✏️ Change `wiener` to `carlos` to attempt resetting Carlos’s password.
- 🏆 If the application does not verify email ownership, it will accept the modified request.

### 5️⃣ Sending the Manipulated Request 📡
- 📩 Forward the **modified request** to the server.
- ✅ If successful, you will receive a response confirming that **Carlos's password has been reset**.

### 6️⃣ Logging in as Carlos 🔓
- Return to the **🔑 Login Page** and enter:
  - **👤 Username:** `carlos`
  - **🔑 New Password:** *(the password set in the manipulated request)*
- 🎉 Upon successful login, navigate to the **"My Account"** page to confirm the exploit worked.

---

## 🔍 Security Implications 🚨
This vulnerability arises due to **insufficient authentication checks** during the password reset process. A secure implementation should:
- 🛡 **Require a unique, time-sensitive token** for password resets.
- 📧 **Ensure the token is tied to the correct user** and verify it via email confirmation.
- 🔒 **Restrict password resets** to only valid email recipients.

## 🏁 Conclusion
By exploiting broken logic in the password reset mechanism, we were able to reset Carlos’s password and gain unauthorized access to his account. This highlights a **critical security flaw in authentication workflows** that could be exploited by malicious actors if not properly mitigated.

---

## 🔧 Recommendations for Fixing This Vulnerability ✅
To prevent such attacks, applications should implement **robust password reset mechanisms**, including:
- 🔐 **Multi-Factor Authentication (MFA):** Require additional verification (e.g., OTP via email/SMS).
- 🔑 **Strong Token Validation:** Ensure password reset links are single-use, time-limited, and associated with the correct email.
- 📊 **Logging and Monitoring:** Implement monitoring to detect abnormal password reset requests.
- 📩 **User Notifications:** Send alerts when password reset attempts are made.

By addressing these issues, organizations can significantly **reduce the risk of unauthorized account takeovers** and **improve security** in authentication workflows. 🔒🚀


![Picture15](https://github.com/user-attachments/assets/04dc635a-d921-467a-85aa-d2dcb4b87b80)
![Picture16](https://github.com/user-attachments/assets/85e02e53-4a8b-4f86-92c6-3f1ea9e49b0b)
![Picture17](https://github.com/user-attachments/assets/04cd9873-ab5c-436f-b1f3-3838685706cf)
<img width="468" alt="Picture18" src="https://github.com/user-attachments/assets/2ee8ebb6-8f4d-4c83-848f-55b0c480ef1f" />
![Picture19](https://github.com/user-attachments/assets/2f699fb4-1471-408b-a957-5ee8b6f66113)
![Picture20](https://github.com/user-attachments/assets/29e8a178-0172-4464-88d3-6b980e712fcf)
