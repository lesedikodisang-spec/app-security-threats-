# app-security-threats-
STRIDE-based risk assessment for a mobile banking app
# Threat Modeling: "MyBank" Mobile App

**Scope**: Android/iOS mobile application for balance inquiries, fund transfers, and transaction history.

**Objective**: Identify, prioritize, and mitigate security risks using the STRIDE methodology.

---

## 📚 Table of Contents
1. [Assets to Protect](#-assets-to-protect)
2. [Threats (STRIDE)](#-threats-stride)
3. [Risk Matrix](#-risk-matrix)
4. [Mitigation Roadmap](#-mitigation-roadmap)
5. [References](#-references)
6. [Contributing](#-contributing)

---

## 🎯 Assets to Protect
| Asset | Description | Confidentiality | Integrity | Availability |
| :--- | :--- | :--- | :--- | :--- |
| User PII | Names, email addresses, SSNs | High | High | Medium |
| Transaction History | Incoming/outgoing transfers | High | High | Low |
| Session Tokens | Authentication tokens after login | High | High | High |
| API Keys | Backend service authentication | High | High | Medium |

---

## 🚨 Threats (STRIDE)

### 1. Spoofing
- **Threat**: Fake login pages (phishing) tricking users into entering credentials.
- **Mitigation**: Implement Certificate Pinning and educate users on verifying the app's authenticity.

### 2. Tampering
- **Threat**: Intercepting API calls to modify transfer amounts or recipient details.
- **Mitigation**: Enforce HTTPS with request signing (HMAC). Validate all inputs server-side.

### 3. Repudiation
- **Threat**: Users deny initiating a transfer.
- **Mitigation**: Implement audit logs with timestamps and IP addresses. Require OTP for transactions.

### 4. Information Disclosure
- **Threat**: Sensitive data (e.g., account numbers) exposed in device logs or error messages.
- **Mitigation**: Use ProGuard for Android, scrubbing logs in production, and encrypt stored data.

### 5. Denial of Service
- **Threat**: Attackers flood the API with requests, causing downtime.
- **Mitigation**: Rate limiting, Web Application Firewall (WAF), and auto-scaling infrastructure.

### 6. Elevation of Privilege
- **Threat**: A standard user escalates to admin privileges via parameter manipulation.
- **Mitigation**: Implement role-based access control (RBAC) and validate all authorization tokens.

---

## 📊 Risk Matrix

| Threat | Likelihood | Impact | Priority | Status |
| :--- | :--- | :--- | :--- | :--- |
| API Interception (Tampering) | High | Critical | **P0** | In Progress |
| Data Leakage (Info Disclosure) | Medium | High | **P1** | Planned |
| Phishing (Spoofing) | High | High | **P1** | Mitigated |
| DoS Attacks | Medium | Medium | **P2** | Not Started |
| Audit Gaps (Repudiation) | Low | Medium | **P3** | Mitigated |

---

## 🛠️ Mitigation Roadmap

| Priority | Action Item | Owner | Due Date |
| :--- | :--- | :--- | :--- |
| P0 | Implement request signing for all API calls | Backend Team | Q3 2026 |
| P1 | Add certificate pinning in mobile app | Mobile Team | Q4 2026 |
| P1 | Deploy WAF and rate limiting | DevOps | Q4 2026 |
| P2 | Conduct penetration testing | External Vendor | Q1 2027 |

---

## 🔗 References
- [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/)
- [NIST SP 800-30 Risk Assessment Guide](https://csrc.nist.gov/publications/detail/sp/800-30/rev-1/final)
- [Microsoft STRIDE Methodology](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats)

---

## 🤝 Contributing
Found a missing threat or a better mitigation? Open an Issue or submit a Pull Request!

---

## ⚠️ Disclaimer
This is a fictional case study for educational purposes only. Any resemblance to real apps is coincidental.
