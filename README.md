# CMP701 Digital Transformation — Marking Tracker

Live marking coordination tool for Ulster University QAHE across London, Birmingham, and Manchester campuses.

**Live app:** https://tertsegha1.github.io/cmp701-tracker/

---

## Overview

A single-page web app that gives the module leader a real-time view of CW1 and CW2 marking progress across all markers and campuses. All changes sync instantly via Firebase Realtime Database — no login, no manual saving, no emailing spreadsheets.

---

## For Markers — How to Update Your Progress

1. Open the link above in any browser
2. Click the **Marker View** tab
3. Select your name from the dropdown
4. For each student, set the **Status**:

| Status | When to use |
|---|---|
| **Yes** | Marked and completed |
| **Non-Submission** | Student did not submit |
| **EC1 Approved** | Extenuating circumstances approved |
| **Not Required** | Student no longer on the module |

5. Add any relevant details in the **Notes** column
6. Changes save automatically — look for the green **✓ Saved** flash

> Your updates are visible to the module leader and the full team the moment you make them.

---

## For the Module Leader

### Dashboard
Overview of CW1 and CW2 allocation and progress across all campuses. KPI cards show total enrolment, marks allocated, completed, and remaining.

### CW1 / CW2 Trackers
Full student-level view with inline editing. Filter by campus or status, or search by student name. Export to CSV at any time.

### Non-Submissions
Auto-populated list of students with Non-Submission or Not Required status, ready for report generation.

### Allocation
Breakdown of marking load per marker, grouped by campus and session type (Lecture 40% / Seminar 60% / Full group 100%).

### New Cohort
Upload a new student list CSV to onboard the next cohort. Required columns: `Marker, Campus, Group, SessionType, StudentName`. Download the template from within the app.

---

## Key Dates — 2025–26 Cohort

| | CW1 — Video Presentation (25%) | CW2 — Written Report (75%) |
|---|---|---|
| Submission deadline | 13 March 2026 | 6 May 2026 |
| Marking deadline | 27 March 2026 | 20 May 2026 |

---

## Technical Notes

- **Stack:** Vanilla HTML/CSS/JS — no build step, no dependencies beyond Firebase
- **Sync:** Firebase Realtime Database (`cmp701markingtracker` project). The header badge shows `✓ Live` when connected.
- **Offline fallback:** Data is cached in `localStorage` so the app loads instantly even without a network connection. Changes made offline will not sync until reconnected.
- **Hosting:** GitHub Pages, auto-deployed from the `main` branch

### Updating the App
Edit `index.html`, then run in PowerShell from the project folder:

```powershell
git add index.html
git commit -m "your message"
git push
```

GitHub Pages redeploys automatically within ~1 minute.

---

*Module Leader: Dr. Tertsegha Anande · Ulster University QAHE*
