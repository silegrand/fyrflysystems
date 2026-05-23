# SIRO & DPO Governance Checklist — Public Sector Surveillance

**Applicable legislation:** UK GDPR; Data Protection Act 2018; Data (Use and Access) Act 2025; Surveillance Camera Code of Practice (PoFA 2012)
**Source:** Fyrfly Systems Ltd — [www.fyrflysystems.com/connected-council.html](https://www.fyrflysystems.com/connected-council.html)

---

## Legal Basis & DPIA

- [ ] Lawful basis for each surveillance category documented (typically Article 6(1)(e) Public Task; LIA where applicable)
- [ ] DPIA completed before deployment of any new CCTV capability, AI analytics, or ANPR system; reviewed annually
- [ ] DPIA signed off by SIRO and DPO; held on record for ICO inspection
- [ ] Processing activities register updated to reflect all surveillance systems, data types, retention periods, third-party processors
- [ ] Surveillance Camera Code of Practice self-assessment completed and published

## Purpose Limitation & Proportionality

- [ ] Each camera justified against a documented "specified pressing need" (PoFA 2012 requirement)
- [ ] AI analytics limited to functions specified in DPIA; no function creep without new assessment
- [ ] Facial recognition: Enhanced DPIA and Chief Executive sign-off; public consultation documented
- [ ] ANPR: only enforcement-purpose data retained; no speculative vehicle movement records

## Transparency & Public Communication

- [ ] Visible, compliant signage at all camera locations (ICO and Surveillance Camera Commissioner standards)
- [ ] Comprehensive CCTV privacy notice on council website; reviewed annually
- [ ] Annual transparency report published: camera count, access events, SARs, police disclosures
- [ ] CCTV policy approved by Full Council or relevant committee; on publication scheme

## Data Security, Retention & Access Controls

- [ ] Standard retention: 30 days for general footage; documented extension process for evidential material
- [ ] Footage encrypted at rest (AES-256 minimum) and in transit (TLS 1.3)
- [ ] Role-based access controls: named, authorised individuals; all access logged and auditable
- [ ] SAR process documented including automated third-party redaction capability
- [ ] Police disclosure process documented with designated contact and disclosure log
- [ ] Third-party data processor agreements with all system suppliers and monitoring centres
- [ ] Annual penetration test by CREST-accredited provider

## Network Security

- [ ] Security network separated from public-facing connectivity
- [ ] QoS configuration documented: security traffic prioritised during emergencies
- [ ] Device monitoring: proactive alerting on outages
- [ ] Failover mechanism tested and documented

---

**Related documents:**
- [UK GDPR Checklist — Education](../education/04-gdpr-checklist.md)
- [Data Security & UK GDPR Technical Reference](../technical/data-security-gdpr.md)
- [Financial Case for Consolidation](./05-financial-case.md)
