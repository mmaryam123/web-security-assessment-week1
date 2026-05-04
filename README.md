# web-security-assessment

My First Cybersecurity Vulnerability Assessment Project

## Target Application

- Application: OWASP Juice Shop  
- URL: http://localhost:3000  

---

## Target Application Setup Guide

- Install Node.js (required to run the application)
- Clone the OWASP Juice Shop repository:
  git clone https://github.com/juice-shop/juice-shop.git --depth 1
- Go into the project folder:
  cd juice-shop
- Install dependencies:
  npm install
- Start the application:
  npm start
- Open in browser:
  http://localhost:3000  

---

## Vulnerabilities Found

<img width="191" height="101" alt="image" src="https://github.com/user-attachments/assets/fa764c5f-306a-4c52-b724-e7470bdf39b6" />
<img width="191" height="56" alt="image" src="https://github.com/user-attachments/assets/44f17c4d-f60a-4cf5-a95f-f70761a68f64" />

### Missing Security Headers
- Content Security Policy (CSP) not set  
- Strict-Transport-Security (HSTS) not enabled  
- X-Frame-Options missing  
- X-Content-Type-Options missing  

---

### CORS Misconfiguration
- Access-Control-Allow-Origin is set to *  
- This allows any website to access application data  

---

### Insecure Communication
- Application uses HTTP instead of HTTPS  
- Data is transmitted in plain text  

---

### Session Security Issues
- Session ID is passed in URL instead of secure cookies  
- Risk of session hijacking  

---

### Information Disclosure
- Server version information is exposed in response headers  
- Internal IP address is revealed  

---

## Cross-Site Scripting (XSS) / SQL Injection Tests

### XSS Payloads
- <img src=x onerror=alert('XSS')>  
- <iframe src="javascript:alert('XSS')">  

### SQL Injection Payload
- admin' OR 1=1--

---

## Weak Password Storage

During testing, authentication requests were inspected using browser developer tools.  
Sensitive credentials may be transmitted without strong protection mechanisms.

---

## Security Misconfigurations

- Missing CSP header  
- Missing HSTS header  
- Session cookies should use:
  - HttpOnly: true  
  - Secure: true  
- Server information may be exposed in response headers
### Conclusion

This assessment of OWASP Juice Shop identified common vulnerabilities such as XSS, SQL Injection, missing security headers, insecure communication, and session issues. The findings highlight the importance of proper input validation, secure configuration, and use of HTTPS. This project helped in understanding basic web application security and vulnerability testing techniques.
