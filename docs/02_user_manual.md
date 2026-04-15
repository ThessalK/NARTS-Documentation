# NARTS — User Manual

> **Non-Communicable Disease Appointment & Retention Tracking System**
> *St. Peter's Specialized Hospital — NCD Care Department*
> *Version 1.1 · March 2026*

---

> [!TIP]
> **Who is this for?** This manual is written for all clinical and administrative staff who use NARTS — Physicians, Nurses, Health Extension Workers (HEW), and System Administrators. No technical background is required.

---

## 🚀 Getting Started

### Step 1 — Open the Application

Open **Chrome** (recommended) on any device and navigate to your hospital's NARTS link.

```
🌐  [Your Hospital NARTS URL]
📱  Works on smartphones, tablets, and desktop computers
```

### Step 2 — Log In

1. Enter your **registered phone number** (e.g. `0912345678` or `+251912345678`)
2. Enter your **password**
3. Click **"Login"**

> [!NOTE]
> **First time using NARTS?** Click **"Register Account"** to submit your account request. Your account will be reviewed and approved by an Administrator before you can log in.
>
> **Forgot your password?** Click **"Forgot Password"** — an Administrator can initiate a reset on your behalf.

---

## 🧭 Navigation — The Five Main Tabs

After logging in, you will see five tabs at the top of your screen. Each tab opens a distinct area of the system:

| Tab | Icon | Purpose |
|-----|------|---------|
| **Dashboard** | 📊 | At-a-glance clinical statistics and animated trend charts |
| **Patients** | 👥 | Search, register, and manage patient records |
| **Missed Appointments** | 🔴 | Patients who have not attended their scheduled appointment |
| **Appointments** | 📅 | Daily and diurnal appointment schedule |
| **Settings** | ⚙️ | Account settings and (Admin) user management |

> [!IMPORTANT]
> Not all tabs are visible to every role. Administrators see additional panels and controls that are securely hidden from clinical staff.

---

## 👥 Patients Tab

### Searching for a Patient

1. Click the **Patients** tab
2. Type any part of the patient's **name**, **MRN**, or **phone number** in the search box
3. Matching results appear instantly below as you type

### Registering a New Patient (Validation Rules)

1. Click the **➕ Add Patient** button
2. Fill in the required fields:
   - **Full Name** — *Minimum three name parts required.* 
   - **MRN** — Medical Record Number
   - **Phone Number** — Ethiopian format (e.g. `0912345678`)
   - **Diagnosis** — `DM`, `HTN`, `DM and HTN`, or `Other`
3. Click **Save**

> [!WARNING]
> **Strict Amharic Name Rule:** To maintain data quality, the Full Name field **only accepts Amharic characters** (በአማርኛ ብቻ). Any English or non-Amharic characters will be automatically erased as you type. 

### 🎙️ Using Voice Dictation 
Because NARTS currently runs inside Google's secure Apps Script sandbox, native web microphones are blocked. To use voice dictation for patient names, use your Operating System's built-in voice tools:
* **On Windows PC:** Click the text field and press <kbd>Win</kbd> + <kbd>H</kbd> to open Windows Voice Typing.
* **On Mobile (Android):** Tap the text field, then tap the **Mic Icon** on your Gboard keyboard.

> 📲 As soon as a patient is cleanly saved, an **Amharic SMS consent request** is automatically sent to their phone. The system records the consent as `Pending` until the patient replies.

### The Patient Card

Each patient is displayed as a sleek card with all key clinical information at a glance:

```
┌───────────────────────────────────────────────────────┐
│  👤 አበበ ከበደ አለሙ                  [Consent: ✅]      │
│  MRN: 10245   ·   Dx: DM and HTN                     │
│  📞 +251912345678                                     │
│  ─────────────────────────────────────────────────── │
│  Last Appointment:    15 Jan 2026                     │
│  Next Appointment:    18 Mar 2026                     │
│  Drug Adherence:      Good                            │
│  Follow-up Adherence: Fair                            │
│  ─────────────────────────────────────────────────── │
│        [📱 SMS]    [✏️ Edit]    [📋 Update Appt]     │
└───────────────────────────────────────────────────────┘
```

### Consent Status Icons

The icon next to a patient's name shows their current SMS consent status:

| Icon | Meaning |
|------|---------|
| 📱 SMS icon (blue) | No consent SMS sent yet |
| ⏳ Pending | Consent SMS sent — awaiting the patient's reply |
| ✅ Agreed (green) | Patient agreed — SMS communications enabled |
| ❌ Disagreed (red) | Patient declined — no SMS will be sent |

---

## 🔴 Missed Appointments Tab

This tab automatically identifies and displays every patient who has not attended their scheduled appointment, ranked by how long they have been overdue.

### Patient Status Categories

| Indicator | Status | Days Overdue |
|-----------|--------|-------------|
| 🟡 Yellow | **Missed Appointment** | 1–14 days |
| 🔴 Red | **Defaulter** | 15–89 days |
| ⛔ Dark Red | **Lost to Follow-Up (LTFU)** | 90+ days |

### Filters

Use the filter controls at the top of this tab to narrow the list:
- **By Diagnosis:** DM / HTN / DM and HTN / Other
- **By Status:** Missed Appointment / Defaulter / LTFU
- **Calendar Toggle:** Switch between **Gregorian (GC)** and **Ethiopian (ETC)** dates using the toggle in the top-right corner

### Available Actions

| Action | How to Do It |
|--------|-------------|
| Record a tracing / outreach | Click **"Trace"** on the patient's row |
| Send a missed appointment SMS | Click **"📱 SMS"** on the patient's row |
| View full tracing history | Click the patient's name |

---

## 📅 Appointments Tab

### Diurnal View

Switch to **Diurnal** mode to see today's appointment schedule broken into hourly morning and afternoon slots. Each slot shows:
- Number of patients scheduled
- Dates in your preferred calendar system (ETC or GC)

---

## 📊 Dashboard Tab

The Dashboard gives the entire NCD clinic an evidence-based, real-time overview of patient retention and care quality. While loading, you will see highly detailed medical micro-animations (ECG and stethoscope vectors).

### Available Charts

| Chart | What It Shows |
|-------|---------------|
| **Service Rating Trend** | Weekly patient satisfaction scores |
| **Missed Appointments** | Count and trend of missed appointments over time |
| **Drug Adherence** | Good / Fair / Poor distribution across the clinic |
| **Follow-up Adherence** | Appointment attendance rate over time |
| **Diurnal Appointment Distribution** | How appointments are spread across the day |

> 🔄 **ETC / GC Toggle:** Every chart has a calendar toggle so you can view data in Gregorian or Ethiopian Calendar dates.

---

## 📲 SMS Features

NARTS automatically sends Amharic-language SMS messages to patients at key points in their care journey. All SMS requires patient consent.

### SMS Types

| SMS Type | When It Is Sent | Language |
|----------|----------------|---------|
| **Consent Request** | Immediately upon patient registration | Amharic 🇪🇹 |
| **Appointment Reminder** | Day before scheduled appointment, 9 AM EAT | Amharic 🇪🇹 |
| **Missed Appointment** | 1–6 days after a no-show | Amharic 🇪🇹 |
| **Agreed Return-Visit Reminder** | Day before the patient's agreed return date | Amharic 🇪🇹 |
| **Health Education** | Periodic educational messages (sent manually from Tracing) | Amharic 🇪🇹 |
| **Condolence** | Sent automatically when patient death is recorded via Tracing | Amharic 🇪🇹 |

---

## ⚙️ Settings Tab

### Available to All Staff — Profile Settings
- Change your own password (current password required)

### Available to Administrators Only — User Management
- **Approve / Reject** pending account registrations
- Change any user's **role** or **status**
- View all registered staff accounts

---

## 💬 Patient Feedback System

Patients can submit feedback anonymously using a separate public link — no login required:
```
[Your NARTS URL]?page=feedback
```

Administrators can:
1. Open **Settings → Feedbacks** to view all **Pending** submissions
2. Click **"Evaluate"** to record a response and mark the feedback as resolved

> [!NOTE]
> Only Administrators can see Pending feedback entries. Clinical staff see resolved feedback only.

---

## 🌙 Dark Mode & Light Mode

Use the **☀️ / 🌙 toggle** in the top-right corner to switch between dark mode (default) and light mode. The glassmorphism layers adjust natively. Your preference is applied immediately.

---

## ❓ Frequently Asked Questions

**Q: A patient says they did not receive their SMS reminder. What should I check?**
> First, confirm the patient's **consent status** is ✅ Agreed. If it shows Pending or Disagreed, no automated SMS will be sent. Also verify their phone number is saved in the correct Ethiopian format.

**Q: I try to type a patient's name but the letters disappear. Why?**
> The system enforces **Amharic characters only**. Make sure your system keyboard is set to Amharic. English letters will be aggressively erased.

**Q: A patient came in but their record still shows "Missed Appointment". How do I fix it?**
> Open the patient card, click **"Update Appointment"**, and record today's visit and the new appointment date. The status will update automatically.

**Q: The system is showing Gregorian dates. Can I change them to Ethiopian?**
> Yes — use the **ETC / GC toggle** button available on each tab and chart. The change applies immediately to the current view.

---

## 📞 Support

For technical assistance, contact your **hospital IT department** or the **NARTS System Administrator**.

---

*© 2026 St. Peter's Specialized Hospital — NCD Department*  
*NARTS User Manual v1.1 — Authorised Clinical Staff Only*
