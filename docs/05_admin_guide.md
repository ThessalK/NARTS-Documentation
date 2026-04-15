# NARTS — Administrator Guide

> **Non-Communicable Disease Appointment & Retention Tracking System**
> *St. Peter's Specialized Hospital*
> *Version 1.1 · March 2026*

---

> [!CAUTION]
> **Who is this for?** This guide is written exclusively for the **System Administrator** (Role: Admin). It covers initial system setup, user management, security responsibilities, and routine maintenance. Clinical staff do not require this guide.

> [!NOTE]
> **Your role in the Digital Health Mission:** As a System Administrator at St. Peter's, you are a primary steward of the hospital's *Information Revolution*. Your governance of NARTS directly supports the **Ethiopia Digital Health Blueprint 2021–2030** — ensuring that patient data is managed with the highest standards of integrity, security, and accountability.

---

## 1. Initial System Setup

Perform each of the following steps **once only**, in the order listed, immediately after first deployment.

### Step 1 — Initialize Admin Credentials

Open the Apps Script editor and run `initializeAdminInSettings()`:

```javascript
// Apps Script Editor → Run → initializeAdminInSettings()
function initializeAdminInSettings() { /* ... */ }
```

> [!IMPORTANT]
> Edit the admin phone number and password **inside the function** before running it. Store the credentials in a secure, access-controlled location.

---

### Step 2 — Migrate SMS Credentials to Script Properties

Run `setupSmsCredentials_()` to move the SMS gateway credentials from source code into Google's encrypted ScriptProperties vault:

```javascript
setupSmsCredentials_()
```

After confirming the SMS gateway connects successfully, you may optionally remove the hardcoded fallback values from the source code.

---

### Step 3 — Register the SMS Webhook

Deploy the web app first, then run `setupSMSWebhook()` to register the incoming SMS reply endpoint. The webhook URL is your deployed web app URL. 

> [!WARNING]
> If the URL changes (due to a new deployment ID), you **must** run `setupSMSWebhook()` again to restore Amharic SMS tracking capabilities.

---

### Step 4 — Verify the Database Schema

Run the schema validation suite to confirm all sheets have the correct structure:

```javascript
runAllVerificationTests()
```

---

## 2. User Management

### Approving a New Account

1. Log in as Admin → **Settings → User Management**
2. In the **Pending Users** table, locate the new registration
3. Select the appropriate **Role** (Physician / Nurse / HEW)
4. Click **Approve**

> [!SUCCESS]
> The user can log in immediately after approval.

### Disabling a User Account

1. In All Users, change the user's **Status** to `Disabled`
2. Click **Save Changes**

The user cannot log in until their status is restored to `Active`. Use this for staff who are temporarily away or under review.

---

## 3. Time-Based Trigger Setup

NARTS sends automated daily Amharic SMS reminders via time-based triggers. Set these up **once** in the Apps Script editor:

1. Open **Apps Script Editor** → click the **⏰ Triggers** icon
2. Click **+ Add Trigger**
3. Configure the first trigger (`resendSmsForTomorrow`):
   - Event source: **Time-driven**
   - Type: **Day timer**
   - Time: **9 AM – 10 AM (EAT)**

4. Repeat the above steps for `autoSendAgreedReturnSms`

> [!TIP]
> Both triggers should be set to the same 9 AM – 10 AM time window to ensure reminders are dispatched before clinic hours begin.

---

## 4. Security Responsibilities

As Admin, you bear ongoing responsibility for the security of patient data and system integrity:

| Responsibility | Recommended Action | Frequency |
|---------------|-------------------|----------|
| Audit log review | Open the `AuditLog` sheet and scan for anomalies, failed logins, or unexpected actions | Monthly |
| Webhook token rotation | Update `SMS_WEBHOOK_TOKEN` in ScriptProperties, then re-run `setupSMSWebhook()` | Annually |
| Data breach response | Notify ECA within 72 hours — see Privacy Policy | As needed |
| Backup verification | Confirm Google Sheets version history is intact and accessible | Monthly |

---

## 5. Mobile Companion App & Sync Connectivity

The N-ARTS architecture is bridging toward a **Progressive Web App (PWA)** to allow syncing for offline operations inside clinical wards.
If your users report 500 Server Errors on the Mobile App regarding missing Patient Data:

1. Validate the UTF-8 Encoding for the Amharic strings. Ensure mobile payload headers explicitly request `charset=utf-8`.
2. Confirm the `patient_name` column enforces the strict regex validation constraints (`\u1200-\u137F`). Mobile devices may fail sync if non-Amharic metadata pollutes the JSON blob.
3. Check `Google Apps Script Executions` tab for runtime timeout failures (usually when patients exceed 5000 rows). 

---

## 6. Feedback Management

The public patient feedback form is accessible externally via the `?page=feedback` query parameter on your main URL.

To manage incoming feedback:
1. Log in as Admin → **Settings → Feedbacks**
2. **Pending** entries are visible natively within the beautifully blurred Glassmorphism container.
3. Click **"Evaluate"** to review, respond, and log the feedback as resolved.

---

## 7. Escalation Contacts

| Issue | Contact |
|-------|---------|
| System unavailable | Hospital IT Department |
| Data breach suspected | IT Department + Data Protection Officer + ECA (within 72 hours) |
| SMS not being sent or received | SMS-Gate.app support |
| Mobile App Sync Failure | Network Engineer & Frontend PWA Team |

---

*© 2026 St. Peter's Specialized Hospital — Administrator Reference v1.1*  
*⚠️ RESTRICTED — For System Administrator Use Only*
