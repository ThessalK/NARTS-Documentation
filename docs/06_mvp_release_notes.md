# NARTS v1.1 — MVP Release Notes & Product Roadmap

> **St. Peter's Specialized Hospital · NCD Care Department**
> *Release: March 2026*

---

## 🚀 About This Release

NARTS v1.1 extends the Minimum Viable Product for the NCD Appointment & Retention Tracking System. This release introduces stringent data entry validation, highly engaging medical-grade UI animations, and lays the fundamental offline-first architecture to handle the unique networking demands of clinical delivery in Ethiopia.

---

## ✅ Features Delivered in v1.1

### 🧑‍⚕️ Patient Management & Data Quality
- [x] Patient registration with **Strict Amharic Name Validation** (Unicode `\u1200-\u137F`).
- [x] OS-level Voice typing fallback for Name dictates (bypassing Google Sandbox restrictions).
- [x] Instant patient search by name, MRN, or phone number.
- [x] Appointment recording and updating per visit.
- [x] Drug adherence tracking (Good / Fair / Poor) and Tracing.

### 📅 Appointment Retention System
- [x] Automatic patient status classification based on days since last appointment.
- [x] Patient tracing and outreach record management with high-fidelity Custom Modals replacing native browser alerts.
- [x] Agreed return-visit scheduling and tracking.

### 📲 Mobile Sync & Infrastructure
- [x] Resolution of Mobile Companion App routing (fixing 500 Server Errors).
- [x] UTF-8 character encoding fixes ensuring uncorrupted Amharic transmission to the mobile layout.
- [x] **PWA Foundation:** Initialization of the Offline-First structure using IndexedDB capability hooks for future Service Worker syncing.

### 📊 Analytics Dashboard
- [x] Dynamic **ECG & Stethoscope UI Loading Animations** directly inside dashboard canvas points.
- [x] Service rating trend chart (weekly satisfaction).
- [x] Missed appointments analytics with ETC/GC toggle.
- [x] Diurnal (hourly) appointment distribution view.

### 💬 Patient Feedback Component
- [x] External public patient feedback UI.
- [x] Star-rating feedback submission natively tracked into the central Sheets node.

### 🇪🇹 Ethiopian Localization
- [x] Bidirectional Gregorian ↔ Ethiopian Calendar conversion.
- [x] All patient-facing SMS messages in Amharic.
- [x] Ethiopian time period labels (ጠዋት / ረፋድ / ከሰዓት).

---

## ⚠️ Known Limitations (Current Scope)

The following items are intentionally unactivated for v1.1 and are actively tracked in the roadmap:

| Limitation | Clinical Impact | Priority |
|-----------|----------------|---------|
| **Iframe Web APIs Block** | Voice dictates require OS-level fallback instead of native buttons. | 🔴 High |
| Google Sheets as database (~5k limit) | Performance risk at high scaling context. | 🟡 Medium |
| SMS delivery depends on SMS-Gate.app | No fallback if gateway is intermittently down. | 🔴 High |

---

## 📅 Strategic Roadmap

Future development aligns structurally with the **Ethiopia Digital Health Blueprint 2021–2030**.

### Phase 1 — Decentralization & Offline Resilience *(Q2–Q3 2026)*
> [!NOTE] 
> Focus is heavily shifting to extracting the UI from Google's iframe into its own Independent PWA.

- [ ] **Full PWA Standalone Mode** — Complete transition out of the Google Sandbox, activating Web Speech APIs.
- [ ] **Background Synchronization** — Service Workers recording data locally and syncing to Sheets when connectivity restores.

### Phase 2 — Institutional Integration *(Q4 2026)*
- [ ] **Bahmni EMR Integration** — Bi-directional sync with St. Peter's central EMR.
- [ ] **Automated Nightly Backups** — Redundant copies to Google Drive.
- [ ] **SMS Delivery Receipts** — Tracking confirmed vs. failed delivery.

### Phase 3 — National eHealth Architecture & Scale *(2027+)*
- [ ] **HL7 FHIR Integration** — National data exchange compliance.
- [ ] **ICD-11 (ESV-ICD11) Diagnostic Coding**.
- [ ] **Mobile Outreach App (Android)** — Offline-capable tool specifically for Health Extension Workers.

---

## 🧪 Testing Summary

| Test Area | Method | Result |
|-----------|--------|--------|
| Amharic Regex Validation | Unit Test & UI Manual Input | ✅ Pass |
| Mobile Sync Layout | Fetch Simulation | ✅ Pass |
| Login flow (all roles) | Manual browser testing | ✅ Pass |
| Patient registration | Manual end-to-end | ✅ Pass |
| SMS consent flow | Manual with live phone reply | ✅ Pass |

---

*NARTS v1.1 MVP · March 2026*  
*St. Peter's Specialized Hospital — NCD Department · Addis Ababa, Ethiopia*
