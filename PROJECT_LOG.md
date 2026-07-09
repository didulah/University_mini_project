# PROJECT_LOG.md

> Purpose: This file is the persistent context log for this project. Paste this file's content (or point to it) at the start of a new chat with Claude so it can pick up exactly where the last session left off. Update it after every meaningful session.

---

## 1. Project Goal

Build a **Fingerprint-Based Student Attendance Management System** combining:
- Hardware: ESP32 + R307S fingerprint sensor + DS3231 RTC + OLED display + buzzer, battery-powered
- Software: Flask web app + SQLite database

Primary users: **Lecturers** (via web dashboard). Students only interact with the physical fingerprint device.

## 2. Hardware Inventory (already owned, per user)

- Fingerprint sensor — R307S
- Charging module
- 3.7V battery
- RTC module — DS3231 (HW-084)
- ESP32, 38-pin variant
- OLED 0.91" display
- Buzzer
- S8050 transistor

## 3. Functional Requirements (from original spec)

1. Fingerprint scan on the device marks a student present.
2. Lecturer login (username + password) + select today's lecture from a list.
3. Lecturer web app must support:
   - Full attendance report (all students) with a printable/exportable version
   - Search by student ID → view historical monthly data (name, student ID, total lectures held, lectures absent, per-day attendance, attendance % with 80% eligibility threshold)
   - "Update Attendance" — fix a student wrongly marked absent (sensor failure case)
   - "Update Attendance" — retroactively mark present after excuse approval (medical/sport/other)
   - Open to additional useful features suggested during development
4. SQLite database design covering students, lecturers, lectures, and attendance records.
5. A deployment/publishing strategy for the finished web app.

## 4. Environment / Tools Available

- VS Code
- GitHub account — repo: `https://github.com/didulah/University_mini_project`
- **Repo status (as of this log): empty — starting from scratch.**

## 5. Architecture Decisions Log

| Date | Decision | Reasoning |
|---|---|---|
| _(pending)_ | Flask + SQLite chosen for backend | Lightweight, matches original spec, easy to self-host for a mini project |
| _(pending)_ | ESP32 communicates with Flask over HTTP (WiFi) | Simplest integration; RTC module protects timestamp accuracy if WiFi drops |

_(Add a row every time a real architectural choice is made — e.g. auth method, DB schema changes, deployment platform choice.)_

## 6. Current Status

- Requirements gathered from the user (see Section 3).
- Repo confirmed empty — no code exists yet.
- `README.md` and this `PROJECT_LOG.md` created as the starting point.
- **Not yet started:** database schema, Flask app skeleton, ESP32 firmware, frontend templates.

## 7. Immediate Next Steps

1. Design the SQLite database schema (students, lecturers, lectures, attendance tables) — clarify relationships (e.g. does a lecture belong to a specific course + lecturer?).
2. Scaffold the Flask project structure (`app.py`, `models.py`, `templates/`, `static/`).
3. Build lecturer authentication (login).
4. Build the "select today's lecture" flow.
5. Build the attendance report view + student history lookup.
6. Build the "Update Attendance" correction flow.
7. Design and test ESP32 → Flask HTTP communication (can be mocked with Postman/curl before hardware is wired in).
8. Decide on deployment target (e.g. Render, Railway, PythonAnywhere) once the app is functional.

## 8. Open Questions (to resolve with the user)

- Does a "lecture" mean a specific course session (e.g. "CS201 - Mon 9am"), and how are lectures scheduled/created in the system — manually by an admin, or by the lecturer themselves?
- Should there be an "admin" role separate from "lecturer," or is lecturer the only role?
- How should student fingerprint templates be registered initially — a separate enrollment flow needed?

---

## Session History

### Session 1 — 2026-07-09
- Gathered full project requirements from user's mini_project.md description.
- Confirmed GitHub repo is empty.
- Created README.md and this PROJECT_LOG.md as the project's starting documentation.
- Proposed high-level flow: Hardware (ESP32 + sensor) → Flask backend (SQLite) → Lecturer web dashboard.