# Corporación Umbrella: IT Risk and Control Assessment for a Clinical Laboratory

**Course:** Systems Audit (SC-704), Universidad Fidélitas (2026) · **Type:** individual case study
**Author:** Rafael Brenes Brenes
**Frameworks:** ISO 15189:2022, CIA asset valuation, preventive / detective / corrective controls

> Corporación Umbrella S.A. is a fictional company created for the course.

## 1. Understanding the business

### Context

Corporación Umbrella S.A. is a mid-sized clinical laboratory in Los Angeles, United States,
that runs specialized blood tests for private clinics, insurers and hospitals. It has a
sample collection area, a central laboratory (hematology, clinical chemistry and
immunology), a web platform where doctors and patients check results, and a database that
stores historical results and test orders. Its digital infrastructure is basic but growing,
so the company started a digital transformation and hired external auditors to review its
IT governance, risk management and controls, as preparation for accreditation under
quality standards such as **ISO 15189**.

### Current situation

Umbrella is in a transition. A growing mid-sized lab usually buys equipment and tools as
needs come up, without an IT plan tying them together, so there is probably no complete
inventory and no clear maintenance or replacement policy. The web platform was likely
launched to serve clients better, with security added afterwards instead of designed in.

The lab depends more on technology every year, but its controls haven't kept pace. Three
things are pushing it toward an audit:

- **Clients:** hospitals and insurers increasingly ask for guarantees on quality and data
  protection, and accreditation gives them that confidence.
- **The data:** it handles health information, protected in the US by laws such as HIPAA
  and a frequent target of attacks like ransomware.
- **Growth:** with more patients, platform users and staff, what used to be handled
  informally no longer works.

### Working assumptions

The analysis starts from assumptions the audit would need to confirm: database backups are
not tested regularly, IT training for staff is informal, and nobody tracks equipment
warranties and support centrally. There's no direct evidence for these, so the
probabilities in the matrix are estimates.

### Assets evaluated

I chose the three assets that matter most for delivering results. Each is rated 1–5 for
confidentiality (C), integrity (I) and availability (A). The overall value is the highest
of the three.

| Asset | Description | C | I | A | Value |
|---|---|---|---|---|---|
| **A1. Laboratory equipment** | Computers, microscopes and medical equipment used to collect samples and run tests. Their condition, warranty or support, and the training of the people using them determine whether results are reliable. | 3 | 5 | 4 | 5 (critical) |
| **A2. Confidential user information** | Data of each user registered on the web platform: identification, insurance details and medical records. Personal health information that must be protected. | 5 | 4 | 4 | 5 (critical) |
| **A3. Database** | Stores historical results and test orders, and feeds the web platform. If it fails or is lost, the service stops. | 5 | 5 | 5 | 5 (critical) |

### ISO 15189

ISO 15189 is the international standard for medical laboratories. It specifies
requirements for quality and competence, and accreditation bodies use it to decide whether
to grant accreditation. The current version is from 2022 and replaced the 2012 edition and
ISO 22870 (ISO, 2022).

The risks below relate to things the standard requires a lab to control: equipment, staff
competence, and the protection and retention of patient information. Treating them with
controls helps the lab show it meets those requirements and produces the records an
assessor would ask for (inventories, training records, backup tests). That doesn't
guarantee accreditation on its own, but it's an important part of preparing for it.

## 2. Risk analysis

### Scales

| Value | Impact | Description | Probability | Description |
|---|---|---|---|---|
| 1 | Insignificant | No effect on results or operations. | Rare | Only in exceptional circumstances. |
| 2 | Minor | Slight effect, easy to correct. | Unlikely | Could happen, but not expected this year. |
| 3 | Moderate | Delayed results or rework. | Possible | May happen during the year. |
| 4 | Major | Unreliable results or service stopped; possible loss of accreditation. | Likely | Very likely to happen during the year. |
| 5 | Critical | Patient harm, legal penalties, data loss or operations halted. | Almost certain | Expected, or already happening in the sector. |

Risk level = impact × probability: **Low** 1–4, **Medium** 5–9, **High** 10–16,
**Critical** 20–25. Probabilities are my estimates from the case context (basic but
growing infrastructure, in a sector that receives many cyberattacks) and would need to be
confirmed during the audit.

### Risk matrix

| Risk event | Asset | Threat | Vulnerability | Impact | Probability |
|---|---|---|---|---|---|
| **R01.** Equipment failure or downtime from obsolescence, lapsed warranty or support, or missing resources. | A1. Laboratory equipment | Technical failures and end of life with no manufacturer support or spare parts. | No inventory tracking warranties, support contracts and life cycle; basic infrastructure that is growing. | 4: delays or unreliable results; non-compliance with the standard's equipment requirements. | 3: warranties and support commonly lapse without life-cycle control. |
| **R02.** Misuse of IT resources by staff who haven't been properly trained. | A1. Laboratory equipment and the systems that run it | Human error, misuse and susceptibility to scams such as phishing. | No formal training plan, competence assessment or authorization to use equipment and systems. | 3: operational errors, rework or improper access. | 4: human error is common, and staff and systems are growing with the digital transformation. |
| **R03.** Leak of confidential patient information (IDs, insurance and medical records) through a cyberattack. | A2. Confidential user information on the web platform | External attackers: credential theft, exploitation of web app flaws, phishing. | Weak security: no second authentication factor, unencrypted data, missing patches and no penetration testing. | 5: harm to patients, legal penalties and loss of trust. | 4: the health sector is a frequent target and the platform is exposed to the internet. |
| **R04.** Loss of historical results and orders due to poor backup management. | A3. Results and orders database | Hardware failure, accidental deletion, human error or a disaster on site. | Backups not automated, no off-site copy, no restore tests; no defined limits for data loss or downtime. | 5: irreversible loss of results and non-compliance with record-keeping controls. | 3: without restore tests, a failure can leave useless copies. |
| **R05.** Database and backups encrypted or held hostage by ransomware. | A3. Results and orders database (and its backups) | Ransomware delivered through phishing or exposed services. | Backups reachable from the same network, not isolated or immutable; no network segmentation or endpoint protection. | 5: total service outage and loss of access to results. | 4: ransomware frequently hits laboratories and hospitals. |

R04 and R05 are related, because ransomware can also encrypt the backups. They're kept as
separate risks (one from failure or error, the other from an attack) but share key
controls such as isolated, immutable backups.

### Resulting risk level

| ID | Risk | Impact | Probability | Score | Level |
|---|---|---|---|---|---|
| R01 | Equipment without active warranty or support, or obsolete | 4 | 3 | 12 | High |
| R02 | Staff not trained in IT resources | 3 | 4 | 12 | High |
| R03 | Leak of confidential patient information | 5 | 4 | 20 | **Critical** |
| R04 | Data loss from poor backup management | 5 | 3 | 15 | High |
| R05 | Ransomware on the database and its backups | 5 | 4 | 20 | **Critical** |

## 3. Proposed controls

| Risk | Preventive | Detective | Corrective |
|---|---|---|---|
| **R01.** Equipment without support, or obsolete | **C01. Asset inventory with warranty and life cycle:** record each computer, microscope and medical device with purchase date, expected life, warranty expiry and support contract; quarterly review and a budgeted annual replacement plan.<br>**C02. Maintenance, support and calibration contracts:** keep manufacturer support active, schedule preventive maintenance and calibration, and evaluate replacing equipment that goes out of support. | **C03. Expiry alerts and failure log:** alerts 90 days before warranties or support expire, and a failure log reviewed regularly. | **C04. Equipment contingency plan:** backup equipment or an agreement with an external lab to keep testing; a repair or replacement procedure, with verification before equipment goes back into use. |
| **R02.** Staff not trained in IT | **C05. Annual training and awareness plan:** mandatory onboarding and regular training on safe use of equipment and systems, passwords, phishing and handling patient data.<br>**C06. Competence matrix and authorization:** only assessed, authorized staff operate critical equipment and systems; up-to-date, accessible manuals and procedures. | **C07. Competence assessments and simulations:** regular assessments, phishing simulations and review of human-error incidents to find knowledge gaps. | **C08. Retraining and corrective action:** immediate retraining after an incident or a failed assessment, with the corrective action recorded and followed up. |
| **R03.** Leak of patient information | **C09. Two-step verification and role-based access:** two-step verification for doctors and staff, strong passwords for patients, and permissions limited to what each role needs (least privilege).<br>**C10. Encryption in transit and at rest:** HTTPS on the platform and encryption of sensitive fields (ID, insurance, medical records) in the database.<br>**C11. Vulnerability management and penetration testing:** regular patching, a web application firewall, secure development and annual penetration tests of the platform. | **C12. Log monitoring and alerts:** log access to and queries on patient data, with alerts for anomalous behavior or bulk data extraction. | **C13. Incident response and notification plan:** procedure to contain the incident, revoke credentials, investigate the cause and notify those affected and the authorities as the law requires (for example, HIPAA). |
| **R04.** Data loss from poor backups | **C14. Backup policy and automation:** automatic backups following the 3-2-1 rule (three copies, two media, one off-site), with defined limits for acceptable data loss (RPO) and downtime (RTO). | **C15. Regular restore tests:** a documented test restore every quarter to confirm backups are complete and usable.<br>**C16. Backup job monitoring:** alerts for failed or incomplete backups and a daily review of the backup report. | **C17. Disaster recovery plan:** documented restore procedures, roles and responsibilities, and an alternate site to recover the database within the defined maximum downtime. |
| **R05.** Ransomware on the database and backups | **C18. Isolated, immutable backups:** immutable or offline copies, separate from the production network and with their own credentials, so ransomware can't encrypt them. This control links R04 and R05.<br>**C19. Endpoint protection, email filtering and segmentation:** EDR, email filtering, segmentation between the lab network, the platform and the database, and closing unnecessary exposed services. | **C20. Early detection of encryption activity:** alerts for mass file encryption, unusual database access and unauthorized changes to backups. | **C21. Ransomware response plan:** isolate affected systems, restore from a clean, verified backup, analyze the root cause and coordinate with the authorities; any decision about a ransom belongs to management with legal advice. |

## 4. Conclusions

All three assets are essential to the lab, because complete, correct and timely results
depend on them. Of the five risks, two are **critical** (patient data leak and ransomware)
and three are **high** (equipment without support, lack of training and poorly managed
backups).

The risks are connected. An untrained employee can open a phishing email that leads to a
data leak or ransomware, and if backups are poorly managed, that attack can mean losing the
data for good. That's why they're better treated as a set than one at a time.

**Recommendation:** start with the critical risks: turn on two-step verification, encrypt
sensitive data and keep isolated backups that can't be modified from the normal network.
Then build the equipment inventory with warranties, create a training plan and regularly
test that backups can be restored. This should bring the critical risks down to at least
medium, though they would need to be reassessed to confirm it.

This analysis is based on the case information, so a significant part of it rests on
assumptions and estimates. To make it more accurate, they should be confirmed through
interviews, site visits and a review of how the systems are configured. Management should
also assign an owner to each control and review the matrix at least once a year.

## Reference

International Organization for Standardization. (2022). *Medical laboratories:
Requirements for quality and competence* (ISO Standard No. 15189:2022).
https://www.iso.org/standard/76677.html

---

*English portfolio version of the case study I submitted in Spanish. The analysis,
ratings and controls are unchanged. I added the RPO/RTO abbreviations to C14 and pointed
the reference to the standard's page on iso.org.*
