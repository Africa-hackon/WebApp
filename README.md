# Web Application Security

Training resources, tools, and checklists for web application and API security testing.

## Labs

See [WebApps-Labs.md](WebApps-Labs.md) for the full list of practice labs.

---

## Tools

### Burp Suite
The primary tool for web application security testing.

- **Community Edition** — Free; manual proxy, repeater, intruder (throttled), decoder, comparer.
- **Professional Edition** — Paid; full intruder, active scanner, Burp Collaborator, extensions.

**Key Modules:**

| Module | Purpose |
|--------|---------|
| Proxy | Intercept and modify HTTP/S traffic between browser and server |
| Repeater | Manually craft and replay individual requests |
| Intruder | Automate fuzzing and payload injection |
| Scanner (Pro) | Automated vulnerability scanning |
| Decoder | Encode/decode data (Base64, URL, HTML, hex, etc.) |
| Comparer | Diff two requests or responses |
| Sequencer | Analyse randomness/entropy of tokens |
| Extender | Install BApp extensions from the BApp Store |

**Setup:**
1. Download from https://portswigger.net/burp
2. Install the PortSwigger CA certificate in your browser
3. Configure your browser proxy to `127.0.0.1:8080`

---

## OWASP Checklists

### OWASP Top 10 — Web Application

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

### OWASP API Security Top 10

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
