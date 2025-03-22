# 🔓 Lab: Username Enumeration via Account Lock

📌 **Author:** Ankur Sharma  
📅 **Date:** 03/19/2025  

## 🎯 Objective
This lab is vulnerable to **username enumeration** due to a **logic flaw** in the account lock mechanism. Our goal is to:
1️⃣ **Enumerate a valid username** by analyzing error messages.  
2️⃣ **Brute-force the password** of the identified user.  
3️⃣ **Log in successfully** and access the account page.  

---

## 🔍 Step 1: Identifying a Valid Username

### 🛠️ Perform a Test Login
1️⃣ Navigate to the **login page** and enter random credentials.
   - **Example:**  
     ```plaintext
     Username: testuser  
     Password: testpassword  
     ```
2️⃣ Observe the error message:
   - ❌ **"Invalid username or password."** → Username does not exist.
   - ❗ **"Invalid password."** → Username exists!

### 🔎 Capture the Login Request in Burp Suite
1️⃣ Open **Burp Suite** and enable **Intercept** in the **Proxy** tab.
2️⃣ Submit a **test login request**.
3️⃣ **Send the request to Burp Intruder:**
   - Right-click → **"Send to Intruder"**.

### 🎯 Set Up Burp Intruder for Username Enumeration
1️⃣ In **Intruder > Positions**, set the **username field** as the payload position.
2️⃣ Keep the **password field** static (or empty).
3️⃣ Select **Attack Type:** `Cluster Bomb`.

### 📂 Load a Username List
1️⃣ Use a **common username wordlist** (e.g., `usernames.txt`).
2️⃣ Use a **null payload** for the password field.

### 🚀 Execute the Attack
1️⃣ Start the attack and **analyze responses**:
   - A **valid username** will return a different error message (`Invalid password` instead of `Invalid username or password`).
2️⃣ Note the **valid username** for the next step.

---

## 🔓 Step 2: Brute-Forcing the Password

### 📡 Capture a Login Request with the Identified Username
1️⃣ Use the **valid username** found in Step 1.
2️⃣ Send the request to **Burp Intruder**.

### ⚙ Configure Burp Intruder for Password Brute-Forcing
1️⃣ Keep the **username field static** (valid username).
2️⃣ Set the **password field** as the **payload position**.
3️⃣ Select **Attack Type:** `Sniper`.

### 🔑 Load a Password List
1️⃣ Use a **common password list** (e.g., `rockyou.txt` or a custom list).

### 🚀 Start the Attack
1️⃣ Look for different responses:
   - ✅ **"Login successful"** → Correct password found!
   - ❌ **"Invalid password"** → Incorrect password.
2️⃣ Identify the **correct password**.

---

## 🔐 Step 3: Logging in and Accessing the Account Page

### 🏆 Use the Discovered Credentials
1️⃣ Enter the **valid username and password** in the login form.
2️⃣ Click **Log in** to access the account.

### 📜 Verify Lab Completion
1️⃣ If the credentials are correct, you will be logged in.
2️⃣ The **lab will be marked as solved**! 🎉

---

## 🌟 Key Takeaways
✔ **Username enumeration vulnerabilities** can expose valid accounts.  
✔ **Error message analysis** is a powerful technique for identifying existing users.  
✔ **Burp Suite Intruder** automates both **enumeration** and **brute-force attacks**.  
✔ **Weak account lock mechanisms** allow attackers to bypass authentication easily.  

💡 **Pro Tip:** Secure systems should implement **rate-limiting, CAPTCHA, and multi-factor authentication (MFA)** to prevent brute-force attacks.

---

## 🔒 Prevention Techniques
To **prevent** this vulnerability, developers should:
✔️ Implement **rate-limiting** on login attempts.
✔️ Enforce **progressive delays** or **account lockout** after multiple failures.
✔️ Avoid revealing specific **error messages** (use generic messages like "Login failed").
✔️ Require **multi-factor authentication (MFA)** to enhance security.
✔️ Monitor **login attempts** and alert users on **suspicious activity**.

---

## 📜 Disclaimer
This guide is for **educational purposes only**. Unauthorized security testing on real systems is illegal. Always obtain **explicit legal permission** before performing penetration testing.

🚀 **Happy Ethical Hacking!** 🔥

<img width="468" alt="Picture37" src="https://github.com/user-attachments/assets/b3758733-2747-4cce-aa87-f83a2a5dc5a9" />

![Picture38](https://github.com/user-attachments/assets/57285960-5550-407b-a3f0-5b5cda89e563)

![Picture39](https://github.com/user-attachments/assets/a60b6638-d883-40b8-ba4c-488b2366fb5c)

![Picture40](https://github.com/user-attachments/assets/eb307c96-0388-45ee-b104-1a04156eccb7)

![Picture41](https://github.com/user-attachments/assets/4f0f2937-8e05-4da7-bfdc-bc76a33ee2c4)

![Picture42](https://github.com/user-attachments/assets/d60b357a-0fbd-4f61-bc82-32d7b9782a3d)
