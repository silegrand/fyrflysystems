# Three Pillars of Integrated School Security

**Source:** Fyrfly Systems Ltd — [www.fyrflysystems.com/education.html](https://www.fyrflysystems.com/education.html)
**Full guide:** [The Invisible Shield](https://www.fyrflysystems.com/invisible-shield.html)

---

## Pillar 1 — AI-Driven CCTV (The Eyes)

AI analytics running at the camera edge detect specific behavioural patterns and alert staff before incidents escalate. Processing occurs on the camera or a local node — not via external cloud — keeping footage within the school's data boundary.

### Capabilities Relevant to KCSiE

- **Loitering detection:** Unidentified adults in out-of-bounds areas trigger immediate DSL device alerts
- **Blind spot coverage:** Stairwells, external areas, and corridors monitored without additional staff. Supports KCSiE requirement to consider where child-on-child abuse might occur
- **Visitor tracking:** Camera confirms visitor's physical location matches declared destination; alert if visitor appears in unauthorised zone
- **Perimeter breach:** Person vs object classification suppresses false positives; external gate lockdown available on breach detection

### Technical Specifications

| Parameter | Value |
|---|---|
| Resolution | Up to 4K / 30fps (PTZ, bullet); 8MP (360° panoramic) |
| Encoding | H.265+ / H.264; ONVIF Profile S/G/T |
| Streaming | RTSP; WebRTC |
| Edge alert latency | Under 500ms |
| Retention | 31 days standard; AES-256 at rest |
| Minimum illumination | 0.001 lux (optical with IR); N/A (thermal) |

---

## Pillar 2 — Intelligent Access Control (The Gates)

A well-designed access control system resolves the tension between a welcoming school environment and an impenetrable safeguarding perimeter.

### Staff Access
Frictionless. Smart credentials (card, fob, or mobile) allow staff movement without bottlenecks. Multi-factor authentication available for sensitive zones.

### Visitor Management
Digital visitor registration at reception: photo capture, ID scan, optional barred-list check, time-stamped digital badge, audit trail satisfying KCSiE and UK GDPR simultaneously. Paper visitor books are not a compliant safeguarding tool.

### Dynamic Lockdown
Single authenticated action from headteacher's device, reception console, or designated trigger point:
- Every controlled access door across the site locks immediately
- ARC (Alarm Receiving Centre) notified with live camera feed
- Staff devices receive push notification
- Full audit trail written to tamper-evident log

For technical detail: [Dynamic Lockdown System](../technical/dynamic-lockdown.md)

---

## Pillar 3 — Secure Wireless Networks (The Nervous System)

Security systems must not share bandwidth with classroom traffic.

### Why Separation Matters

A 30-camera 4K CCTV estate requires approximately 200 Mbps of dedicated bandwidth. During Period 4 with 600 students on devices, a shared network cannot reliably carry both. Security system outages during business hours are the direct result of this contention.

### Requirements

- **Dedicated VLAN:** logically separated from student/staff Wi-Fi; no broadcast domain overlap
- **QoS enforcement:** DSCP EF marking on all security traffic; lockdown commands prioritised above all other traffic
- **Failover:** automatic 4G/5G secondary link; activates within 30 seconds of primary failure
- **Device monitoring:** SNMP/ICMP polling at 60-second intervals; alert within 2 minutes of device loss

---

**Related documents:**
- [Safeguarding Overview](./01-safeguarding-overview.md)
- [Martyn's Law — Schools](./03-martyns-law-schools.md)
- [Data Security & UK GDPR](../technical/data-security-gdpr.md)
