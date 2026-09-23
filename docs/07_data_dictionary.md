# NARTS — Data Dictionary & Schema Reference

> **Non-Communicable Disease Appointment & Retention Tracking System**
> *Kidus Petros Hospital · Version 1.1 · March 2026*

---

> [!NOTE] 
> **Who is this for?** This reference is for technical staff, clinical informaticists, and senior clinicians who need precise definitions of every field, code, and status used in NARTS.

---

## 1. Diagnosis / Condition Codes

| Code | Full Name | ICD-11 Reference | Default SMS Arrival Time |
|------|-----------|-----------------|-------------------------|
| `DM` | Diabetes Mellitus | 5A10 | ጠዋት — 12:30 EC ≈ 06:30 EAT |
| `HTN` | Hypertension (Essential) | BA00 | ከሰዓት — 6:30 EC ≈ 12:30 EAT |
| `DM and HTN` | Diabetes Mellitus with Hypertension | 5A10 + BA00 | ጠዋት — 12:30 EC ≈ 06:30 EAT |
| `Other` | Other NCD conditions | — | ከሰዓት — 6:30 EC ≈ 12:30 EAT |

> **Note:** Current codes are plain-text labels. The Strategic Roadmap targets a transition to **ICD-11 / ESV-ICD11** standardised codes in Phase 2, in alignment with the Ethiopia Digital Health Blueprint 2021–2030.

---

## 2. Patient Status & Data Constraints

### `patient_name` Strict Validation Binding

> [!CAUTION]
> To explicitly preserve the integrity of Amharic downstream SMS processing and UI rendering, `patient_name` fields are heavily sanitized against standard Unicode.

| Field | Regex Constraint | Effect |
|-------|------------------|--------|
| `patient_name` | `/^[\u1200-\u137F\s]+$/` | English, Symbols, or Numbers are entirely eradicated from input blocks at runtime. Any bypassing attempt yields an API Validation failure. |

### `consent_status` — Patients Sheet, Column H

| Value | Meaning | Effect on SMS |
|-------|---------|--------------|
| *(empty)* | No consent SMS has been sent | SMS allowed (except for `Disagreed` guard) |
| `Pending` | Consent SMS sent — awaiting patient reply | SMS still allowed |
| `Agreed` | Patient replied `A` — explicit opt-in | All SMS enabled |
| `Disagreed` | Patient replied `B` — explicit opt-out | All non-consent SMS **blocked permanently** |

> **Immutability rule:** Once a patient's status is `Agreed` or `Disagreed`, subsequent replies are silently ignored. The status cannot change without direct Admin intervention.

---

### Appointment Status — Calculated, Not Stored

Appointment status is derived at query time from `today - recent_appointment_date` (Appointments sheet, Col D).

| Status | Condition | Days Overdue | Display Colour |
|--------|-----------|-------------|---------------|
| Future / On-Time | `recent_appointment_date` ≥ today | — | — |
| **Missed Appointment** | 1–14 days past due | 1–14 | 🟡 Yellow |
| **Defaulter** | 15–89 days past due | 15–89 | 🔴 Red |
| **Lost to Follow-Up (LTFU)** | 90+ days past due | ≥90 | ⛔ Dark Red |

---

## 3. User Roles & Permissions

| Role | Internal Code | Description |
|------|:------------:|-------------|
| `Admin` | ROLE_ADMIN | Full system access: user management, all feedback, audit logs, admin functions |
| `Physician` | ROLE_PHYSICIAN | Full patient care: registration, appointments, SMS, tracing |
| `Nurse` | ROLE_NURSE | Full patient care: registration, appointments, SMS, tracing |
| `Health Extension Worker` | ROLE_HEW | Read access to patients and missed appointments; no add/edit |

### Account Status Values

| Field | Possible Values |
|-------|----------------|
| `status` | `Active` · `Inactive` · `Disabled` |
| `approval` | `Pending` · `Approved` · `Rejected` |

---

## 4. SMS Types Reference

| SMS Code | Sheet Column | Trigger Function | When Sent |
|---------|:------------:|-----------------|---------|
| `consent_sms` | SMS Col C | `sendConsentSMS()` | On patient registration |
| `reminder_sms` | SMS Col D | `resendSmsForTomorrow()` | Day before appointment, 9 AM EAT |
| `education_sms` | SMS Col E | Manual or scheduled | Periodic health education campaigns |
| `appointment_miss_sms` | SMS Col F | `autoSendMissedApptSms()` | 1–6 days after a no-show |
| `remind_returnVisit_sms` | SMS Col G | `autoSendAgreedReturnSms()` | Day before agreed return date |
| `condolence_sms` | SMS Col H | `sendReminderSms()` — `condolence` | On tracing outcome = `Deceased` |

---

## 5. Tracing Outcomes

| Outcome | Clinical Meaning |
|---------|----------------|
| `Returned` | Patient voluntarily attended the clinic |
| `Transfer` | Patient transferred to another healthcare facility |
| `Self-transfer` | Patient independently moved their care elsewhere |
| `Deceased` | Patient has died — triggers condolence SMS to next of kin if applicable |
| `Refused` | Patient was contacted but declined to return |
| `Not found` | Patient could not be located through all available channels |

---

## 6. Drug Adherence Values

| Value | Clinical Definition |
|-------|-------------------|
| `Good` | Patient takes medication consistently as prescribed |
| `Fair` | Patient occasionally misses doses |
| `Poor` | Patient frequently misses doses — clinical intervention warranted |

---

## 7. Follow-Up Appointment Adherence Values

| Value | Clinical Definition |
|-------|-------------------|
| `Good` | Patient attends appointments consistently |
| `Fair` | Patient has missed some appointments |
| `Poor` | Patient frequently fails to attend — active tracing recommended |

---

## 8. Ethiopian Calendar Time Periods

All appointment reminders and SMS references use Ethiopian time system periods:

| Period (Amharic) | Ethiopian Clock | Approximate EAT | Used for |
|-----------------|----------------|----------------|---------|
| ጠዋት (Morning) | 12:00–6:00 EC | 06:00–12:00 EAT | DM / DM+HTN default slot |
| ረፋድ (Late Morning) | 6:00–7:00 EC | 12:00–13:00 EAT | Mid-morning appointments |
| ከሰዓት (Afternoon) | 7:00–12:00 EC | 13:00–18:00 EAT | HTN / Other default slot |

> [!TIP]
> **30-Minute Early Arrival:** All reminder times are calculated 30 minutes *earlier* than the actual appointment time to account for clinic queues and registration.

---

## 9. Phone Number Format

All phone numbers are stored in **normalised international format** by `normalizeEthiopianPhone()`:

```
+2519XXXXXXXX   (most Ethiopian mobile numbers)
+2517XXXXXXXX   (alternative prefix mobile numbers)
```

**Accepted input formats:**

| Input Format | Example | Result |
|-------------|---------|--------|
| `09XXXXXXXX` | `0912345678` | `+251912345678` |
| `9XXXXXXXX` | `912345678` | `+251912345678` |
| `+2519XXXXXXXX` | `+251912345678` | `+251912345678` |
| `2519XXXXXXXX` | `251912345678` | `+251912345678` |

---

## 10. Audit Log Event Types

Every significant action in NARTS is logged to the AuditLog sheet. Key event types:

| Event Type | Triggered By |
|-----------|-------------|
| `LOGIN_SUCCESS` | Successful user authentication |
| `LOGIN_FAILED` | Failed login attempt |
| `LOGOUT` | User logout |
| `USER_REGISTERED` | New user self-registration submitted |
| `PATIENT_ADDED` | New patient record created |
| `APPOINTMENT_UPDATED` | Appointment date changed |
| `TRACING_ADDED` | Patient tracing record created |
| `SMS_CONSENT_REPLY` | Patient's consent reply processed via webhook |
| `SMS_CONSENT_DUPLICATE` | Duplicate consent reply received and ignored |
| `SMS_SENT` | SMS dispatched to patient |
| `REGISTRATION_ERROR` | Error encountered during user registration |

---

*© 2026 Kidus Petros Hospital · NCD Department — Internal Technical Reference*
