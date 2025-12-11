

# Vulnerable Web Applications: DVWA, XVWA & Building a Custom VWA

This document provides a theoretical overview of DVWA and XVWA, and outlines a structured approach to building a custom Vulnerable Web Application (VWA) for learning, research, and security testing environments.

---

## 1. Damn Vulnerable Web Application (DVWA)

DVWA is a deliberately insecure PHP/MySQL web application designed for cybersecurity training. It helps learners understand common web vulnerabilities and practice exploitation techniques safely in a controlled environment.

### **Key Features**

* Written in PHP with a MySQL backend
* Multiple difficulty levels (Low, Medium, High, Impossible)
* Contains modules for:

  * SQL Injection
  * Command Execution
  * File Upload bypass
  * XSS (Reflected & Stored)
  * CSRF
  * Brute Force
  * Insecure CAPTCHA
* Supports security configuration review through `config.inc.php`
* Often deployed on XAMPP, WAMP, or Docker environments

### **Learning Outcomes**

* Understanding how insecure coding practices create real-world vulnerabilities
* Hands-on exploitation practice
* Familiarity with detection and mitigation methods

---

## 2. Xenotix Vulnerable Web Application (XVWA)

XVWA is a modern vulnerable web application created to simulate real-world web vulnerabilities with updated technologies, unlike DVWA which uses older PHP patterns.

### **Key Features**

* Built using PHP, MySQL, and modern HTML5 components
* Contains realistic vulnerabilities such as:

  * HTML5-based XSS vectors
  * DOM-based XSS
  * SQLi & Authentication bypass
  * OS Command Injection
  * XML External Entity (XXE)
  * Server-Side Request Forgery (SSRF)
  * Insecure Deserialization
* Better representation of modern attack surfaces

### **Learning Outcomes**

* Exposure to attacks targeting contemporary frameworks and technologies
* Understanding DOM-based and client-side security issues
* Practical insight into complex vulnerabilities used in modern web exploitation

---

## 3. How to Build Your Own Custom Vulnerable Web Application (Custom VWA)

The purpose of creating a custom VWA is to design your own controlled environment to understand the root cause of vulnerabilities, experiment with exploit development, and create unique learning modules.

Below is a structured approach.

---

## Step 1: Define Objectives

Before building, clarify what vulnerabilities your VWA should demonstrate:

* SQL Injection
* XSS (Reflected, Stored, DOM)
* CSRF
* File Upload bypass
* Authentication flaws
* Broken Access Control
* RCE / Command Injection
* XXE, SSRF, IDOR
* Cryptographic flaws

This defines your architecture and module structure.

---

## Step 2: Set Up the Technology Stack

Choose a simple and easily manipulatable stack:

* **Backend**: PHP or Python (Flask) or Node.js
* **Database**: MySQL or SQLite
* **Frontend**: HTML/CSS/JavaScript

Why PHP is recommended:

* Easy to make insecure
* Low barrier for setup
* Real-world vulnerabilities are easier to demonstrate

---

## Step 3: Create the Application Structure

Example file layout:

```
/custom-vwa
    /config
        db.php
    /modules
        sql_injection.php
        xss_reflected.php
        xss_stored.php
        csrf.php
        file_upload.php
    /uploads
    index.php
    login.php
    register.php
```

---

## Step 4: Implement Insecure Code Intentionally

Each module should include vulnerable logic.
Examples:

### SQLi (classic)

```php
$query = "SELECT * FROM users WHERE username = '$user'";
```

### XSS (reflected)

```php
echo $_GET['msg'];
```

### File Upload

```php
move_uploaded_file($_FILES['file']['tmp_name'], "uploads/" . $_FILES['file']['name']);
```

### Authentication Bypass

* No password hashing
* Weak session handling

This code must be intentionally flawed and documented.

---

## Step 5: Include Difficulty Levels (Optional but Recommended)

Similar to DVWA:

* Low: direct vulnerability
* Medium: partial sanitization
* High: better sanitization
* Impossible: proper defense

This helps learners gradually understand exploitation and mitigation.

---

## Step 6: Add Logging for Research

Add basic logging to track payloads and usage:

```
logs/requests.log
logs/uploads.log
```

This is extremely useful if the VWA will be used in training labs.

---

## Step 7: Provide Documentation Inside the Project

Include:

* Overview of each vulnerability
* How to exploit it
* How to fix it (secure version)
* Recommended tools (Burp, OWASP ZAP, sqlmap, XSStrike, etc.)

---

## Step 8: Deploy on a Safe Environment

Use:

* Docker
* XAMPP / WAMP
* Localhost VM
* Never deploy to public internet

---

## Step 9: Optional Advanced Additions

If you want your custom VWA to be more realistic, add:

* Token-based authentication
* Role-based access control
* API endpoints with insecure logic
* JWT vulnerabilities
* Insecure cookie handling
* Race conditions

These simulate real-world enterprise applications.

---

## Summary

DVWA and XVWA are foundational tools for learning web exploitation. Creating your own VWA deepens your mastery by forcing you to understand the backend logic that causes vulnerabilities. A well-structured custom VWA becomes a powerful asset for cybersecurity demonstrations, ethical hacking labs, and research.


