# Data Security & UK GDPR — Technical Specification

**Source:** Fyrfly Systems Ltd — [www.fyrflysystems.com](https://www.fyrflysystems.com)

---

## Encryption

| Layer | Standard |
|---|---|
| At rest (camera SD, NVR, NAS) | AES-256-GCM |
| In transit | TLS 1.3 |
| Key management | Per-site HSM or cloud KMS (AWS KMS / Azure Key Vault); customer-managed keys available |
| Footage integrity | SHA-256 hash on write; verified on read (tamper-evident chain of custody) |
| Secure deletion | DoD 5220.22-M 3-pass overwrite on retention expiry |
| Hardware disposal | NIST 800-88 compliant media sanitisation |

## Role-Based Access Control

| Role | Permissions |
|---|---|
| FYRFLY_ADMIN | Full system; user management; audit log export |
| FYRFLY_SITE_MANAGER | Site configuration; lockdown authority; viewer access |
| FYRFLY_OPERATOR | Live view; playback within permitted zones; alert management |
| FYRFLY_VIEWER | Live view only; no playback; no export |
| FYRFLY_AUDIT_ONLY | Audit log and compliance reports; no footage access |
| FYRFLY_TEMP_ACCESS | Time-limited credential; no VMS access |

All access events logged: user, action, resource, timestamp, source IP.
MFA enforced for FYRFLY_ADMIN and FYRFLY_SITE_MANAGER roles.
Inactivity timeout: configurable per role (default 15 minutes).

## Data Retention

| Data Type | Default Retention | Extension Trigger | Deletion |
|---|---|---|---|
| CCTV footage (general) | 31 days | Incident flag | AES-256 secure overwrite |
| CCTV footage (evidential) | Indefinite (flagged) | Manual flag | Manual deletion with audit log entry |
| Access control logs | 12 months | Legal hold | Secure deletion |
| Visitor records | 12 months | SAR / legal hold | Right-to-erasure workflow |
| ANPR data | 30 days standard | Enforcement action | Secure deletion |
| Audit logs | 7 years | Regulatory requirement | Immutable; dual ADMIN auth required |

## Subject Access Request (SAR) Workflow

1. Operator searches VMS by date range, camera, or access credential
2. Relevant footage identified and clipped
3. Automated or semi-automated third-party face-blurring applied
4. Clip exported to encrypted ZIP with SHA-256 manifest
5. Export action logged in audit trail
6. Delivered via expiring secure download link (7-day default)

## DPIA Support

Fyrfly provides a completed DPIA template for each deployment type:
- School CCTV estate
- Town centre and public space surveillance
- Access control with biometric credentials
- Temporary event surveillance (solar tower)

Templates are maintained against current ICO guidance and are available to Data Protection Officers on request.

## Applicable Legislation

- UK GDPR (retained EU law as amended by the Data Protection, Privacy and Electronic Communications Regulations 2019)
- Data Protection Act 2018
- Data (Use and Access) Act 2025
- Surveillance Camera Code of Practice (Protection of Freedoms Act 2012)
- ICO guidance on CCTV in schools and public spaces

---

**Related documents:**
- [UK GDPR Checklist — Education](../education/04-gdpr-checklist.md)
- [SIRO & DPO Checklist — Public Sector](../public-sector/04-siro-dpo-checklist.md)
- [Dynamic Lockdown System](./dynamic-lockdown.md)
