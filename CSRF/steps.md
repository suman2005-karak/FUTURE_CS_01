# Cross-Site Request Forgery (CSRF) – DVWA

## 1. Objective
The objective of this experiment is to demonstrate a Cross-Site Request Forgery (CSRF) attack where an authenticated user is forced to perform an unintended action.

---

## 2. Application Details
- Application: DVWA
- Vulnerability Type: CSRF
- Affected Function: Password Change
- Security Level: Low

---

## 3. Test Environment
- OS: Kali Linux / Windows
- Browser: Firefox / Chromium
- Hosting: DVWA (Docker)
- Tool: Custom HTML file

---

## 4. Pre-Conditions
1. User must be logged into DVWA.
2. Security level must be set to LOW.
3. Same browser session must be used.

---

## 5. Attack Steps

### Step 1: Navigate to CSRF Module
- Click on “CSRF” from DVWA menu.
- Observe password change form.

### Step 2: Identify Vulnerability
- Password change request uses GET.
- No CSRF token present.

### Step 3: Create Malicious HTML File
- A fake HTML page is created that auto-submits the request.

### Step 4: Execute Attack
- Open `csrf.html` while logged in.
- Password changes automatically.

---

## 6. Result Verification
- Logout from DVWA.
- Login using new password `csrf123`.
- Login successful.

---

## 7. Observation
The application does not verify request origin, allowing attackers to exploit authenticated sessions.

---

## 8. Impact Analysis
- Account takeover
- Unauthorized actions
- Loss of user trust

Impact Level: **Medium**

---

## 9. OWASP Mapping
- OWASP Top 10 (2021): **A01 – Broken Access Control**

---

## 10. Evidence Collected
1. CSRF page
2. csrf.html code
3. Successful login screenshot

---

## 11. Remediation
- Implement CSRF tokens
- Use POST requests
- Validate Origin and Referer headers

---

## 12. Conclusion
The CSRF vulnerability was successfully exploited, demonstrating the risks of missing request validation.