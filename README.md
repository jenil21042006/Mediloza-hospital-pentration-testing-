# Mediroza General Hospital — Black-Box Penetration Testing

**Networkwalks Academy — Week 4 Training Project**

> ⚠️ **Disclaimer:** This project was conducted as a simulated cybersecurity training exercise in an authorised lab environment. The target is a fictional training website. No real hospital, patient, employee, or individual data was involved. The techniques documented here must only be used on systems for which explicit permission has been granted.

## Project Overview

This project demonstrates a black-box penetration testing assessment of a simulated hospital web application. The objective was to identify security weaknesses, validate vulnerabilities through controlled testing, assess their potential impact, and document remediation recommendations.

| Category | Details |
|---|---|
| Client | Mediroza General Hospital (Simulated) |
| Target | `https://medirozahospital.com` |
| Engagement Type | Black-Box Web Application Penetration Test |
| Duration | 5 Days |
| Project | Networkwalks Academy – Week 4 |
| Author | **Jenil Patel** |
| Objective | Identify and document web application security vulnerabilities |

## Tools and Technologies Used

- **PowerShell / curl** — HTTP requests, session handling and response analysis.
- **Web Browser** — Application navigation and vulnerability validation.
- **PowerShell Select-String / Get-Content** — Response parsing and data extraction.
- **Networkwalks Hash Calculator** — PDF encryption hash extraction.
- **Networkwalks Password Cracker** — Offline dictionary attack lab.
- **John the Ripper Wordlist** — Extended dictionary testing.
- **PDF Viewer** — Verification of recovered PDF documents.

## Summary of Security Findings

| ID | Vulnerability | Risk |
|---|---|---|
| F1 | Sensitive path disclosure through robots.txt | Low |
| F2 | SQL Injection – Authentication Bypass | Critical |
| F3 | Insecure Direct Object Reference (IDOR) | High |
| F4 | Weak PDF Encryption Passwords | Medium |
| F5 | Publicly Accessible Database Backup | Critical |

---

## M1 — Initial Access and Reconnaissance

### F1: Sensitive Path Disclosure Through robots.txt

The initial reconnaissance phase involved examining the website's publicly accessible `robots.txt` file.

The file disclosed several restricted-looking directories, including:

- `/patient/`
- `/staff/`
- `/old/`

Although robots.txt is designed to guide search engine crawlers, it does not provide authentication or access control.

**Security Impact:**
- Reveals potentially sensitive application paths.
- Helps attackers identify additional areas for investigation.
- May expose poorly protected legacy resources.

**Recommendation:** Restrict sensitive directories using server-side access controls rather than relying on robots.txt.

### F2: SQL Injection — Authentication Bypass

The patient login functionality was assessed for improper input handling.

During testing, a SQL injection payload was used to demonstrate an authentication bypass in the simulated environment.

**Affected Endpoint:** `/patient/login.php`

**Security Impact:**
- Unauthorised portal access.
- Potential exposure of protected application functionality.
- Possible access to sensitive patient resources.

**Recommendation:**
- Use parameterised SQL queries.
- Implement server-side input validation.
- Apply secure authentication mechanisms.
- Avoid dynamically concatenating untrusted input into SQL statements.

### F3: Insecure Direct Object Reference (IDOR)

The patient report download functionality was assessed for broken object-level authorisation.

The application used sequential document identifiers through the `download.php?id=N` endpoint.

Testing demonstrated that access to individual records was not properly restricted to the authorised user.

**Security Impact:**
- Unauthorised access to other users' documents.
- Potential exposure of confidential records.
- Violation of data confidentiality.

**Recommendation:**
- Implement server-side ownership verification.
- Apply role-based access controls.
- Use unpredictable identifiers as an additional defence.
- Validate authorisation for every document request.

---

## M2 — PDF Encryption and Password Security Assessment

The downloaded simulated patient reports were encrypted PDF documents.

The assessment examined whether weak document passwords could be recovered through controlled offline dictionary attacks.

### PDF Assessment Results

| File | Password Testing Result |
|---|---|
| report1.pdf | Password recovered |
| report2.pdf | Password recovered |
| report3.pdf | Password recovered |

### Key Observations

- Common passwords were susceptible to dictionary attacks.
- Weak password policies reduced document confidentiality.
- Password-protected documents should not be treated as a replacement for access control.

**Recommendation:**
- Enforce strong, randomly generated passwords.
- Use modern encryption standards.
- Protect sensitive documents through authenticated portals.
- Apply appropriate encryption key management.

---

## M3 — Critical Data Exposure Assessment

### F5: Publicly Accessible Legacy Database Backup

During the assessment, the previously identified `/old/` directory was investigated further.

A legacy database backup was identified as publicly accessible in the simulated environment.

**File:** `mediroza_db_backup_2019.sql`

The backup contained simulated organisational records, including:

- Shareholder information.
- Employee names and designations.
- Department information.
- Contact information.
- National identification fields.
- Salary information.

### Security Impact

A publicly accessible database backup can result in significant confidentiality and privacy risks.

Potential consequences include:

- Exposure of employee personal information.
- Unauthorised disclosure of financial information.
- Organisational privacy violations.
- Increased risk of identity-related fraud.

**Recommendation:**
- Store database backups outside publicly accessible directories.
- Restrict access through authentication and network controls.
- Encrypt backup files.
- Regularly audit web server directories.
- Implement secure backup retention policies.

---

## M4 — Final Security Assessment

The assessment identified multiple security weaknesses across the simulated hospital application.

### Overall Findings

| Finding | Severity | Recommended Priority |
|---|---|---|
| robots.txt Disclosure | Low | P3 |
| SQL Injection | Critical | P1 |
| IDOR | High | P1 |
| Weak PDF Passwords | Medium | P2 |
| Exposed Database Backup | Critical | P1 |

### Key Security Recommendations

1. Implement parameterised SQL queries throughout the application.
2. Enforce object-level authorisation for every sensitive resource.
3. Apply strong password policies and modern document encryption.
4. Remove database backups from publicly accessible directories.
5. Implement secure authentication and session management.
6. Conduct regular vulnerability assessments and security audits.
7. Follow secure development and deployment practices.

---

## Skills Demonstrated

- Web Application Penetration Testing
- Black-Box Security Assessment
- SQL Injection Analysis
- IDOR Vulnerability Assessment
- HTTP Request Analysis
- Session and Authentication Testing
- PDF Encryption Assessment
- Dictionary Attack Concepts
- Sensitive Data Exposure Analysis
- Security Reporting and Remediation

## Project Evidence

Screenshots and supporting evidence from the authorised lab exercise are organised below.

| Evidence | Description |
|---|---|
| 01 | robots.txt disclosure |
| 02 | SQL injection and IDOR links |
| 03 | Patient report download assessment |
| 04 | Retrieved file sizes |
| 05 | PDF hash extraction |
| 06 | First PDF password assessment |
| 07 | Second PDF password assessment |
| 08 | Initial dictionary assessment |
| 09 | Extended wordlist |
| 10 | Final PDF password assessment |

*Replace these evidence descriptions or filenames if your actual screenshots differ.*

---

## Conclusion

This project provided practical exposure to web application penetration testing and demonstrated how multiple security weaknesses can combine to create serious risks.

The assessment highlighted the importance of secure authentication, proper authorisation, strong encryption, and secure handling of sensitive organisational information.

The project strengthened my understanding of vulnerability identification, controlled exploitation, security impact analysis, and professional penetration testing documentation.

---

**Author:** Jenil Patel  
**Cybersecurity Student**  
**Project:** Networkwalks Academy — Week 4 Training Project

*All activities were conducted in an authorised simulated training environment for educational purposes.*# Mediloza-hospital-pentration-testing-
