# CMP701 Digital Transformation — Marking Tracker

Live marking coordination tool for Ulster University QAHE across London, Birmingham, and Manchester campuses.

**Live app:** https://tertsegha1.github.io/cmp701-tracker/

---

## Signing In

When you open the app, a login screen appears. Choose your role:

- **I am the Module Leader** — enter your admin PIN for full access
- **I am a Marker** — select your name from the dropdown to access your student list

Your session stays active if you refresh the page. It clears when you close the browser tab. Use the **Sign Out** button in the top-right corner to switch roles.

---

## For Markers

1. Open the link above and select **I am a Marker**
2. Choose your name from the dropdown and click **Enter as Marker**
3. You will land on the **Marker View** tab, filtered to your students only
4. For each student, update the **Status** using the dropdown:

| Status | When to use |
|---|---|
| **Yes** | Marked and completed |
| **Non-Submission** | Student did not submit |
| **EC1 Approved** | Extenuating circumstances approved |
| **Not Required** | Student no longer on the module |

5. Add any comments in the **Notes** column
6. Changes save automatically — look for the green **✓ Saved** flash

> Updates are visible to the module leader the moment you make them. No need to email or export anything.

---

## For the Module Leader

Sign in with **I am the Module Leader** and your admin PIN (default: `CMP701Admin`).

### Access & Permissions

| Feature | Module Leader | Marker |
|---|---|---|
| Dashboard (full view + shuffle) | ✅ | Read-only |
| Marker View (own students) | ✅ | ✅ |
| CW1 / CW2 Trackers | ✅ | — |
| Non-Submissions | ✅ | — |
| Allocation | ✅ | — |
| New Cohort / Manage Cohorts | ✅ | — |

### Dashboard
Overview of CW1 and CW2 allocation and progress across all campuses. KPI cards show total enrolment, marks allocated, completed, and remaining. Includes the shuffle tool to redistribute students within split groups.

### CW1 / CW2 Trackers
Full student-level view with inline editing across all markers. Filter by campus or status, search by student name, and export to CSV at any time.

### Non-Submissions
Auto-populated list of students with Non-Submission or Not Required status, ready for board reporting.

### Allocation
Breakdown of marking load per marker, grouped by campus and session type (Lecture 40% / Seminar 60% / Full group 100%).

### New Cohort
Upload a new student list CSV each semester. Required columns: `Marker, Campus, Group, SessionType, StudentName`. Download the template from within the app.

> The marker login dropdown automatically updates each semester when a new cohort CSV is uploaded — no manual list to maintain.

---

## Changing the Admin PIN

1. Go to [Firebase Console](https://console.firebase.google.com/project/cmp701markingtracker/database) → Realtime Database
2. Find the `adminPin` node at the root level
3. Click the value and type the new PIN → press Enter

The change takes effect immediately.

---

## Key Dates — 2025–26 Cohort

| | CW1 — Video Presentation (25%) | CW2 — Written Report (75%) |
|---|---|---|
| Submission deadline | 13 March 2026 | 6 May 2026 |
| Marking deadline | 27 March 2026 | 20 May 2026 |

---

## Technical Notes

- **Stack:** Vanilla HTML/CSS/JS — no build step, no dependencies beyond Firebase
- **Auth:** Session-based (sessionStorage) with role stored client-side. Admin PIN validated against Firebase.
- **Sync:** Firebase Realtime Database (`cmp701markingtracker` project). Header badge shows `✓ Live` when connected.
- **Offline fallback:** Data cached in `localStorage` — app loads instantly without a network connection. Changes sync when reconnected.
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
