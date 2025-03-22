# 🔐 PortSwigger Authentication Vulnerability Lab: Broken Brute-Force Protection (Multiple Credentials Per Request)

## 🏆 Objective
This lab contains a **logic flaw** in its **brute-force protection mechanism**. Our goal is to:

✅ Brute-force **Carlos's password** 🔑  
✅ Log into **his account** 🕵️‍♂️  
✅ Access **Carlos's account page** 🖥️

---

## 🚀 Step 1: Initial Login Attempt

1. **Navigate to the login page** of the lab.
2. **Enter the victim’s username** with any incorrect password attempt:
   - **Username:** `carlos`
   - **Password:** (any incorrect attempt)
3. **Observe the error message** indicating an incorrect password.
4. **Capture the login request** using **Burp Suite** for further analysis.

---

## 🎯 Step 2: Identifying the Vulnerability

1. **Send the captured request** to **Burp Repeater**.
2. **Examine the request structure**, especially how the **username and password** are transmitted.
3. **Identify the flaw:** The brute-force protection only checks for **multiple requests**, but it does **not** properly handle **multiple credentials in a single request**.

---

## 🔓 Step 3: Modifying the Request for Brute-Force Attack

Instead of sending **multiple login requests**, we modify the request to include **multiple credentials in a single request** using a **string format**.

### 📝 Modified Request Format:
```http
POST /login HTTP/1.1
Host: vulnerable-lab.com
Content-Type: application/x-www-form-urlencoded

username="carlos"&password="123456,password,12345678,qwerty,letmein,football"
```

1. **Insert multiple passwords** from a common **password wordlist** into a single request.
2. **Send the modified request** using **Burp Intruder** or **Burp Repeater**.
3. **Look for a successful response**, indicated by **HTTP status 200 (OK) or 302 (Redirect)**.

---

## 🎯 Step 4: Extracting the Correct Password

1. **Analyze the responses** to identify the password that triggered a **302 redirect** or successful login.
2. **Retrieve the correct password** and use it to log in as Carlos.

---

## 🏁 Step 5: Accessing Carlos's Account Page

1. **Log in with Carlos’s credentials:**
   - **Username:** `carlos`
   - **Password:** (the cracked password)
2. **Navigate to Carlos’s account page** and confirm access.
3. ✅ **Lab successfully completed!** 🎉

---

## 📌 Conclusion

🔹 **Brute-force protection flaws** can be exploited if authentication mechanisms allow **multiple credentials in a single request**.  
🔹 **Rate limiting and IP-based monitoring** are essential to **prevent such attacks**.  
🔹 **Mitigation strategies:**  
   - Enforce **single password attempts per request** 🔒  
   - Implement **multi-factor authentication (MFA)** for enhanced security 📲  
   - Monitor and **limit login attempts based on behavior** 🛑  

---

⚠️ **Ethical Disclaimer:** This guide is for **educational purposes only**. Always follow ethical hacking practices and obtain permission before testing security vulnerabilities. 🛡️

---

✍️ **Author:** Ankur Sharma  
📅 **Date Edited:** Today
![Picture10](https://github.com/user-attachments/assets/419c47b7-dfbc-4335-a667-86e279e639b2)
![Picture11](https://github.com/user-attachments/assets/34061349-39b3-4c28-9a72-2b090581abe7)
![Picture12](https://github.com/user-attachments/assets/a48badea-ef4f-4b94-aea5-43524ee9ebfc)
![Picture13](https://github.com/user-attachments/assets/5415ce9e-e10b-4bf8-97da-4263b1243878)




