# OWASP Checklists

## OWASP Top 10 — Web Application

| # | Category | What to Test |
|---|----------|-------------|
| A01 | Broken Access Control | Horizontal/vertical privilege escalation, IDOR, missing function-level access control |
| A02 | Cryptographic Failures | Sensitive data in transit/at rest, weak algorithms, hard-coded keys |
| A03 | Injection | SQL, NoSQL, OS command, LDAP, SSTI injection |
| A04 | Insecure Design | Missing threat modelling, insecure design patterns |
| A05 | Security Misconfiguration | Default credentials, verbose errors, unnecessary features enabled, missing hardening |
| A06 | Vulnerable & Outdated Components | Outdated libraries/frameworks with known CVEs |
| A07 | Identification & Authentication Failures | Weak passwords, credential stuffing, broken session management, missing MFA |
| A08 | Software & Data Integrity Failures | Insecure deserialization, unsigned updates, CI/CD pipeline integrity |
| A09 | Security Logging & Monitoring Failures | Missing logs, no alerting on attacks, insufficient audit trails |
| A10 | Server-Side Request Forgery (SSRF) | Unvalidated URLs fetched server-side, internal network access |

Reference: https://owasp.org/Top10/

---

## OWASP API Security Top 10

| # | Category | What to Test |
|---|----------|-------------|
| API1 | Broken Object Level Authorization (BOLA/IDOR) | Manipulate object IDs in requests to access other users' data |
| API2 | Broken Authentication | Weak tokens, no expiry, improper credential validation |
| API3 | Broken Object Property Level Authorization | Mass assignment, over-exposed properties in responses |
| API4 | Unrestricted Resource Consumption | No rate limiting, large payload abuse, resource exhaustion |
| API5 | Broken Function Level Authorization | Access to admin/privileged endpoints without proper role checks |
| API6 | Unrestricted Access to Sensitive Business Flows | Abuse of legitimate business workflows (e.g., bulk purchase, account enumeration) |
| API7 | Server-Side Request Forgery (SSRF) | API fetches attacker-controlled URLs reaching internal services |
| API8 | Security Misconfiguration | Verbose errors, default configs, missing TLS, unnecessary HTTP methods |
| API9 | Improper Inventory Management | Undocumented/shadow APIs, outdated API versions still accessible |
| API10 | Unsafe Consumption of APIs | Trusting third-party API responses without validation, injection via external data |

Reference: https://owasp.org/API-Security/editions/2023/en/0x11-t10/
