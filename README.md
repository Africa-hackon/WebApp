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

See [owasp-checklist.md](owasp-checklist.md) for the OWASP Top 10 Web and API Security checklists.
