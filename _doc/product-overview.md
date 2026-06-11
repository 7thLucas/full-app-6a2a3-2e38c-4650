# Allied Financial Insurance — Compliance Management App

**Product**: Web-based internal compliance management platform for Allied Financial Insurance (AFI)
**Tagline**: Compliance, Tracked. Automatically.
**Type**: Internal enterprise web application

---

## What It Is

A unified digital compliance management system that automates the tracking, documentation, and escalation of mandatory compliance requirements for AFI employees — starting with the Sales and Compliance/Risk departments. Employees upload required documents and see real-time color-coded scorecards; HR/Admin manages rules, monitors company-wide compliance health, and generates audit-ready reports — all in one platform.

---

## Personas

### 1. Employee
Sales Representatives, Compliance Analysts, Risk Managers, and all department staff. They log in to view their personal compliance scorecard, upload required certificates and forms, enter quiz scores, and act on pending items — from desktop or mobile.

### 2. HR / Compliance Admin
HR coordinators and the Chief Compliance Officer (CCO). They configure compliance rules per department and role, monitor department-wide status in a live dashboard, send reminders, trigger or receive escalations, and export audit-ready reports on demand.

---

## Departments & Compliance Items (Initial Scope)

### Sales Department — 7 Items

| ID  | Item                                  | File Type       | Min Score | Renewal     |
|-----|---------------------------------------|-----------------|-----------|-------------|
| A.1 | AML Training                          | PDF + Numeric   | 80        | Annual      |
| A.2 | Anti-Fraud Training                   | PDF + Numeric   | 80        | Annual      |
| A.3 | Data Privacy Training (GLBA)          | PDF + Numeric   | 80        | Annual      |
| A.4 | State Producer License                | PDF             | N/A       | Per state   |
| A.5 | SOP / Compliance Acknowledgment Form  | PDF             | N/A       | Annual      |
| A.6 | Sales Compliance Knowledge Assessment | Numeric only    | 80        | Annual      |
| A.7 | Code of Conduct Acknowledgment        | PDF             | N/A       | Annual      |

### Compliance / Risk Department — 9 Items

| ID  | Item                                          | File Type       | Min Score | Renewal   |
|-----|-----------------------------------------------|-----------------|-----------|-----------|
| B.1 | AML Training (Enhanced)                       | PDF + Numeric   | 85        | Annual    |
| B.2 | Anti-Fraud Training (Enhanced)                | PDF + Numeric   | 85        | Annual    |
| B.3 | Data Privacy Training (Enhanced — GLBA+CCPA)  | PDF + Numeric   | 85        | Annual    |
| B.4 | CRCM Certification                            | PDF             | Pass/Fail | 3 Years   |
| B.5 | BSA / OFAC Compliance Training                | PDF + Numeric   | 85        | Annual    |
| B.6 | Risk Assessment & Internal Controls Cert.     | PDF + Numeric   | 80        | Annual    |
| B.7 | SOP Ack. + Conflict of Interest Disclosure    | PDF (2 files)   | N/A       | Annual    |
| B.8 | Compliance/Risk Knowledge Assessment          | Numeric only    | 85        | Annual    |
| B.9 | Code of Conduct Acknowledgment                | PDF             | N/A       | Annual    |

---

## Core Features

### Employee-Facing
- **Personal Compliance Scorecard** — color-coded per item: Complete (green), At Risk (amber), Overdue (red), Not Applicable (gray). Each item shows status, due date, expiration, and next required action.
- **Document Upload Portal** — upload PDFs for certificates and forms; enter numeric scores for quizzes. System validates file type, score threshold, and completeness on submission.
- **Pending Actions List** — items ordered by urgency with due dates, instructions, and direct upload links.
- **Submission History** — immutable log of all past uploads, scores, and status changes.
- **Mobile-friendly** — fully responsive design for desktop and mobile access.

### HR / Admin-Facing
- **Compliance Dashboard** — overall company health score, department summaries, top missing items, upcoming expirations (30/60/90-day views), and open escalations.
- **Rule Configurator** — set mandatory status, file type (PDF/numeric), passing score threshold, renewal/expiration interval, and escalation rules per department, per role, and per compliance item. Rules are versioned and auditable.
- **Expiration Calendar** — visual timeline of upcoming certificate and license renewals by employee and department.
- **Reminder Engine** — send individual or bulk email reminders; automated reminders fire at 90 days, 30 days, and 7 days before expiration, and every 7 days after.
- **Escalation Manager** — structured escalation chain: Manager → HR → CCO at configurable day thresholds. All escalation events are timestamped and logged.
- **Audit Log** — immutable record of every upload, status change, rule edit, reminder sent, and escalation triggered — with user attribution and timestamps.
- **Export** — CSV and PDF reports for any employee, department, date range, or compliance item — formatted for regulatory examination.

---

## Compliance Scorecard Logic

Each compliance item for each employee carries one of four statuses, derived automatically:

| Status         | Condition                                                          |
|----------------|--------------------------------------------------------------------|
| **Compliant**  | Valid document on file (not expired) AND score ≥ threshold        |
| **At Risk**    | Expiring within 30 days, OR score gap, OR renewal pending         |
| **Overdue**    | Expired, missing mandatory item, or score below threshold         |
| **N/A**        | Item not applicable to this employee's role/department            |

An employee's overall scorecard status is **Compliant** only when ALL mandatory items are Compliant.

---

## Escalation Rules (Default)

| Trigger                         | Action                                         | Owner            |
|---------------------------------|------------------------------------------------|------------------|
| Expiration date reached (Day 0) | Auto-reminder to employee + manager            | System           |
| Day +7 overdue                  | "At Risk" flag; second reminder                | System + HR      |
| Day +14–15 overdue              | HR notified; manager written acknowledgment    | HR Coordinator   |
| Day +30 overdue (Sales)         | Restrict customer-facing activities; CCO alert | CCO + Manager    |
| Day +30 overdue (C/Risk)        | Review oversight duties; CCO direct notify     | CCO              |
| Day +45 overdue                 | Open formal disciplinary record                | HR + CCO         |
| License expired (Sales)         | Immediate removal from licensed sales activity | CCO + HR         |
| CRCM expired (C/Risk)           | Review role eligibility                        | CCO + HR         |

---

## Brand & Tone

**Voice**: Professional, authoritative, and enterprise-grade. The app serves compliance professionals in a regulated financial services entity — it must feel dependable, transparent, and built for serious institutional use.

**Color palette**: Deep navy blue (primary) + amber/gold (accent) — reinforcing trust, credibility, and institutional weight. Backgrounds: white and light gray. Status colors: green (compliant), amber (at risk), red (overdue).

**Typography**: Clean, high-legibility sans-serif. Strong hierarchy: bold display for metrics and headlines, concise supporting copy, structured tables and labels for compliance data.

---

## Technical Scope (MVP)

- Web app — mobile-friendly and desktop-ready (responsive)
- Two initial departments: Sales and Compliance/Risk
- Employee portal (scorecard + upload + history)
- HR/Admin dashboard (metrics + rule config + reminders + escalations)
- Automated alerts and escalation engine
- Immutable audit log
- CSV and PDF export
- Configurable rule engine per department, role, and compliance item

---

## Strategic Principles

1. **Rules-first, not hard-coded** — every compliance requirement is defined as a configurable rule, not baked into the UI, so HR can extend to new departments or items without a rebuild.
2. **Audit-ready at all times** — the system maintains a complete, timestamped record of every action so no manual assembly is needed for an examination.
3. **Employee clarity over HR burden** — employees should never be surprised by a compliance gap; the scorecard and alerts exist to surface problems before they become escalations.
4. **Escalation as a system function** — the escalation chain is automatic and consistent, not dependent on HR remembering to follow up.
