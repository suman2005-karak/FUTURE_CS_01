# Cross-Site Scripting (XSS) – DVWA

## 1. Objective
The objective of this experiment is to identify and exploit Cross-Site Scripting (XSS) vulnerabilities in DVWA and understand how malicious scripts can be executed in a victim’s browser.

---

## 2. Application Details
- Application: Damn Vulnerable Web Application (DVWA)
- Vulnerability Type: Cross-Site Scripting (XSS)
- XSS Types: Reflected and Stored
- Security Level: Low

---

## 3. Test Environment
- OS: Kali Linux / Windows
- Browser: Firefox / Chromium
- Hosting: DVWA (Docker)
- URL: http://localhost:8080/

---

## 4. Pre-Conditions
1. DVWA must be running.
2. User must be logged in.
3. Security level must be set to LOW.
4. XSS modules must be accessible.

---

## 5. Reflected XSS Testing

### Step 1: Navigate to Reflected XSS
- Click on “XSS (Reflected)” from the DVWA menu.

### Step 2: Normal Input Test
- Enter a normal string such as `hello`.
- Observe that the same value is reflected back.

### Step 3: Inject Malicious Script
- Enter the following payload:
<script>alert('XSS')</script>
yaml
Copy code

### Step 4: Analyze Response
- A JavaScript alert box appears.
- This confirms execution of injected script.

---

## 6. Stored XSS Testing

### Step 1: Navigate to Stored XSS
- Click on “XSS (Stored)” from the menu.

### Step 2: Inject Payload
- Enter the following payload in the message/comment field:
<script>alert('Stored XSS')</script>
yaml
Copy code

### Step 3: Submit the Form
- Save the input.

### Step 4: Observe Persistent Behavior
- Reload the page.
- Alert executes automatically.
- Confirms stored XSS vulnerability.

---

## 7. Observation
The application does not sanitize or encode user input before displaying it in the browser, allowing arbitrary JavaScript execution.

---

## 8. Impact Analysis
- Cookie theft
- Session hijacking
- Website defacement
- Phishing attacks

Impact Level: **High**

---

## 9. OWASP Mapping
- OWASP Top 10 (2021): **A07 – Cross-Site Scripting (XSS)**

---

## 10. Evidence Collected
1. Reflected XSS input page
2. Alert popup screenshot
3. Stored XSS execution screenshot

---

## 11. Remediation
- Encode output
- Validate input
- Implement Content Security Policy (CSP)
- Use secure frameworks

---

## 12. Conclusion
Both reflected and stored XSS vulnerabilities were successfully demonstrated in DVWA