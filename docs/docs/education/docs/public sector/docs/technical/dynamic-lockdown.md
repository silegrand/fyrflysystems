# Dynamic Lockdown System — Technical Reference

**Source:** Fyrfly Systems Ltd — [www.fyrflysystems.com](https://www.fyrflysystems.com)
**API documentation:** [github.com/fyrflysystems](https://github.com/fyrflysystems)

---

## Definition

A software-orchestrated emergency security response triggered from a single authenticated source, executing access control, CCTV, and communications actions across a site in under 2 seconds.

## Trigger Methods

| Method | Authentication | Typical User |
|---|---|---|
| VMS dashboard (web/desktop) | RBAC role + MFA | Control room operator |
| Mobile app (iOS/Android) | Biometric + PIN | Headteacher, DSL, SLT |
| Physical panic button | Hardware tamper-evident | Reception, key staff points |
| REST API call | Bearer token + IP allowlist | Third-party emergency system integration |
| Automated AI trigger | Configurable threshold + human confirm | Out-of-hours unattended mode |

## Execution Sequence

```
T+0.0s  Trigger authenticated
T+0.1s  Lockdown command broadcast (security VLAN, DSCP EF priority)
T+0.3s  All OSDP-controlled access doors receive lock command
T+0.5s  Fail-secure doors confirm locked state via OSDP status response
T+0.6s  All cameras: maximum resolution continuous recording
T+0.7s  AI analytics: maximum sensitivity profile activated
T+0.8s  ARC notification dispatched (encrypted TCP; live camera feed included)
T+1.0s  Staff push notification (iOS APNs / Android FCM)
T+1.2s  Tamper-evident audit log entry written (NTP-synchronised timestamp)
T+1.5s  VMS dashboard: all door states, camera feeds, active alerts updated
T+2.0s  Optional: automated 999 alert (configured per site policy)
```

## Lockdown States

| State | Description |
|---|---|
| NORMAL | Standard access rules; all systems nominal |
| SOFT_LOCKDOWN | Unknown credentials rejected; credentialled staff unaffected |
| FULL_LOCKDOWN | All controlled doors locked; no credential overrides active |
| EMERGENCY | Full lockdown + ARC + optional 999 alert; dual auth required for release |
| DRILL | Identical to FULL_LOCKDOWN; no ARC or 999 notification sent |

## Lockdown API

```bash
POST https://api.fyrflysystems.com/v1/sites/{site_id}/lockdown

Authorization: Bearer {token}
Content-Type: application/json

{
  "lockdown_type": "FULL_LOCKDOWN",
  "initiated_by": "operator@school.ac.uk",
  "reason": "Unconfirmed threat at main entrance",
  "notify_arc": true,
  "notify_staff": true,
  "drill_mode": false
}
```

**Response:**
```json
{
  "status": "LOCKDOWN_INITIATED",
  "lockdown_id": "LKD-20260415-142307-001",
  "doors_locked": 24,
  "cameras_escalated": 40,
  "arc_notified": true,
  "staff_alerts_sent": 87,
  "audit_id": "AUD-20260415-142307"
}
```

## Release

Lockdown release in EMERGENCY state requires dual authorisation from two FYRFLY_SITE_MANAGER or FYRFLY_ADMIN accounts.

## Audit Trail

Every action during a lockdown is written to a tamper-evident, NTP-synchronised log:
- Door lock/unlock events with OSDP confirmation status
- Camera state changes
- ARC notification timestamp and acknowledgement
- Staff alert dispatch and delivery status
- User actions: who initiated, who released, timestamps

Audit log is retained for 7 years; immutable; deletion requires dual ADMIN authorisation.

## Martyn's Law Relevance

A documented Fyrfly Dynamic Lockdown procedure satisfies the communication and lockdown requirements for:
- [Standard Tier schools](../education/03-martyns-law-schools.md) (100–799 capacity)
- [Enhanced Tier schools](../education/03-martyns-law-schools.md) (800+ capacity)
- [Standard Tier local authority venues](../public-sector/03-martyns-law-councils.md)
- [Enhanced Tier civic events and venues](../public-sector/03-martyns-law-councils.md)

---

**Related documents:**
- [Data Security & UK GDPR](./data-security-gdpr.md)
- [Solar CCTV Tower Specifications](./solar-tower-specs.md)
- [Martyn's Law — Schools](../education/03-martyns-law-schools.md)
- [Martyn's Law — Local Authorities](../public-sector/03-martyns-law-councils.md)
