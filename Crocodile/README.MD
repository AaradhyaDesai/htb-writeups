
#  HTB: Crocodile — Writeup

## Overview

* **Machine Name:** Crocodile
* **Difficulty:** Easy
* **Platform:** Hack The Box (Starting Point)
* **Category:** Web / Enumeration / Credential Abuse

Crocodile is a beginner-friendly machine that focuses on **web enumeration, directory brute-forcing, and credential usage**. The key lesson here is understanding how **hidden endpoints and exposed files** can lead to authentication bypass or access.

## Attack Flow

```
1. Recon (Nmap Scan)
        ↓
2. Web Enumeration
        ↓
3. Directory Brute Force (Gobuster)
        ↓
4. Discover Login Endpoint (login.php)
        ↓
5. Use Credentials
        ↓
6. Gain Access
```

## Tools Used

* `nmap`
* `gobuster`
* `curl` (optional)
* Web browser

---

## MITRE ATT&CK Mapping

| Technique | Description                  |
| --------- | ---------------------------- |
| T1595     | Active Scanning              |
| T1083     | File and Directory Discovery |
| T1078     | Valid Accounts               |

---
## Skills Learned

* Directory brute-forcing using Gobuster
* Identifying hidden login endpoints
* Understanding web authentication mechanisms
* Using credentials effectively
* Basic web enumeration workflow

---
---

## Objective

Gain access to the web application by discovering hidden resources and using provided credentials.

---

---

## Step 1: Enumeration (Nmap)

Start with a basic scan:

```bash
nmap -sC -sV <target-ip>
```

### Findings:

* Port **80 (HTTP)** open
* Web server hosting a simple webpage

---

## Step 2: Web Application Analysis

Visit:

```
http://<target-ip>
```

### Observation:

* Basic webpage
* No visible login form
* No obvious attack surface



---

## Step 3: Directory Brute Forcing

Since nothing is visible, we enumerate hidden directories:

```bash
gobuster dir -u http://<target-ip>/ -w /usr/share/wordlists/dirb/common.txt -x php
```

### Important Flag:

* `-x php` → tells Gobuster to search for `.php` files

---

## Step 4: Key Discovery

Gobuster reveals:

```
/login.php
```

-> This is the **hidden authentication endpoint**

---

##  Step 5: Authentication

You were given credentials earlier in the lab.

Navigate to:

```
http://<target-ip>/login.php
```

Enter credentials → Login successful

---

## Step 6: Access Granted

After login:

* You gain access to the protected area
* The flag or required information is displayed

---

## Screenshots

![Step 1](./screenshot/screenshot_16.jpeg)

![Step 2](./screenshot/screenshot_12.jpeg)

![Step 3](./screenshot/screenshot_10.jpeg)

![Step 4](./screenshot/screenshot_5.jpeg)

![Step 5](./screenshot/screenshot_1.jpeg)

![Step 6](./screenshot/screenshot_17.jpeg)

![Step 7](./screenshot/screenshot_14.jpeg)

![Step 8](./screenshot/screenshot_11.jpeg)

![Step 9](./screenshot/screenshot_6.jpeg)

![Step 10](./screenshot/screenshot_2.jpeg)

![Step 11](./screenshot/screenshot_18.jpeg)

![Step 12](./screenshot/screenshot_13.jpeg)

![Step 13](./screenshot/screenshot_8.jpeg)

![Step 14](./screenshot/screenshot_7.jpeg)

![Step 15](./screenshot/screenshot_3.jpeg)

![Step 16](./screenshot/screenshot_15.jpeg)

![Step 17](./screenshot/screenshot_9.jpeg)

![Step 18](./screenshot/screenshot_4.jpeg)


---

## Key Findings

### 1. Hidden Endpoints

* Login page was not linked anywhere
* Only discoverable via brute force

### 2. Importance of File Extensions

* Without `-x php`, Gobuster might miss:

  ```
  login.php
  ```

### 3. Credential Usage

* Having credentials is useless without knowing **where to use them**

---


## Commands Summary

```bash
# Nmap Scan
nmap -sC -sV <target-ip>

# Directory Brute Force
gobuster dir -u http://<target-ip>/ \
-w /usr/share/wordlists/dirb/common.txt \
-x php
```

---


## Lessons Learned

* Always perform **directory enumeration**, even if the site looks simple
* Hidden endpoints are very common in real-world applications
* File extensions matter during brute forcing
* Enumeration is often more important than exploitation

---

## 🏁 Conclusion

Crocodile teaches a fundamental concept in penetration testing:

> **“If you can’t see it, enumerate it.”**

Even when an application appears minimal, **hidden functionality often exists**, and tools like Gobuster help uncover it. This machine reinforces the importance of combining **enumeration + logic + credentials** to achieve access.

---
