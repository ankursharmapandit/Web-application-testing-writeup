# 🚀 PortSwigger Authentication Vulnerability Lab: Password Brute-Force via Password Change

## 🎯 Objective
This lab's password change functionality contains a vulnerability that allows brute-force attacks. Our goal is to:

- 🔓 Brute-force Carlos’s password using the password change feature
- 🔑 Gain access to Carlos’s "My Account" page

---

## 📝 Step 1: Initial Login & Password Change Attempt

1. 🔹 Log in using the provided credentials:
   - **👤 Username:** `wiener`
   - **🔑 Password:** `peter`
2. 🔹 Navigate to the password change page.
3. 🔹 Attempt to change the password with incorrect confirmation:
   - **🔄 Current password:** `peter`
   - **🆕 New password:** `peter1234`
   - **✅ Confirm new password:** `peter123`
4. ⚠️ Observe the error message: _“New passwords do not match.”_
5. 📡 Capture this request using Burp Suite.

---

## 🔍 Step 2: Identifying the Vulnerability

1. 🕵️ Analyze the intercepted request in Burp Suite.
2. ✏️ Modify the request:
   - Change the **username** field from `wiener` to `carlos`.
   - The victim’s username (`carlos`) is provided, but the password is unknown.
3. 🎯 This means we can brute-force the password field by injecting multiple candidate passwords.

---

## 💥 Step 3: Performing Brute-Force Attack

1. 📜 Use a password wordlist and insert it into the `new password` field.
2. 🎯 Paste the wordlist into Burp Intruder's payload section.
3. 🔍 Set the grep match for the response:
   - Look for the message _“New passwords do not match”_ (indicating failure).
   - If the message does not appear, the password change was successful.
4. 🔑 Identify the correct password from the response.

---

## ✅ Step 4: Logging in as Carlos & Accessing the Account Page

1. 🔹 Use the cracked credentials:
   - **👤 Username:** `carlos`
   - **🔑 Password:** (the identified correct password)
2. 🔹 Log in to Carlos’s account.
3. 🔹 Navigate to the "My Account" page.
4. 🏆 Lab successfully completed.

---

## 🔒 Conclusion

- 🚨 Password change vulnerabilities can be exploited for brute-force attacks if there are no proper security measures.
- 🔧 Mitigation strategies:
   - 🛡️ Implement rate-limiting and monitoring for password change attempts.
   - 🔐 Require multi-factor authentication (MFA) to prevent unauthorized account takeovers.
   - ✅ Ensure password change validation prevents brute-force exploitation.

---

**⚠️ Ethical Disclaimer:** This guide is for educational purposes only. Always follow ethical hacking practices and obtain permission before testing security vulnerabilities.

---

**✍️ Author:** Ankur Sharma  
**📅 Date Edited:** Today

<img width="960" alt="1" src="https://github.com/user-attachments/assets/ef712085-3ed1-433f-8e81-8122fb5d66f2" />
<img width="960" alt="2" src="https://github.com/user-attachments/assets/a469854b-22d5-43f2-b971-543c5460e26c" />
<img width="960" alt="3" src="https://github.com/user-attachments/assets/25960b3a-0b93-4f02-8d8a-52f388a6f3e7" />
<img width="960" alt="4" src="https://github.com/user-attachments/assets/dabbb892-8cb8-4d80-bb36-1ddd910d1799" />
<img width="960" alt="5" src="https://github.com/user-attachments/assets/3dfdd84c-bd80-42b3-895f-794493b530af" />
<img width="960" alt="6" src="https://github.com/user-attachments/assets/4b1cdc52-bb89-4efb-9ff7-7070dbd43afd" />
<img width="960" alt="7" src="https://github.com/user-attachments/assets/094af5f7-f6dc-4adf-89f4-73d122b9d944" />
