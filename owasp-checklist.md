# OWASP Checklists

## OWASP Top 10 — Web Application

Reference: https://owasp.org/Top10/

---

### A01 — Broken Access Control
Users can act outside their intended permissions. This includes accessing other users' data, performing admin actions, or bypassing access restrictions simply by modifying URLs, parameters, or tokens.

**What to test:** IDOR (changing IDs in requests), accessing admin endpoints without privilege, missing authorization checks on functions.

---

### A02 — Cryptographic Failures
Sensitive data is exposed due to weak or missing encryption. This covers passwords stored in plaintext, data sent over HTTP, use of outdated algorithms like MD5 or SHA1, and hard-coded secrets in code.

**What to test:** Check if sensitive data (passwords, tokens, PII) is encrypted in transit and at rest, look for weak cipher suites, inspect source code/configs for hard-coded keys.

---

### A03 — Injection
Untrusted input is sent to an interpreter (database, OS, LDAP, etc.) and executed as a command. SQL injection is the most common but this also covers NoSQL, OS command, LDAP, and template injection.

**What to test:** Insert special characters (`'`, `;`, `--`, `{{`) into input fields, headers, and URL parameters to observe unexpected behaviour or errors.

---

### A04 — Insecure Design
Security flaws baked into the design of an application before a single line of code is written. No amount of patching fixes a fundamentally insecure design — it requires a redesign.

**What to test:** Lack of rate limiting on sensitive flows (e.g., OTP brute force), absence of business logic controls, no threat modelling evidence, missing security requirements.

---

### A05 — Security Misconfiguration
The application or its infrastructure is configured insecurely. This is the most common vulnerability and includes default credentials, open cloud storage, verbose error messages, and unnecessary services running.

**What to test:** Default admin credentials, directory listing enabled, detailed stack traces in error pages, unnecessary HTTP methods (PUT, DELETE), missing security headers.

---

### A06 — Vulnerable & Outdated Components
Using libraries, frameworks, or other components with known vulnerabilities. Attackers can look up public CVEs and exploit unpatched dependencies.

**What to test:** Check package versions against CVE databases (e.g., via `npm audit`, `pip audit`, Snyk), look for end-of-life software in use.

---

### A07 — Identification & Authentication Failures
Weaknesses in how users are identified and authenticated. This includes weak passwords, missing account lockout, broken session tokens, and lack of multi-factor authentication.

**What to test:** Brute force login with no lockout, session tokens that don't expire, token reuse after logout, predictable token values, missing MFA on sensitive accounts.

---

### A08 — Software & Data Integrity Failures
Code and data pipelines that don't verify integrity. An attacker could tamper with software updates, serialized objects, or CI/CD pipelines if there are no integrity checks.

**What to test:** Insecure deserialization (tamper with serialized objects), unsigned software updates, CI/CD pipelines pulling from untrusted sources without verification.

---

### A09 — Security Logging & Monitoring Failures
The application fails to log security events or those logs are not monitored. Without visibility, attacks go undetected and incident response is severely limited.

**What to test:** Attempt failed logins, privilege escalation, and injection — check if any alerts or logs are generated. Verify sensitive actions (password change, fund transfer) are audited.

---

### A10 — Server-Side Request Forgery (SSRF)
The server is tricked into making HTTP requests to an unintended destination — typically internal services or cloud metadata endpoints — by supplying a malicious URL in user input.

**What to test:** Submit internal addresses (`http://127.0.0.1`, `http://169.254.169.254`) into any URL input field. Look for features that fetch URLs (webhooks, file imports, PDF generators).

---

## OWASP API Security Top 10

Reference: https://owasp.org/API-Security/editions/2023/en/0x11-t10/

---

### API1 — Broken Object Level Authorization (BOLA / IDOR)
APIs expose endpoints that handle object identifiers. If authorization isn't enforced per object, an attacker can simply change an ID in the request to access another user's data.

**What to test:** Change resource IDs (user IDs, order IDs, account numbers) in API requests and observe if data belonging to other users is returned.

---

### API2 — Broken Authentication
Authentication mechanisms are implemented incorrectly, allowing attackers to compromise tokens, passwords, or sessions and assume other users' identities.

**What to test:** Test for weak or predictable tokens, missing token expiry, tokens that remain valid after logout, lack of brute-force protection on login endpoints.

---

### API3 — Broken Object Property Level Authorization
The API exposes more object properties than needed, or allows users to modify properties they shouldn't (mass assignment). An attacker can update privileged fields like `role` or `balance`.

**What to test:** Send extra fields in request bodies (e.g., `"role": "admin"`) and check if they are accepted. Review API responses for sensitive fields that shouldn't be returned.

---

### API4 — Unrestricted Resource Consumption
The API does not limit how many resources a client can consume — no rate limiting, no payload size limits, no request throttling. This can lead to DoS or financial abuse.

**What to test:** Send a high volume of requests in a short time, send very large payloads, trigger resource-heavy operations repeatedly and observe if any limits are enforced.

---

### API5 — Broken Function Level Authorization
The API fails to restrict access to sensitive functions (e.g., admin endpoints) based on user roles. Regular users can call privileged actions by simply knowing the endpoint.

**What to test:** As a regular user, call admin-level API endpoints (e.g., `DELETE /api/users/{id}`, `GET /api/admin/stats`) and check if access is granted.

---

### API6 — Unrestricted Access to Sensitive Business Flows
The API exposes a business flow (e.g., purchase, referral, OTP) without safeguards, allowing attackers to abuse it at scale — bulk buying, account enumeration, or reward farming.

**What to test:** Automate legitimate workflows to identify missing rate limits or business logic controls (e.g., apply a discount code 1000 times, enumerate usernames via forgot-password).

---

### API7 — Server-Side Request Forgery (SSRF)
The API fetches a remote resource based on user-supplied input without validating the URL. An attacker can point it to internal services or cloud metadata endpoints.

**What to test:** Supply internal URLs (`http://127.0.0.1`, `http://169.254.169.254/latest/meta-data/`) in any parameter that triggers a server-side fetch.

---

### API8 — Security Misconfiguration
The API or its supporting infrastructure is misconfigured — CORS set to `*`, default credentials in place, unnecessary HTTP methods allowed, missing TLS, verbose error messages leaking stack traces.

**What to test:** Check CORS headers, try OPTIONS requests to list allowed methods, look for detailed error messages, test with expired/no TLS certificates.

---

### API9 — Improper Inventory Management
Organizations run multiple API versions or environments (dev, staging, old versions) without proper tracking. Forgotten or undocumented APIs often lack the same security controls as the current version.

**What to test:** Look for older API versions (`/v1/`, `/v2/`), test deprecated endpoints that may still be live, check if dev/staging environments are exposed publicly.

---

### API10 — Unsafe Consumption of APIs
The application blindly trusts data from third-party APIs without validation. An attacker who compromises or manipulates that third-party data can then exploit the consuming application.

**What to test:** Identify third-party API integrations and check if their responses are validated and sanitized before use. Look for injection points via third-party data (e.g., webhooks, OAuth responses).
