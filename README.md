# Fingerprint-Based Student Attendance Management System

A hybrid **embedded system + web application** project that replaces manual attendance marking (paper registers, roll calls) with a fingerprint sensor connected to a web dashboard for lecturers.

## Problem Statement

Traditional attendance methods suffer from:
- **Proxy attendance** (buddy punching) — one student marking another present
- **Time consumption** — lecture time lost to manual roll calls
- **Manual errors** — mistakes during data entry
- **No centralized record** — no easy way to analyze historical attendance, late arrivals, absentees, or check per-student eligibility (attendance % threshold)

## Hardware Components

| Component | Purpose |
|---|---|
| Fingerprint sensor — R307S | Captures and verifies student fingerprints |
| ESP32 (38-pin) | Main microcontroller — reads sensor, connects to WiFi, sends data to backend |
| RTC module — DS3231 (HW-084) | Accurate timestamping, even without WiFi/power |
| OLED 0.91" display | On-device feedback (e.g. "Attendance Marked") |
| Buzzer | Audio confirmation on successful scan |
| S8050 transistor | Buzzer/peripheral driver circuit |
| Charging module + 3.7V battery | Portable power supply |

## Software Stack

- **Backend:** Flask (Python)
- **Database:** SQLite
- **Frontend:** Flask templates (Jinja2) + HTML/CSS/JS (to be finalized)
- **Firmware:** Arduino/ESP-IDF (C/C++) for ESP32

## Core Features

1. Students mark attendance by placing a finger on the sensor connected to the ESP32 device.
2. Lecturers log in (username/password) and select the specific lecture session taking place that day.
3. Lecturer dashboard supports:
   - Viewing and printing attendance reports for all students in a session
   - Looking up a student by ID number to view historical attendance for a given month — including total lectures held, lectures absent, attendance %, and eligibility status (≥80% = eligible)
   - **Update Attendance** — correcting a student marked absent due to a failed fingerprint scan
   - **Update Attendance** — retroactively marking a student present after they submit a valid excuse (medical/sport/other)
4. Centralized SQLite database storing students, lecturers, lectures, and attendance records.
5. Deployment plan for making the web app publicly accessible.

## Project Structure

```
University_mini_project/
├── README.md
├── PROJECT_LOG.md
├── app.py                 # Flask entry point
├── models.py               # Database models
├── requirements.txt
├── firmware/                # ESP32 code (Arduino/PlatformIO)
├── templates/                # HTML templates
├── static/                    # CSS/JS assets
└── instance/
    └── attendance.db      # SQLite database (gitignored in production)
```

## Status

🚧 **In active development.** See `PROJECT_LOG.md` for current progress, architecture decisions, and next steps.

## Setup

_(To be added once the initial Flask app skeleton is created.)_