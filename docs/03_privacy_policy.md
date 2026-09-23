# NARTS — Privacy Policy

> **Non-Communicable Disease Appointment & Retention Tracking System**
> *Kidus Petros Hospital · Addis Ababa, Ethiopia*
> *Effective Date: March 2026 · Version: 1.1*

---

> [!IMPORTANT]
> **Compliance Notice:** This Privacy Policy is strictly drafted in full compliance with the **Ethiopian Personal Data Protection Proclamation No. 1321/2024** and aligns intrinsically with the standards established by the **Ethiopia Digital Health Blueprint 2021–2030**.

---

## 1. Data Controller Information

Kidus Petros Hospital is the legal **Data Controller** under Article 2(10) of the Proclamation for all patient data processed through the NARTS ecosystem.

| Entity | Details |
|--------|---------|
| **Organisation** | Kidus Petros Hospital |
| **Department** | Non-Communicable Diseases (NCD) Care Department |
| **Location** | Addis Ababa, Federal Democratic Republic of Ethiopia |
| **Data Protection Officer** | *[Hospital DPO Name / Contact]* |

---

## 2. Personal Data We Collect

In strict accordance with Articles 2(1) and 2(24) of the Proclamation, NARTS explicitly limits data collection specifically to what is clinically and operationally necessary.

### 2.1 Patient Health Data (Sensitive Personal Data — Art. 2(5))
> [!CAUTION]
> Health data is afforded the highest tier of legal and technical protection. It is heavily encrypted and protected by strict role-based access grids.

| Data Field | Clinical Purpose |
|------------|----------------|
| **Full Name** | Accurate patient identification (Amharic encoding exclusively) |
| **MRN** | Cross-referencing with the central hospital medical record |
| **Phone Number** | Delivery of appointment reminders and outreach SMS |
| **Diagnosis** | Clinical care classification (e.g. DM, HTN) and automated SMS scheduling |
| **Appointments** | Care continuation and retention tracking |
| **Adherence** | Monitoring clinical outcomes (medication and follow-up) |
| **Consent Log** | Timestamped legal basis for SMS communications |
| **Tracing Records**| Documenting clinical outreach efforts for overdue patients |

### 2.2 System User Data (Staff)
| Data Field | Operational Purpose |
|------------|----------------|
| **Full Name** | Staff identification and system auditing |
| **Phone Number** | Secure login credential |
| **Job Role / Unit** | Cryptographic role-based access control (RBAC) permissions |
| **Audit Logs** | Tamper-evident record of all system modifications |

---

## 3. Lawful Basis for Processing

We process patient health data under the following legal grounds specified in **Articles 7, 8, and 9** of the Proclamation:

| Processing Activity | Legal Basis under Proclamation No. 1321/2024 |
|--------------------|----------------------------------------------|
| Appointment tracking | **Art. 9(b)** — Necessary for medical treatment by a medical institution |
| SMS communications | **Art. 8** — Explicit, informed patient consent (A/B reply mechanism) |
| Patient tracing / outreach | **Art. 7(e)** — Public interest in public health |
| Immutable audit logging | **Art. 7(c)** — Legal obligation for institutional record-keeping (Art. 46) |
| Staff authentication | **Art. 7(b)** — Performance of employment contract |

### 3.1 How We Obtain Patient Consent

Consistent with **Article 8**, NARTS automates the consent process immutably:

1. **Clear Information:** Upon registration, an Amharic SMS is sent to the patient explaining who is collecting the data, why, that it will not be shared, and how to opt out.
2. **Explicit Choice:** The patient is asked to reply **"A"** (Agreed) or **"B"** (Disagreed).
3. **Immutable Record:** The system timestamps and permanently protects the reply via structural locks.
4. **Strict Enforcement:** If a patient replies "B" (or does not reply), the system **automatically blocks** all further clinical or marketing SMS, except where necessary to protect vital interests (Art. 9(c)).

---

## 4. How We Protect and Use Your Data

Patient data is used **exclusively** for direct clinical care and operational tracking:

### ✅ Approved Uses:
- Scheduling and managing NCD clinic appointments.
- Sending timely reminders and health education (with consent).
- Tracking clinic-wide retention and medication adherence trends.
- Generating anonymised statistical reports for clinical improvement.

### ❌ Strictly Prohibited Uses:
- We **never** sell, rent, or trade patient data to any third party.
- We **never** share data with commercial or marketing entities.
- We **never** transfer identifying data outside of Ethiopia without explicit federal consent.

---

## 5. Your Rights as a Data Subject

Under **Articles 24–32** of the Proclamation, patients possess the following rights regarding their data:

### 5.1 Right to be Informed (Art. 24)
You have the right to transparent information about how your data is used. This is fulfilled during the initial consent SMS process.

### 5.2 Right of Access & Rectification (Art. 25 & 27)
You may request confirmation of your data in NARTS and ask for corrections to inaccurate information by contacting your care provider.

### 5.3 Right to Erasure (Art. 28)
You may request the deletion of your data when it is no longer necessary, subject to mandatory federal medical record retention requirements.

### 5.4 Right to Withdraw Consent (Art. 8)
You may withdraw your consent for SMS tracking **instantly and at any time** by replying **"B"** to any NARTS SMS, or by informing the NCD department directly.

---

## 6. Technical Security Measures

As required by **Article 17**, NARTS implements rigorous technical and organisational safeguards:

- **Role-Based Access (RBAC):** Clinical staff can only access data required for their specific role function.
- **Cryptographic Hashing:** Staff passwords are computationally protected with salted SHA-256 encryption.
- **Session Isolation:** Token-keyed sessions aggressively prevent cross-user data leakage.
- **Immutable Audit Trail:** Every addition, edit, or deletion is permanently logged with the user's ID and a timestamp.
- **Automated Consent Gate:** The software hard-blocks SMS delivery to patients without a valid `Agreed` structural flag.
- **XSS Prevention:** All patient data is sanitized before display to prevent malicious code execution vectors.

---

## 7. Data Retention & Third-Party Processors

### Retention Periods
- **Clinical Records:** Minimum 10 years (Ethiopian health records law)
- **Audit Logs:** Minimum 3 years (Art. 46)
- **User Accounts:** Duration of employment + 1 year

### Authorised Data Processors (Art. 2(11))
Patient data is transmitted securely to the following processors purely for system operation:
1. **Google LLC** — Secure cloud hosting infrastructure (Google Apps Script & Sheets).
2. **SMS-Gate.app** — Routing and delivery of Amharic SMS payload messages.

> [!NOTE]
> All data transmissions are strictly limited to the minimum necessary and governed by rigorous data protection agreements.

---

## 8. Data Breach Notification

In accordance with **Articles 43 and 44**:
- If a catastrophic data breach occurs that risks patients' rights or freedoms, the **Ethiopian Communications Authority (ECA)** will be formally notified **within 72 hours**.
- Affected patients will be notified without undue delay.
- All technical incidents are comprehensively recorded in the hospital's internal secure breach register.

---

## 9. Contact & Complaints

To exercise your data rights, or if you firmly believe your privacy has been violated, please contact:

1. **Kidus Petros NCD Department / Data Protection Officer**
2. **Ethiopian Communications Authority (ECA)** — Data Protection & Privacy Unit ([eca.gov.et](https://www.eca.gov.et))

---

*© 2026 Kidus Petros Hospital. All rights reserved.*
