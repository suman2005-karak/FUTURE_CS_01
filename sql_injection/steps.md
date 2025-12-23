# SQL Injection – DVWA (Step-by-Step Process)

## 1. Objective
The objective of this experiment is to identify and exploit an SQL Injection vulnerability in the Damn Vulnerable Web Application (DVWA) in order to understand how improper input validation can allow attackers to manipulate backend databases.

---

## 2. Application Details
- Application Name: Damn Vulnerable Web Application (DVWA)
- Vulnerability Type: SQL Injection
- Module Tested: SQL Injection
- Security Level: Low

---

## 3. Test Environment
- Operating System: Kali Linux / Windows
- Web Browser: Firefox / Chromium
- Application Hosting: DVWA (Docker)
- URL: http://localhost:8080/
- Testing Method: Manual testing using browser input fields

---

## 4. Pre-Conditions
Before performing SQL Injection testing, the following conditions were ensured:
1. DVWA was running successfully.
2. User logged in using valid credentials (admin / password).
3. DVWA security level was set to LOW.
4. SQL Injection module was accessible from the DVWA menu.

---

## 5. Steps Performed

### Step 1: Login to DVWA
- Open the browser.
- Navigate to http://localhost:8080/
- Login using:
  - Username: admin
  - Password: password

### Step 2: Set Security Level
- Click on “DVWA Security” from the left menu.
- Set the security level to LOW.
- Click Submit.

### Step 3: Access SQL Injection Module
- From the DVWA left panel, click on “SQL Injection”.
- The page displays an input field to enter a User ID.

### Step 4: Normal Input Testing
- Enter a valid numeric input such as `1`.
- Observe that a single user record is returned.
- This confirms normal application behavior.

### Step 5: Inject Malicious SQL Payload
- Enter the following payload into the input field:
' OR '1'='1 --


### Step 6: Analyze the Response
- The application returns multiple database records instead of a single user.
- This indicates that the SQL query logic has been manipulated.
- Authentication and data filtering were bypassed.

---

## 6. Payload Used
' OR '1'='1 --


## 7. Observation
The application directly concatenates user input into SQL queries without sanitization or validation. As a result, the injected payload modifies the query logic and returns unauthorized data.

---

## 8. Impact Analysis
- Unauthorized access to sensitive database records
- Possibility of authentication bypass
- Exposure of user credentials
- Complete database compromise in real-world scenarios

Impact Level: **High**

---

## 9. OWASP Top 10 Mapping
- OWASP Top 10 (2021): **A03 – Injection**

---



## 10. Remediation Recommendations
To prevent SQL Injection attacks, the following measures are recommended:
- Use prepared statements and parameterized queries
- Implement strict server-side input validation
- Use ORM frameworks
- Apply least-privilege access to database accounts
- Enable proper error handling

---