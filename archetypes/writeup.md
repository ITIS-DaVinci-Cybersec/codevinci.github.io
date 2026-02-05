---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
description: "Writeup for CHALLENGE_NAME from CTF_NAME"
summary: "Brief description of the challenge and solution approach"

# CTF Information
categories:
  - "CTF_NAME"
tags:
  - "web"        # Change to: pwn, crypto, reverse, forensics, misc
  - "medium"     # Difficulty: easy, medium, hard, insane
series:
  - "CTF_NAME 2026"

# Post display options
showToc: true
TocOpen: true
hidemeta: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowCodeCopyButtons: true

# Cover image (optional)
cover:
    image: ""  # Path to cover image
    alt: "Challenge cover"
    caption: ""
    relative: false
    hidden: false

# Author (optional, defaults to site author)
author: "Your Name"
---

## 📋 Challenge Info

| Property | Value |
|----------|-------|
| **CTF** | CTF_NAME |
| **Challenge** | CHALLENGE_NAME |
| **Category** | Web / Pwn / Crypto / Reverse / Forensics / Misc |
| **Difficulty** | ⭐ Easy / ⭐⭐ Medium / ⭐⭐⭐ Hard |
| **Points** | XXX |
| **Solves** | XXX |
| **Author** | Challenge Author |

---

## 📝 Description

> Original challenge description goes here.
> Can be multiple lines.

**Files provided:**
- `file1.py` - Description
- `file2.zip` - Description

**Connection info:**
```
nc challenge.ctf.com 1337
```

---

## 🔍 Analysis

### Initial Reconnaissance

Describe your initial analysis here...

### Vulnerability Discovery

What vulnerability did you find?

```python
# Vulnerable code snippet
def vulnerable_function():
    pass
```

---

## 💡 Solution

### Step 1: Description

Explain the first step...

```python
# Code for step 1
```

### Step 2: Description

Explain the second step...

```python
# Code for step 2
```

### Final Exploit

```python
#!/usr/bin/env python3
"""
Exploit for CHALLENGE_NAME - CTF_NAME
Author: Your Name
"""

from pwn import *

def exploit():
    # Your exploit code here
    pass

if __name__ == "__main__":
    exploit()
```

---

## 🚩 Flag

```
flag{example_flag_here}
```

---

## 📚 Lessons Learned

- What did you learn from this challenge?
- Any new techniques discovered?
- References and resources

---

## 🔗 References

- [Reference 1](https://example.com)
- [Reference 2](https://example.com)
