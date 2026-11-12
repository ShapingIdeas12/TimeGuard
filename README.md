# Robotics Office Attendance & Shift Tracker

A modern, frontend-only Employee Attendance & Shift Tracking web application built with **HTML5, CSS3 (Tailwind CSS), JavaScript, and React 18**.

Designed for **Chirag (Owner)** with pre-configured team members, **10:00 AM to 6:30 PM** shift, **2:00 PM to 2:45 PM** lunch break, **GPS Live Area Detection (Anti-Cheat, Zero Backend)**, **Office vs. Field selection popup**, **Protected CSV export with Owner ID & Password**, and **Automatic PDF Summary Report**.

---

## 👥 Organization & Team Structure

* **Executive Owner**: **Chirag** (Owner & Director — Has exclusive ID & Password to download CSV reports and manage geofencing)
* **Robotics Team (7 Staff Members)**:
  1. **Muskan** (EMP01 — Robotics Engineer)
  2. **Rupa** (EMP02 — Robotics Engineer)
  3. **Abhinav** (EMP03 — Robotics Engineer)
  4. **Abhijeet** (EMP04 — Robotics Engineer)
  5. **Rohit** (EMP05 — Robotics Engineer)
  6. **Niyati** (EMP06 — Creative Designer)
  7. **Milan** (EMP07 — Office Boy)

---

## 📍 Anti-Cheat Live GPS & Area Detection (Zero Backend Needed!)

### How It Works 100% in Browser:
1. **HTML5 Geolocation API**: When an employee clicks **"Office In"**, the browser queries their device's actual GPS / Wi-Fi hardware (`navigator.geolocation`).
2. **Instant Area Reverse-Geocoding**: The client-side browser immediately resolves the exact human-readable **Locality, Sector, City, and State** (e.g., *Sector 62, Noida* or *Okhla Industrial Area*).
3. **Office Distance Calculation (Haversine Formula)**: Compares the employee's current coordinates with the Office GPS coordinates:
   - Within 250m: Marked with `✅ Verified Inside Office`.
   - Outside: Flagged with `⚠️ X.X km from Office` so nobody can fake their attendance from home!
4. **Google Maps Link**: Generates a direct clickable link to verify on Google Maps.

---

## 🏢 Office vs. 🚗 Field Popup Selection

When an employee clicks **"Office In"**:
1. A popup modal opens with live GPS and Area already detected.
2. The employee chooses:
   - **🏢 Office** (Head Office / Robotics Lab)
   - **🚗 Field** (Client Site / Factory / Field Installation)
3. If **Field** is selected, they can optionally enter the client or site name.
4. The location and area are recorded and displayed on their card, daily log table, weekly summary, and exported in CSV and PDF.

---

## 👑 Owner Space: Chirag's Password-Protected CSV Export

* **Protected CSV**: Only **Chirag (Owner)** can download the raw attendance CSV data.
* **Credentials**:
  - **Default ID**: `chirag`
  - **Default Password**: `123`
* **Custom ID & Password Setup Space**:
  - Click **"Owner Space (Chirag)"** in the top navigation.
  - Go to the **"Set ID & Password"** tab to set a custom Username and secret Password anytime.
* **Office Geofence Setup**:
  - In Owner Space, go to the **"Office GPS"** tab.
  - Click **"Set Current GPS as Office Location"** to lock the office's exact coordinates.

---

## ⏰ Work Timings & Duration Logic

* **Official Work Shift**: `10:00 AM` to `06:30 PM` (8 Hours 30 Minutes span).
* **Official Lunch Break**: `02:00 PM` to `02:45 PM` (45 Minutes duration).
* **Target Net Work Time**: **7 Hours 45 Minutes** (465 minutes).
* **Total Duration Popup**: Appears immediately after each logout with exact net work hours, lunch duration, gross span, and compliance status.
* **Overall PDF Summary**: Automatically triggered with celebration confetti when all staff members have logged out!

---

## 🚀 How to Run in Terminal

Aapke computer par **Python 3.12** installed hai:

```powershell
python -m http.server 8000
```
Open in browser: 👉 **[http://localhost:8000](http://localhost:8000)**

Ya direct double click karein:
- **`run.bat`** ya **`index.html`**
