# BlueTech CR: IT Management Audit (Planning Stage)

**Course:** Systems Audit, Universidad Fidélitas (2026) · **Type:** team project (4 auditors)
**Deliverables:** IT risk matrix (22 risks) and audit work program (16 procedures)
**My role:** Mobile & UX Audit Specialist. I wrote **procedures 9–12** of the audit program.

> BlueTech CR is a fictional company created for the course.

## The case

BlueTech CR builds a real-time **water-quality monitoring system** for an *ASADA*, a
community-run rural drinking-water association in Costa Rica (the case is set in La Fila de
Desamparados). ESP32-based IoT sensors measure pH, turbidity and residual chlorine, send
readings to **Google Firebase**, and a mobile app shows the data and alerts users when
water quality goes out of range.

**Audit type:** management audit (efficiency, effectiveness, economy and quality of IT and
operations management).

**Objective:** evaluate the effectiveness, efficiency, economy, security and regulatory
compliance of the planning, software development, deployment and infrastructure processes
of the BlueTech CR system, to confirm that the service the ASADA depends on is reliable.

**Scope:** 5 development sprints, July to December 2026: software development, Firebase
cloud configuration, IoT device assembly and calibration, risk management and community
adoption.

**Specific objectives:**
1. Evaluate calibration, maintenance and validation controls for the IoT sensors.
2. Verify information security controls: user access, permissions, authentication and personal data protection.
3. Analyze cloud infrastructure management: backups, availability and recovery.
4. Check the security of communications between IoT devices, the cloud and the app.
5. Review software development, testing and update processes, including version control and remote deployments.
6. Evaluate how technical incidents are logged, assigned, answered and closed.
7. Determine whether business continuity and disaster recovery measures exist.
8. Analyze staff management, training and supplier dependence.

## Standards applied

| Standard | Abbrev. |
|---|---|
| General Auditing Standards for the Public Sector (R-DC-64-2014) | NGASP |
| General Internal Control Law No. 8292 | LGCI |
| Internal Control Standards for the Public Sector (N-2-2009-CO-DFOE) | NCISP |
| Law No. 8968 on the Protection of Personal Data | LPDP |
| Drinking Water Quality Regulation, Decree No. 38924-S | RCAP |
| ISO 31000:2018 Risk management | ISO 31000 |
| ISO/IEC 27001:2022 Information security | ISO 27001 |
| COBIT 2019 | COBIT |

## Risk assessment

Each risk was rated for **probability** and **impact** on a 1–5 scale (very low to very
high). Score = probability × impact.

| Level | Score | Risks |
|---|---|---|
| Very serious | 15–25 | 4 |
| Significant | 9–14 | 13 |
| Moderate | 5–8 | 5 |
| Low | 1–4 | 0 |

### Risk matrix

| ID | Area | Inherent risk | P | I | Score | Level | Procedure |
|---|---|---|---|---|---|---|---|
| R01 | IoT devices and sensors | Erroneous readings caused by miscalibrated pH, turbidity and residual chlorine sensors. | 3 | 5 | 15 | Very serious | #1 (EGJ) |
| R02 | Information security and personal data | Leak or improper processing of the app users' personal data. | 3 | 5 | 15 | Very serious | #2 (EGJ) |
| R03 | Cloud infrastructure | Loss of the measurement history due to dependence on a single cloud provider. | 2 | 5 | 10 | Significant | #9 (RBB) |
| R04 | Communications and networks | Interception or tampering of the data sent by IoT devices. | 3 | 4 | 12 | Significant | #5 (ARG) |
| R05 | Staff management and training | Operational disruption from dependence on key staff in critical technical areas. | 4 | 4 | 16 | Very serious | #4 (EGJ) |
| R06 | Information security and personal data | Credentials or access keys exposed in code repositories. | 2 | 5 | 10 | Significant | #14 (ERM) |
| R07 | IoT devices and sensors | Damage, theft or loss of connectivity of devices installed in the field. | 3 | 3 | 9 | Significant | Not covered |
| R08 | Technical support and incidents | Customer-reported incidents handled informally. | 3 | 3 | 9 | Significant | #15 (ERM) |
| R09 | Information security and personal data | Unauthorized access to privileged accounts (Firebase, GitHub, Microsoft 365) due to missing MFA and excessive permissions. | 3 | 5 | 15 | Very serious | #3 (EGJ) |
| R10 | Software development and quality | Over-the-air (OTA) firmware updates without digital signatures or prior testing leave installed devices inoperable. | 2 | 4 | 8 | Moderate | #10 (RBB) |
| R11 | Software development and quality | Automatic water-quality alerts fail (false negatives or undelivered notifications). | 2 | 5 | 10 | Significant | #13 (ERM) |
| R12 | Software development and quality | Mobile app vulnerabilities (outdated dependencies, insecure on-device data storage). | 3 | 4 | 12 | Significant | #6 (ARG) |
| R13 | End-user computing | Malware infection or phishing attacks on corporate desktops, laptops and phones. | 3 | 4 | 12 | Significant | #11 (RBB) |
| R14 | Communications and networks | Weak corporate network configuration (permissive firewall rules, no segmentation between the admin network and IoT devices). | 3 | 4 | 12 | Significant | #7 (ARG) |
| R15 | Business continuity | No formal business continuity and disaster recovery plan (BCP/DRP). | 2 | 4 | 8 | Moderate | #12 (RBB) |
| R16 | Business continuity | Power or internet outage at the office halts development, support and monitoring. | 3 | 3 | 9 | Significant | #16 (ERM) |
| R17 | End-user computing | Loss or theft of corporate laptops and phones containing sensitive information. | 2 | 3 | 6 | Moderate | Not covered |
| R18 | Suppliers and procurement | Shortages or delivery delays of ESP32 microcontrollers and sensors from suppliers. | 3 | 2 | 6 | Moderate | Not covered |
| R19 | Cloud infrastructure | Cloud costs (Firebase) exceed the budget as devices and stored readings grow. | 2 | 3 | 6 | Moderate | Not covered |
| R20 | Software development and quality | Undetected firmware and app defects due to insufficient test coverage before production. | 3 | 3 | 9 | Significant | Not covered |
| R21 | Staff management and training | Low adoption and misuse of the app due to insufficient training of ASADA users and administrators. | 4 | 3 | 12 | Significant | #8 (ARG) |
| R22 | IoT devices and sensors | Physical deterioration of sensors from humidity, sediment and environmental conditions, shortening their lifespan. | 4 | 3 | 12 | Significant | Not covered |

The full matrix, a heat map and the audit program are in
[`risk-matrix-and-audit-program.xlsx`](risk-matrix-and-audit-program.xlsx). Scores, levels
and the heat map are formulas, so changing a rating updates everything.

## Audit work program

16 procedures cover 16 of the 22 risks, including all 4 rated very
serious. Not covered in this planning stage: R07, R17, R18, R19, R20, R22.

| # | Procedure | Risk | Owner | Dates (2026) | Workpaper |
|---|---|---|---|---|---|
| 1 | IoT sensor calibration, validation and maintenance testing | R01 (Very serious) | EGJ | Oct 12 – Oct 18 | PT-IOT-01 |
| 2 | Personal data protection and compliance with Law 8968 | R02 (Very serious) | EGJ | Oct 19 – Oct 25 | PT-IOT-02 |
| 3 | Access control, permissions and multi-factor authentication | R09 (Very serious) | EGJ | Oct 26 – Nov 1 | PT-IOT-03 |
| 4 | Key technical staff and knowledge transfer | R05 (Very serious) | EGJ | Nov 2 – Nov 8 | PT-IOT-04 |
| 5 | Security of IoT data transmission | R04 (Significant) | ARG | Nov 9 – Nov 15 | PT-IOT-05 |
| 6 | Mobile app vulnerability review | R12 (Significant) | ARG | Nov 16 – Nov 22 | PT-IOT-06 |
| 7 | Corporate network configuration and segmentation | R14 (Significant) | ARG | Nov 23 – Nov 29 | PT-IOT-07 |
| 8 | Training of ASADA users and administrators | R21 (Significant) | ARG | Nov 30 – Dec 6 | PT-IOT-08 |
| 9 | **Cloud data backups** | R03 (Significant) | RBB | Dec 7 – Dec 13 | PT-IOT-09 |
| 10 | **Over-the-air (OTA) firmware updates** | R10 (Moderate) | RBB | Dec 7 – Dec 13 | PT-IOT-10 |
| 11 | **Malware and phishing protection on corporate devices** | R13 (Significant) | RBB | Dec 14 – Dec 20 | PT-IOT-11 |
| 12 | **Business continuity and disaster recovery plan** | R15 (Moderate) | RBB | Dec 14 – Dec 20 | PT-IOT-12 |
| 13 | Automatic water-quality alert flow | R11 (Significant) | ERM | Oct 26 – Nov 1 | PT-IOT-13 |
| 14 | Secrets and access keys in code repositories | R06 (Significant) | ERM | Nov 2 – Nov 8 | PT-IOT-14 |
| 15 | Technical incident management | R08 (Significant) | ERM | Nov 9 – Nov 15 | PT-IOT-15 |
| 16 | Power and connectivity continuity at the office | R16 (Significant) | ERM | Nov 16 – Nov 22 | PT-IOT-16 |

### My procedures (9–12)

**9. Cloud data backups** (PT-IOT-09, Dec 7 – Dec 13 2026)
- Risk: **R03**, loss of the measurement history due to dependence on a single cloud provider (P2 × I5 = 10, Significant)
- Procedure: Request the Firebase backup configuration and restore-test records from the Infrastructure & Support Specialist, to verify that the measurement history can be recovered after a failure.

**10. Over-the-air (OTA) firmware updates** (PT-IOT-10, Dec 7 – Dec 13 2026)
- Risk: **R10**, over-the-air (OTA) firmware updates without digital signatures or prior testing leave installed devices inoperable (P2 × I4 = 8, Moderate)
- Procedure: Request the deployment procedure, version records and pre-release test reports from the IoT Software Engineer, to verify that updates are validated, digitally signed and can be rolled back before they reach devices.

**11. Malware and phishing protection on corporate devices** (PT-IOT-11, Dec 14 – Dec 20 2026)
- Risk: **R13**, malware infection or phishing attacks on corporate desktops, laptops and phones (P3 × I4 = 12, Significant)
- Procedure: Request the antivirus/EDR configuration, web and email filtering policies and cybersecurity training records from the Infrastructure & Support Specialist, to verify that corporate computers and phones are protected.

**12. Business continuity and disaster recovery plan** (PT-IOT-12, Dec 14 – Dec 20 2026)
- Risk: **R15**, no formal business continuity and disaster recovery plan (BCP/DRP) (P2 × I4 = 8, Moderate)
- Procedure: Request the BCP/DRP, defined recovery times and test records from the General & Financial Administrator, to verify that service can be restored after power, internet or cloud outages.

Together, these four test whether BlueTech CR could **keep the service running and recover
it**: restoring the measurement history, rolling back a bad firmware update, keeping
endpoints free of malware and phishing, and having a tested continuity plan.

## Team

| Initials | Auditor | Role |
|---|---|---|
| EGJ | Esteban Guzmán Jiménez | IoT & Hardware Audit Specialist |
| ARG | Alvaro Rivas Galagarza | Process Auditor / Scrum Master |
| RBB | Rafael Eduardo Brenes Brenes | Mobile & UX Audit Specialist |
| ERM | Esteban Ruiz Matamoros | Cloud & Security Audit Specialist |

## What changed from the submitted version

This is an English portfolio version of the team's deliverables. The content is the same;
I only translated it and fixed small inconsistencies: procedure 8 was missing its risk
rating, workpaper references 10–16 used three digits (`PT-IOT-010`) while 1–9 used two,
and each procedure now names the risk it tests (R01–R22).
