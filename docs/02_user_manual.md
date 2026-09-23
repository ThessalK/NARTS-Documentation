# NARTS — User Manual

> **Non-Communicable Disease Appointment & Retention Tracking System**
> *Kidus Petros Hospital — NCD Care Department*
> *Version 2.2 · May 2026*

---

> [!TIP]
> **Who is this for?** This manual is written for all clinical and administrative staff who use NARTS — Physicians, Nurses, Health Extension Workers (HEW), and Data Clerks. No technical background is required.

---

## Table of Contents

1. [Platform Overview](#1-platform-overview)
2. [NARTS Mobile App (Flutter) — Getting Started](#2-narts-mobile-app-flutter--getting-started)
3. [Mobile App — Navigation & Features](#3-mobile-app--navigation--features)
4. [Mobile App — Patients Tab](#4-mobile-app--patients-tab)
5. [Mobile App — Tracing Catalog (Tiered Overdue)](#5-mobile-app--tracing-catalog-tiered-overdue)
6. [Mobile App — Tracing Overdue Dashboard](#6-mobile-app--tracing-overdue-dashboard)
7. [The Tracing Dialog — Full Reference](#7-the-tracing-dialog--full-reference)
8. [Tracing Protocol — Prioritization & Workflow](#8-tracing-protocol--prioritization--workflow)
9. [Return Visit Quota Management](#9-return-visit-quota-management)
10. [Web App (Desktop) — Quick Reference](#10-web-app-desktop--quick-reference)
    - [Appointments Tab — Diurnal Calendar View](#appointments-tab--diurnal-calendar-view)
11. [SMS Features](#11-sms-features)
12. [Dark Mode & Theme](#12-dark-mode--theme)
13. [Frequently Asked Questions](#13-frequently-asked-questions)
14. [Support](#14-support)

---

## 1. Platform Overview

NARTS operates on **two platforms** that share the same backend database:

| Platform | Primary Use | Device |
|----------|-------------|--------|
| **NARTS Mobile App** (Flutter) | Field tracing, patient search, overdue management, phone outreach | Smartphone |
| **NARTS Web App** (GAS Desktop) | Dashboard analytics, SMS campaigns, appointment scheduling, admin management | Desktop / Tablet |

Both platforms connect to the same secure backend and reflect data changes in real time.

---

## 2. NARTS Mobile App (Flutter) — Getting Started

### 2.1 Installation

The N-ARTS Mobile App is distributed as an installable APK for Android devices. Contact your hospital IT department or System Administrator to obtain the latest version.

### 2.2 Logging In

1. Open the N-ARTS Mobile App
2. Enter your **registered phone number** (e.g. `0912345678` or `+251912345678`)
3. Enter your **password**
4. Tap **"Login"**

> [!NOTE]
> **First time using the mobile app?** Tap **"Register here"** on the login screen to submit an account request. Your account will be reviewed and approved by an Administrator before you can log in.

### 2.3 The Navigation Drawer

Tap the **menu icon (☰)** in the top-left corner to open the navigation drawer, which provides:

| Item | Description |
|------|-------------|
| **User Info Header** | Your name, role, unit, and profession |
| **System Router** | Opens the NARTS Web App in your device browser |
| **User Manual** | Opens this protocol guide within the app |
| **Theme Toggle** | Switch between Dim Mode and Light Mode |
| **Logout** | Sign out of your account |

### 2.4 Main Tabs

The main interface uses a **bottom navigation bar** with three tabs:

| # | Tab | Icon | Purpose |
|--:|-----|------|---------|
| 1 | **Patients** | 👥 | Search, register, and manage patient records |
| 2 | **Tracing Catalog** | 📋 | Tiered list of overdue patients by days missed |
| 3 | **Tracing Overdue** | ⏰ | Outcome dashboard for all traced patients |

---

## 3. Mobile App — Navigation & Features

### Theme Toggle

Use the drawer's theme toggle to switch between **Dim Mode** (dark futuristic with neon cyan accents) and **Light Mode** (medical blue). Your preference is applied immediately.

### Offline & Local Caching

All patient, tracing catalog, and overdue data is **cached locally** on your device. This enables:

- **Instant loading** — Data displays immediately from local cache
- **Offline access** — Search, view, and filter data without an internet connection
- **Background sync** — Fresh data is fetched from the server when connection is available
- **Connectivity check** — Saving tracing records or patient changes requires an internet connection

Pull down on any list to trigger a manual refresh.

### Phone Integration

The app supports click-to-call functionality. When you tap a phone number, the device dialer opens automatically. The app tracks which patients you have already called during your session.

### User Manual Navigation

The User Manual features a **clickable Table of Contents**:

1. Tap the **list icon** in the app bar to open the Table of Contents panel
2. Tap any section title to jump directly to that section
3. Section headings within the manual also respond to taps on anchor links
4. The panel slides down from the top and can be dismissed by tapping any entry

---

## 4. Mobile App — Patients Tab

### Searching for a Patient

1. Tap the **Patients** tab
2. Type any part of the patient's **name**, **MRN**, or **phone number** in the search field
3. Results appear instantly as you type (500ms debounce)

### Filtering Patients

Use the filter controls at the top of the tab:

| Filter | Options |
|--------|---------|
| **Disease / Condition** | All, DM, HTN, DM & HTN, Others |
| **Drug Adherence** | All, Good, Poor, Unknown |
| **Appointment Date Range** | Start and End dates using the Ethiopian calendar picker |

### Registering a New Patient

1. Tap the **+** button in the app bar
2. Fill in the required fields:
   - **Full Name** — Patient's legal name (Amharic text only)
   - **MRN** — Medical Record Number (unique identifier)
   - **Phone Number** — Ethiopian format (e.g. `0912345678`)
   - **Diagnosis** — Select from: `DM`, `HTN`, `DM & HTN`, or `Others`
3. Tap **Save**

> [!IMPORTANT]
> **Name must be in Amharic.** The name field accepts only Ethiopic characters (Amharic). Latin/English characters are blocked at the keyboard level. This ensures consistency with clinical records and SMS communications.

> The system automatically sends an Amharic SMS consent request upon successful registration.

### Editing a Patient

Tap the **edit (✏️) icon** on any patient card to modify their details. The same form is pre-populated with the existing data. Names must also be in Amharic when editing.

### The Patient Card

Each patient is displayed as a clinical card:

```
┌──────────────────────────────────────────────┐
│  👤 አበበ ከበደ አለሙ                           │
│  MRN: 10245     Dx: DM and HTN               │
│  📞 +251912345678                              │
│  ──────────────────────────────────────────── │
│  Last Appointment:    15/01/2026              │
│  Drug Adherence:      Good                    │
│  ──────────────────────────────────────────── │
│   [📞 Call]    [✏️ Edit]                      │
└──────────────────────────────────────────────┘
```

### Call Action

Tap the **📞 Call** button to dial the patient directly. After the first call, the button changes to **Redial**.

### Adding Appointment Sessions

The **Add Appt** button opens a dialog to schedule a new appointment and update the patient's drug adherence:

| Section | Description |
|---------|-------------|
| **Appointment Date (Ethiopian)** | Tap the date field to open the Ethiopian calendar picker. Only future weekdays (non-holiday) are allowed. |
| **Drug Adherence Level** | Dropdown with options: `Good`, `Poor`, `Unknown`. This updates the DrugAdherence sheet. |
| **SMS Notifications** | Two checkboxes: **Feedback Request** (sends a thank-you SMS) and **Health Education Link** (sends an educational SMS). |
| **Time Slot** | A 20-minute slot is automatically allocated based on the patient's diagnosis and daily clinic capacity. |

After saving, a confirmation dialog shows the patient name, Ethiopian date, allocated time slot, adherence level, and SMS options selected. Tap **Done** to close.

> Note: The appointment system prevents scheduling on weekends, Ethiopian holidays, and dates in the past. Duplicate detection blocks a patient from being double-booked on the same day.

### Transferring Out a Patient

Use the **Transfer Out / Referral** button (icon: 🔄) to transfer a patient to another health facility:

1. Tap the 🔄 **Transfer Out** icon on the patient card
2. Select the **Institution Type**: `Health Center`, `Hospital`, or `Other`
3. Enter the **Institution Name** (required)
4. Tap **Transfer** to confirm

After transferring:
- The patient's card shows a greyed-out transfer icon
- The **Edit** and **Add Appt** buttons are disabled
- The patient remains visible in the patient list but is flagged as transferred out
- A record is written to the **TransferOuts** sheet with the patient ID, institution details, and timestamp
- The patient is excluded from active tracing lists

### Restoring a Transferred Patient to Care

If a transferred-out patient returns to your facility, they can be restored to active care:

1. Locate the patient in the **Patients** tab — their card displays a green **Restore** icon (↩️)
2. Tap the **Restore** icon
3. A confirmation dialog appears explaining the patient will return to active care
4. Tap **Restore** to confirm, or **Cancel** to keep the transfer status

After restoring:
- The patient's records are removed from the **TransferOuts** sheet
- The patient reappears in tracing lists and becomes eligible for appointments
- The card returns to its normal active state with all actions enabled
- An audit log entry is recorded

> **Note:** Restoring is a permanent action. Use it only when the patient has physically returned to your facility.

---

## 5. Mobile App — Tracing Catalog (Tiered Overdue)

This tab organizes all overdue patients into **three clinical tiers** based on how many days they have missed their appointment:

| Tier | Days Overdue | Color | Priority | Clinical Action |
|------|-------------|-------|----------|-----------------|
| **Missed Appointments** | 1–14 days | 🟦 Blue | Standard | Phone tracing, reschedule |
| **Defaulters** | 15–89 days | 🟧 Orange | High | Escalated tracing, alternate contacts |
| **Lost to Follow-up (LTFU)** | 90+ days | 🟥 Red | Critical | Final outcome logging |

### Dial Lock Feature

For **Missed Appointments** under 7 days, the dial button is **locked** (greyed out). These patients receive an automated SMS reminder instead of a phone call. Once the 7th day is reached, the dial unlocks and a human tracer can call.

### Date Display

All dates are displayed in the **Ethiopian calendar** format (DD/MM/YYYY E.C.). The `tracedDate` field shows when the patient was last contacted, converted from the system timestamp.

### Retrace Timer

After tapping **📞 Call** (or **Redial** on a second attempt), the **🔍 Trace** button is hidden for **25 seconds**. This intentional delay ensures the tracer completes the phone conversation before logging an outcome. The button appears automatically once the timer expires.

- **With phone number:** Trace button appears 25 seconds after the Call/Redial tap
- **No phone number:** Trace button appears immediately (no call to make, tracer proceeds directly to logging)

### Patient Card Actions

| Action | Description |
|--------|-------------|
| **📞 Call** | Dial the patient's phone number |
| **🔍 Trace** | Open the Tracing Dialog to record an outcome |

---

## 6. Mobile App — Tracing Overdue Dashboard

The Overdue tab provides a comprehensive dashboard of **all traced patients**, grouped by their most recent tracing outcome. Each section is a collapsible card.

### Section 1: Agreed to Return Visit (Green)

Patients who agreed to return on a specific date are split into two sub-categories:

| Sub-Category | Description | Dial Status |
|-------------|-------------|-------------|
| **Pending** | Return date is in the future | 🔒 Locked (waiting for patient to return) |
| **Not Returned** | Return date has passed without patient returning | ✅ Unlocked (call to follow up) |

Each patient card shows:
- Patient name with days-overdue badge
- MRN (Medical Record Number)
- **Traced Date** — When the tracing was logged (Ethiopian calendar)
- **Return Date** — The agreed return date (Ethiopian calendar, with local time)
- Phone number with Call / Redial button
- **Retrace** button to log a new tracing outcome

### Section 2: Not Reachable (Orange)

Patients whose phone could not be reached:

| Outcome | Icon | Suggested Next Action |
|---------|------|----------------------|
| **Phone Not Working** | 📵 | Check alternate contacts, community tracing |
| **No Answer** | 📞❌ | Retry at different time of day, send SMS |

### Section 3: Removed from Visit (Red)

Patients who have been permanently or temporarily removed from the tracing list:

| Outcome | Severity | Next Action |
|---------|----------|-------------|
| **Transferred** (to another facility) | Permanent | Close file |
| **Self-Transferred** (moved by self) | Permanent | Close file |
| **Refused Care** | Permanent | Document refusal |
| **Deceased** | Permanent | Send condolence SMS |
| **Already Visited** | Temporary | Record next appointment date |

> [!WARNING]
> Permanent outcomes are **irreversible**. The patient will not appear in future tracing lists. A critical confirmation dialog is shown before any permanent outcome is saved.

### Filters

Both the Tracing Catalog and Tracing Overdue tabs include powerful filtering:

| Filter | Purpose |
|--------|---------|
| **Search Field** | Filter by patient name, phone, or MRN |
| **Disease / Condition** | All, DM, HTN, DM & HTN, Others |
| **Overdue Duration** | All, 1–14 days, 15–30 days, >1 month |
| **Drug Adherence** | All, Good, Poor, Unknown |
| **Traced Date Range** | Start and End dates (Ethiopian calendar picker) |

> **Filter Count Badges:** The filter icon shows a badge with the total number of patients matching the applied filters. This helps you quickly see the scope of filtered results.

> **Filter Panel UX:** Tap the filter icon to expand the filter panel with a smooth sliding animation. Tap anywhere outside the filter panel to close it again. The filter panel also collapses automatically when you tap on patient cards below.

---

## 7. The Tracing Dialog — Full Reference

When you tap **Trace** or **Retrace** on a patient card, the **Tracing Dialog** opens as a modal bottom sheet. This is where you record the outcome of your phone outreach.

### Dialog Sections

| Section | Content |
|---------|---------|
| **Profile Header** | Patient name, MRN, diagnosis with gradient avatar |
| **TRACINGS Section** | Two dropdown selectors: Overdue Status and Tracing Outcome |
| **SCHEDULING Section** | Date picker for return visit (shown for "Agreed to Return Visit" and "Already Visited") |
| **OBSERVATIONS Section** | Free-text notes field for clinical observations |
| **Submit Button** | "SAVE TRACE RECORD" with gradient styling |

### Overdue Status Options

| Status | Requires Outcome? | Requires Date? | Quota Check? |
|--------|-------------------|----------------|--------------|
| **Agreed to Return Visit** | No | Yes (return date) | Yes |
| **Not Reachable** | Yes | No | No |
| **Removed from Visit** | Yes | No | No |

### Tracing Outcome Options

**Not Reachable** sub-options:

| Outcome | Icon | When to Use |
|---------|------|-------------|
| `Phone Doesn't working` | 📵 | The number is disconnected, out of service, or wrong |
| `Patient not answering` | 📞❌ | Phone rings but no one answers after multiple attempts |

**Removed from Visit** sub-options:

| Outcome | Icon | Permanent? | Special Handling |
|---------|------|------------|------------------|
| `Transferred to another health facility` | 🔄 | ✅ Yes | Critical warning dialog |
| `Moved to another health facility by his/her self` | 🚶 | ✅ Yes | Critical warning dialog |
| `Refused to came back` | 🚫 | ✅ Yes | Critical warning dialog |
| `Died` | 💔 | ✅ Yes | Critical warning dialog; condolence SMS sent |
| `Already Visited` | ✅ | ❌ No | Requires next appointment date |

### Critical Warning

For permanent outcomes (Died, Transferred, Self-Transferred, Refused Care), a **red animated critical warning dialog** appears with:

- Gradient header with warning icon
- Patient name and outcome details
- Notice that the change is permanent and irreversible
- **For Died outcome**: A blue info box stating "The condolence expression SMS will be sent to the family"
- A confirmation checkbox: "I understand this action is permanent and irreversible"
- **CONFIRM** button (enabled only after checkbox is checked) and **CANCEL** button

### Quota Check (Agreed to Return Visit)

When a return date is selected, the app automatically checks the daily appointment quota:

| Badge Color | Meaning |
|-------------|---------|
| 🟢 Green | Available — slots remaining |
| 🟠 Orange | Almost Full — 3 or fewer slots remaining |
| 🔴 Red | Full — no slots available; submit is blocked |

---

## 8. Tracing Protocol — Prioritization & Workflow

### 8.1 Core Principles

1. **Timeliness** — The sooner a missed appointment is addressed, the more likely the patient is to return to care
2. **Proportional Response** — The intensity of tracing should match the severity of the gap in care
3. **Documentation** — Every outreach attempt must be logged with a clear outcome
4. **Patient Safety** — Never permanently close a record without documented attempts

### 8.2 Who Should Be Prioritized

Priority is determined by a combination of **days missed**, **diagnosis**, **adherence history**, and **clinical risk**:

| Priority Level | Criteria | Action Timeline |
|---------------|----------|-----------------|
| **Critical** | LTFU (90+ days) + Poor adherence + High-risk diagnosis (DM with complications) | Immediate — within 24 hours |
| **High** | Defaulter (15–89 days) + Poor adherence OR High-risk diagnosis | Within 48 hours |
| **Medium** | Missed appointment (1–14 days) + Poor adherence | Within 72 hours |
| **Standard** | Missed appointment (1–14 days) + Good adherence | Within 7 days |
| **Monitor** | Defaulters with recent phone contact who agreed to return | Track pending return date |

**Priority by Diagnosis:**
1. **DM (Diabetes Mellitus)** — Highest priority due to risk of acute complications (DKA, hypoglycemia)
2. **DM & HTN** — High priority (dual morbidity)
3. **HTN (Hypertension)** — Medium priority (often asymptomatic)
4. **Others** — Standard priority

**Priority by Adherence:**
1. **Poor** — Highest concern, regardless of days missed
2. **Fair** — Medium concern
3. **Good** — Lowest concern within each tier

### 8.3 When to Trace — By Category

#### Missed Appointments (1–14 Days)

| Days Missed | Action | Who Traces |
|-------------|--------|------------|
| 1–6 days | Automated SMS reminder sent; dial is **locked** in the mobile app | System (auto) |
| 7–14 days | Phone tracing by Data Clerk or HEW | Data Clerk / HEW |

**Protocol:**
1. Call the patient using the in-app dialer
2. Ask about the missed appointment
3. Reschedule and record a new appointment date if possible
4. Log the outcome in the Tracing Dialog

#### Defaulters (15–89 Days)

| Days Missed | Action | Who Traces |
|-------------|--------|------------|
| 15–30 days | Phone tracing by assigned HEW | HEW |
| 31–59 days | Escalated tracing — check alternate contacts | Senior HEW |
| 60–89 days | Community tracing — home visit if possible | Community Health Worker |

**Protocol:**
1. Attempt phone call first
2. If unreachable, check if alternate phone numbers exist in the system
3. If still unreachable after 3 attempts, flag for community tracing
4. Document all attempts in the tracing log

#### Lost to Follow-Up (90+ Days)

| Duration | Action | Who Traces |
|----------|--------|------------|
| 90–119 days | Intensive outreach — phone + alternate contacts + community | Team Lead |
| 120+ days | Final outcome determination | Senior Clinician |

**Protocol:**
1. Make at least 3 phone attempts at different times of day
2. Attempt contact through alternate phone numbers
3. If the patient is reached, determine the reason for the gap
4. If unreachable after all attempts, log as "Phone Not Working" or "Patient not answering"
5. Do NOT mark as "Died" without independent verification (family contact, health facility record)

### 8.4 Tracing Workflow by Outcome

```
                             ┌─────────────────────────────┐
                             │  Patient Misses Appointment  │
                             └─────────────┬───────────────┘
                                           │
                                           ▼
                             ┌─────────────────────────────┐
                             │  Tracer Calls Patient        │
                             └─────────────┬───────────────┘
                                           │
                             ┌──────────────┴──────────────┐
                             │                             │
                             ▼                             ▼
              ┌────────────────────────┐     ┌──────────────────────────┐
              │  Patient Reached        │     │  Patient NOT Reached     │
              └────────────┬───────────┘     └─────────────┬────────────┘
                           │                               │
              ┌────────────┼────────────┐     ┌────────────┼────────────┐
              ▼            ▼            ▼     ▼            ▼            ▼
         ┌──────────┐ ┌──────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐
         │Agreed to │ │Already   │ │Refused/│ │Phone   │ │No      │ │Died    │
         │Return    │ │Visited   │ │Transfd │ │Not     │ │Answer  │ │(Verif.)│
         │Visit     │ │          │ │        │ │Working │ │        │ │        │
         └────┬─────┘ └────┬─────┘ └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘
              │            │           │          │          │          │
              ▼            ▼           ▼          ▼          ▼          ▼
         Set return   Record new  Permanent   No action  Retry at   Send
         date +       appt date   close &     needed     different  condolence
         check quota              document               time       SMS + close
```

### 8.5 Outcome-Specific Protocols

#### Agreed to Return Visit

| Step | Action | Details |
|------|--------|---------|
| 1 | Confirm agreement | Patient verbally agrees to come to the clinic |
| 2 | Select return date | Use the Ethiopian date picker — date must be a future weekday, non-holiday |
| 3 | Check quota | System verifies the daily return visit limit is not exceeded |
| 4 | Save | Outcome is logged; patient appears in "Pending" on the Overdue dashboard |
| 5 | Monitor | On the agreed return date, the system sends a reminder SMS |
| 6 | Follow up | If the patient does not return on the agreed date, they move to "Not Returned" and become eligible for retracing |

#### Not Reachable

| Outcome | Protocol |
|---------|----------|
| **Phone Not Working** | Verify the number. If confirmed disconnected, check for an alternate number in the patient record. If no alternate, flag for community tracing. |
| **Patient not answering** | Note the time of day. Try again at a different time (morning vs. afternoon). After 3 failed attempts on different days, escalate. |

#### Removed from Visit

| Outcome | Verification Required | Documentation |
|---------|----------------------|---------------|
| **Transferred** | Confirm receiving facility name and contact | Record transfer-out details |
| **Self-Transferred** | Patient confirms new location | Note new location in observations |
| **Refused Care** | Patient explicitly states refusal | Document reason for refusal |
| **Died** | **Must be verified** — confirm with family member or health facility record, NOT hearsay | Send condolence SMS automatically |
| **Already Visited** | Patient confirms they attended another clinic or came on a different date | Record the actual visit date and next appointment |

> [!CAUTION]
> **Death Verification Protocol:** A "Died" outcome must NEVER be logged based solely on unanswered phone calls. The tracer must:
> 1. Speak to a family member who confirms the death, OR
> 2. Obtain confirmation from another health facility, OR
> 3. View an official death record
> 
> Logging "Died" triggers automated condolence SMS to the family. False logging causes distress and erodes trust.

---

## 9. Return Visit Quota Management

The system enforces a **daily limit** on the number of "Agreed to Return Visit" appointments that can be scheduled per day.

### How the Quota Works

| Component | Source | Description |
|-----------|--------|-------------|
| **Daily Limit** | ApptSettings sheet | Configurable by Administrators (default: 10) |
| **Booked Count** | Tracings sheet | Count of "Agreed to Return Visit" records matching the date |
| **Remaining** | Calculated | `limit - booked` |

### What Happens When Quota Is Full

1. The app displays a red badge: **"Full — X/Y booked"**
2. The submit button is **disabled**
3. The user must select a different date
4. The quota is NOT consumed for the blocked submission

### Duplicate Patient Detection

If a patient already has an appointment recorded on the selected date, the system displays:

> **"Patient has already appointed to this day (DD/MM/YYYY E.C.). Please choose another date."**

The submission is blocked and the quota is **not** consumed.

---

## 10. Web App (Desktop) — Quick Reference

The NARTS Web App is accessed through a browser on desktop or tablet. It provides additional features not available in the mobile app.

### Five Main Tabs

| Tab | Icon | Purpose |
|-----|------|---------|
| **Dashboard** | 📊 | At-a-glance clinical statistics and animated trend charts |
| **Patients** | 👥 | Search, register, and manage patient records (full detail view) |
| **Missed Appointments** | 🔴 | Patients who have not attended their scheduled appointment |
| **Appointments** | 📅 | Daily and diurnal appointment schedule with filter options |
| **Settings** | ⚙️ | Account settings and (Admin) user management |

### Appointments Tab — Diurnal Calendar View

The **Appointments** tab offers two view modes:

| View | Description |
|------|-------------|
| **Timeframe** | Breakdown by appointment window (Short ≤30d, 2-Month 31–60d, 3-Month 61–90d, Extended >90d) |
| **Diurnal** | Daily "calendar postcard" view showing per-day totals split by diagnosis (DM, HTN, DM & HTN, Others) |

**Diurnal Filter Buttons:** When in Diurnal mode, a filter bar at the top lets you focus on specific appointment types:

| Filter | Behaviour |
|--------|-----------|
| **All** | Shows all future appointments (default) |
| **Routine** | Shows only routine scheduled appointments (excludes patients with an "Agreed to Return Visit" tracing record) |
| **Agreed** | Shows only appointments resulting from tracing (patients who have an "Agreed to Return Visit" outcome) |

The calendar toggle (ETC/GC) switches between Ethiopian and Gregorian calendar display.

### Key Differences from Mobile App

| Feature | Web App | Mobile App |
|---------|---------|------------|
| **Dashboard Charts** | ✅ Full analytics suite | ❌ Not available |
| **SMS Campaigns** | ✅ Full SMS management | ❌ Not available |
| **Appointment Scheduling** | ✅ Full schedule view | ❌ Not available |
| **User Administration** | ✅ Role & account management | ❌ Not available |
| **Tracing / Outreach** | Patient counts only (no inline tracing form) | ✅ Full tracing workflow |
| **Phone Dialer** | ❌ Not available | ✅ Click-to-call |
| **Patient Registration** | ✅ Available | ✅ Available |
| **Feedback Management** | ✅ Available | ❌ Not available |

> [!NOTE]
> **Tracing is mobile-only.** The Web App displays patient counts per category in the Reminder Catalog and Overdue Dashboard, but inline tracing forms and dial actions are disabled. All tracing (phone outreach, outcome logging, return visit scheduling) must be performed through the **N-ARTS Mobile Flutter App**, where the dialer is available.

---

## 11. SMS Features

NARTS automatically sends Amharic-language SMS messages to patients at key points in their care journey. All SMS requires patient consent.

### SMS Types

| SMS Type | When It Is Sent | Language |
|----------|----------------|---------|
| **Consent Request** | Immediately upon patient registration | Amharic 🇪🇹 |
| **72hr Appointment Reminder** | 3 days before scheduled appointment, 3 PM EAT | Amharic 🇪🇹 |
| **24hr Appointment Reminder** | Day before scheduled appointment, 3 PM EAT | Amharic 🇪🇹 |
| **Missed Appointment** | 1–6 days after a no-show (auto, no dial needed) | Amharic 🇪🇹 |
| **Agreed Return-Visit Reminder** | Day before the patient's agreed return date | Amharic 🇪🇹 |
| **Health Education** | Periodic educational messages (sent manually) | Amharic 🇪🇹 |
| **Condolence** | Sent automatically when "Died" outcome is logged | Amharic 🇪🇹 |
| **Feedback Request** | Sent to patient after visit for quality feedback | Amharic 🇪🇹 |

> **Note:** The **72hr** and **24hr** appointment reminders are triggered automatically at 3:00 PM EAT daily. Each can be toggled on/off independently from the **Admin → SMS Control Center → Automated Categories**.

### Consent Status

| Icon | Meaning |
|------|---------|
| 📱 SMS icon (blue) | No consent SMS sent yet |
| ⏳ Pending | Consent SMS sent — awaiting the patient's reply |
| ✅ Agreed (green) | Patient agreed — SMS communications enabled |
| ❌ Disagreed (red) | Patient declined — no SMS will be sent |

---

## 12. Dark Mode & Theme

### Dim Mode (Default)

- Background: Deep charcoal (`#0F172A`)
- Accent: Neon cyan (`#00E5FF`)
- Surfaces: Dark glass with subtle borders
- Ideal for: Low-light field conditions, battery saving on AMOLED screens

### Light Mode

- Background: Clean white
- Accent: Medical blue (`#0284C7`)
- Surfaces: Light glass with soft shadows
- Ideal for: Bright outdoor use, shared viewing

Use the toggle options in the navigation drawer — select **"Dim Mode"** (🌙) or **"Light Mode"** (☀️) — to switch between themes. Your preference is applied immediately and persists for the current session.

---

## 13. Frequently Asked Questions

**Q: A patient says they did not receive their SMS reminder. What should I check?**
> First, confirm the patient's **consent status** is ✅ Agreed. If it shows Pending or Disagreed, no automated SMS will be sent. Also verify their phone number is saved in the correct Ethiopian format.

**Q: I accidentally marked a patient as "Died". Can I undo it?**
> No — permanent outcomes (Died, Transferred, Refused Care) are **irreversible**. This is why a critical warning dialog is shown before any permanent outcome is saved. If this occurs, contact your System Administrator immediately.

**Q: The app shows "Dial Locked" for a patient. What does this mean?**
> Patients with **less than 7 days** of missed appointment time have automated SMS handling instead of phone calls. The dial unlocks automatically on day 7.

**Q: Why does the Overdue tab show a different date than the Tracings sheet?**
> The mobile app displays dates in the **Ethiopian calendar**. Times are shown in **Ethiopian local time** (e.g., `ጠዋት 2:30` = 8:30 AM Gregorian). The Tracings sheet stores the same data with the same format.

**Q: Can I register a patient without a phone number?**
> No — a valid Ethiopian phone number is required for SMS consent and appointment reminders. If the patient has no phone, consult your supervisor about alternative tracking methods.

**Q: The quota is full for a date. What should I do?**
> Select a different date. The daily return visit limit is configured by your Administrator based on clinic capacity. Choosing an alternative date ensures balanced patient flow.

**Q: A patient's phone number has changed. How do I update it?**
> Open the patient's card in the **Patients** tab and tap the edit (✏️) icon. Update the phone number and save. The system will send a new consent request.

**Q: The system is showing dates I don't recognize. Can I switch calendars?**
> The mobile app uses the **Ethiopian calendar** natively. The Web App provides a Gregorian / Ethiopian toggle on each tab and chart.

---

## 14. Support

For technical assistance, contact your **hospital IT department** or the **NARTS System Administrator**.

| Role | Responsibility |
|------|---------------|
| **System Administrator** | Account management, role assignments, quota configuration, data integrity |
| **NCD Department Head** | Clinical policy oversight, priority protocol adjustments |
| **Hospital IT Department** | App installation, connectivity, backend support |
| **Data Protection Officer** | Privacy rights, patient data access requests |

---

*© 2026 Kidus Petros Hospital — NCD Department*
*NARTS User Manual v2.2 — Authorised Clinical Staff Only*
