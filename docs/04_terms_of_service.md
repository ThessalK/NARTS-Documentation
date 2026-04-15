# NARTS — Terms of Service

> **Non-Communicable Disease Appointment & Retention Tracking System**
> *St. Peter's Specialized Hospital · Addis Ababa, Ethiopia*
> *Effective Date: March 2026 · Version: 1.1*

---

## 1. Acceptance of Terms

By accessing and using the NARTS system ("the System"), you ("User") agree to be bound by these Terms of Service. If you do not agree to these terms, you must not use the System.

These Terms apply to all users across all clinical and administrative roles, including Physicians, Nurses, Health Extension Workers (HEWs), and System Administrators.

---

## 2. System Purpose and Scope

NARTS is a **secure, internal clinical workflow tool** provided exclusively to St. Peter's Specialized Hospital staff for the purpose of:
- Tracking and managing NCD patient appointments and retention
- Sending automated, consent-based SMS communications to patients
- Monitoring clinical adherence indicators (medication and follow-up)
- Generating aggregated insights for clinical quality improvement

### 🚫 Strict Prohibitions
> [!CAUTION]
> The System **must not** be used for:
> - Accessing patient records without a direct, justifiable clinical need
> - Personal, commercial, or non-clinical purposes
> - Sharing or pooling login credentials with other individuals
> - Processing or transferring patient data outside of Ethiopia without explicit, documented authorisation
> - Attempting to circumvent the system's role-based access controls or security mechanisms

---

## 3. User Accounts and Responsibilities

### 3.1 Account Registration & Access
- All accounts require **Administrator approval** before access is granted.
- You must provide accurate, current information during registration.
- Your registered Ethiopian phone number serves as your unique login identifier.

### 3.2 Password Security
- You are strictly responsible for maintaining the confidentiality of your password.
- Passwords must be a minimum of **6 characters**.
- If you suspect your account has been compromised, you must report it to a System Administrator immediately.
- To protect patient data, the system strictly enforces session isolation and timeouts.

### 3.3 Clinical Conduct
All users agree to:
- Access only those patient records necessary for the execution of their clinical duties.
- Log all patient data changes, appointments, and tracing outcomes accurately.
- Never falsify, alter, or delete clinical records without documented clinical or administrative justification.
- Report any system errors, data discrepancies, or suspected breaches immediately.

---

## 4. Patient Data Handling Obligations

In strict accordance with the **Ethiopian Personal Data Protection Proclamation No. 1321/2024**:

**4.1 Highly Sensitive Data:** Patient health data is classified as *Sensitive Personal Data* (Art. 2(5)) and must be handled with the utmost care, dignity, and confidentiality.

**4.2 Limited Use:** Clinical data accessed through NARTS must only be used for the direct care of the relevant patient unless explicitly authorised by hospital leadership for anonymised research or quality improvement.

**4.3 Mandatory Consent:** Patient consent is a legal prerequisite for sending any non-vital SMS. The System enforces an automated consent gate (`Agreed` vs `Disagreed`). Users must never attempt to bypass this verification mechanism via manual SMS-Gate API calls.

**4.4 Right to Rectification:** Users must respect patients' rights (Art. 27) by correcting inaccurate or incomplete records promptly when notified.

---

## 5. Data Integrity and the Audit Trail

**5.1 Immutable Tracking:** Every action performed in NARTS that modifies patient or system data is **permanently logged** in the system's AuditLog, recording:
- The exact timestamp of the action
- The User ID and Role of the person performing the action
- The precise nature of the change

**5.2 Log Integrity:** Audit logs cannot be deleted, altered, or obfuscated by any user, including Administrators.

**5.3 Hospital Oversight:** St. Peter's Specialized Hospital reserves the right to review audit logs at any time in the event of a suspected policy violation, clinical error, or data breach.

---

## 6. Confidentiality Obligations

All users acknowledge and agree that:

> [!IMPORTANT]
> **Strict Confidentiality:** All information accessed through the NARTS dashboard is strictly confidential and carries the same legal weight and protective requirements as paper-based medical records in Ethiopia.

**6.1 Enduring Obligation:** Confidentiality obligations survive indefinitely following the termination of employment or the revocation of system access.

**6.2 Consequences of Violation:** Unauthorised disclosure of patient data or violation of confidentiality may result in immediate disciplinary action, termination of employment, and referral to the relevant professional regulatory body and civil authorities under Ethiopian law.

---

## 7. SMS Communication Terms

**7.1** Clinical SMS reminders are sent only to patients who have provided **explicit consent** (status: `Agreed`).

**7.2** The system automatically schedules and dispatches SMS messages daily at **09:00 EAT**.

**7.3** Users must **never** use the NARTS SMS backend to send unsolicited, non-clinical, promotional, or personal messages to patients.

**7.4** Any patient complaints regarding SMS communications must be recorded and escalated to the System Administrator immediately.

---

## 8. Acceptable Use Policy

| ✅ Permitted Actions | ❌ Strictly Prohibited Actions |
|---------------------|-------------------------------|
| Searching for patients currently in your care | Bulk downloading or exporting of patient lists |
| Sending clinical SMS to consenting patients | Taking photos or screenshots of patient data |
| Generating aggregated clinic reports | Accessing the system from an unapproved or public device |
| Updating appointment and adherence records | Attempting to modify audit log entries |
| Approving staff accounts (Admin only) | Granting unauthorised persons physical or digital access |

---

## 9. Availability and Service Levels

**9.1** NARTS is hosted on Google Workspace infrastructure and targets **99%+ uptime** during core clinic hours (Monday–Saturday, 7:00–18:00 EAT).

**9.2** Planned maintenance requiring system downtime will be communicated to staff at least **24 hours** in advance.

**9.3** The hospital and system administrators bear no liability for service interruptions caused by third-party platform outages (Google, SMS-Gate.app), local internet connectivity failures, or force majeure events.

---

## 10. Limitation of Liability

> [!WARNING]
> **10.1** The hospital provides the system "as is" to facilitate clinical workflows. **Clinical decisions remain the sole professional responsibility of the attending clinician.**
> 
> **10.2** NARTS is **a decision-support tool only** — it does not replace, supersede, or diminish professional clinical judgment. Appointment data shown in the system must always be verified against the master medical record if a discrepancy is suspected.

**10.3** St. Peter's Specialized Hospital is not liable for adverse outcomes arising from clinical decisions based on data that has been incorrectly entered, omitted, or misinterpreted by staff.

---

## 11. Termination of Access

**11.1** System access is terminated automatically upon the conclusion of your employment or clinical placement.

**11.2** Administrators reserve the right to suspend or revoke access immediately and without notice for any suspected violation of these Terms.

**11.3** Upon termination of access, you must not attempt to log into the System or retrieve any stored data.

---

## 12. Governing Law and Dispute Resolution

These Terms are governed by and construed in accordance with the laws of the **Federal Democratic Republic of Ethiopia**, including but not limited to:
- **Ethiopian Personal Data Protection Proclamation No. 1321/2024**
- **Ethiopian Health Law and Regulatory Standards**

Any disputes arising from the use of NARTS shall be resolved exclusively through the competent courts of Ethiopia.

---

## 13. Amendments

St. Peter's Specialized Hospital reserves the right to amend these Terms at any time to reflect changes in law, clinical policy, or system functionality. Users will be notified of material changes, and continued use of the System constitutes formal acceptance of the updated Terms.

---

*By logging into NARTS via your phone number and password, you formally confirm that you have read, understood, and accept these Terms of Service.*

*© 2026 St. Peter's Specialized Hospital — NCD Department.*
