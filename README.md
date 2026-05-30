# Vulnerability Assessment of OWASP Juice Shop

## Project Overview

This project presents a passive security assessment conducted on the OWASP Juice Shop web application. The objective was to identify security misconfigurations, information disclosure issues, and missing security controls using ethical and non-intrusive techniques.

The assessment was performed as part of a Cybersecurity Internship and focused exclusively on passive reconnaissance and vulnerability analysis without exploiting any vulnerabilities or affecting the target system.

---

## Objective

The primary objectives of this assessment were:

- Perform passive security testing on a publicly accessible web application.
- Identify exposed services and server information.
- Analyze HTTP security headers.
- Detect information disclosure vulnerabilities.
- Assess risks associated with discovered findings.
- Provide remediation recommendations based on industry best practices.

---

## Scope and Ethical Considerations

This assessment was conducted under the following restrictions:

- Passive scanning techniques only.
- No exploitation of identified vulnerabilities.
- No brute-force attacks.
- No denial-of-service testing.
- No authentication bypass attempts.
- Assessment limited to publicly accessible resources.

---

## Tools Used

| Tool | Purpose |
|--------|----------|
| Nmap | Port and service enumeration |
| OWASP ZAP | Passive vulnerability scanning |
| Browser Developer Tools | HTTP header analysis |
| Kali Linux | Security testing environment |
| Canva | Report preparation and documentation |

---

## Methodology

The following methodology was followed during the assessment:

1. Target website selection.
2. Service and port reconnaissance using Nmap.
3. Passive vulnerability scanning using OWASP ZAP.
4. HTTP response header inspection.
5. Risk classification of findings.
6. Recommendation and remediation planning.

---

## Key Findings

### 1. Service and Port Exposure

**Identified Services:**
- HTTP (Port 80)
- HTTPS (Port 443)
- FTP (Port 21)

**Detected Technologies:**
- Apache HTTP Server
- BIG-IP Load Balancer

**Risk Level:** Low

**Impact:**
Exposed services and version information can assist attackers during reconnaissance and vulnerability identification.

**Recommendations:**
- Disable unnecessary services.
- Restrict public access to unused ports.
- Hide server banner information.

---

### 2. Missing Content Security Policy (CSP)

**Risk Level:** Medium

**Description:**
The application does not implement a Content Security Policy (CSP) header.

**Potential Impact:**
- Cross-Site Scripting (XSS) attacks
- Session hijacking
- Malicious script execution
- Content manipulation

**Recommended Fix:**

```http
Content-Security-Policy: default-src 'self';
```

---

### 3. Missing X-Content-Type-Options Header

**Risk Level:** Low

**Description:**
The anti-MIME-sniffing security header was not configured.

**Potential Impact:**
Browsers may incorrectly interpret content types, potentially allowing malicious files to execute.

**Recommended Fix:**

```http
X-Content-Type-Options: nosniff
```

---

### 4. Information Disclosure Through Comments

**Risk Level:** Low

**Description:**
HTML comments and internal implementation details were exposed in the source code.

**Potential Impact:**
- Leakage of sensitive information
- Increased effectiveness of reconnaissance activities
- Easier identification of application structure

**Recommendations:**
- Remove unnecessary comments from production environments.
- Avoid exposing internal development information.
- Conduct secure code reviews before deployment.

---

### 5. HTTP Response Header Analysis

**Observed Issues:**
- Server information disclosure
- Missing security headers
- Cache configuration exposure

**Risk Level:** Low

**Recommendations:**
- Configure security-related HTTP headers.
- Minimize information disclosure.
- Follow secure web server configuration guidelines.

---

## Risk Summary

| Vulnerability | Severity |
|--------------|----------|
| Missing CSP Header | Medium |
| Missing X-Content-Type-Options Header | Low |
| Information Disclosure | Low |
| Server Version Disclosure | Low |

---

## Security Recommendations

- Implement Content Security Policy (CSP).
- Configure X-Content-Type-Options header.
- Remove unnecessary information disclosure.
- Hide server and application version details.
- Perform regular vulnerability assessments.
- Follow OWASP secure configuration guidelines.
- Conduct periodic security audits and reviews.

---

## Learning Outcomes

Through this project, I gained practical experience in:

- Vulnerability Assessment
- Passive Reconnaissance
- Web Application Security
- OWASP Top 10 Concepts
- Security Header Analysis
- Risk Assessment
- Security Reporting
- Nmap and OWASP ZAP Usage

---

## References

- OWASP: https://owasp.org
- OWASP ZAP: https://www.zaproxy.org
- Nmap: https://nmap.org

---

## Conclusion

The assessment identified multiple low and medium-risk security misconfigurations, primarily related to missing security headers and information disclosure. While no critical vulnerabilities were discovered, implementing the recommended remediation measures would significantly strengthen the application's overall security posture and improve its resilience against common web-based attacks.

---

## Author

**THIRUKUMARAN S**  
Cybersecurity Intern  
B.E. Computer Science and Engineering (Cyber Security)
