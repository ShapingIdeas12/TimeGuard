# Robotics Office Attendance & Shift Tracker

A modern, frontend-only Employee Attendance & Shift Tracking web application built with **HTML5, CSS3 (Tailwind CSS), JavaScript, and React 18**.

Designed for **Chirag (Owner)** with flexible morning school shift arrivals (**8:30 AM, 9:00 AM, 9:30 AM**), dynamic check-out (**5:30 PM**), **Separate Overtime (OT) Extra Hours Calculation**, **GPS Live Area Detection (Anti-Cheat, Zero Backend)**, **Office vs. Field selection popup**, **Protected CSV export with Owner ID & Password**, and **Automatic PDF Summary Report**.

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

## 🎒 Early School Shifts & Dynamic Check-Out (8:30 / 9:00 AM ➔ 5:30 PM)

* **Morning Arrival Flexibility**:
  - Employees can check in anytime in the morning (e.g., **8:30 AM**, **9:00 AM**, **9:30 AM**, or standard **10:00 AM**).
  - In the "Office In" popup, quick 1-click arrival buttons allow selecting the exact arrival time.
* **Dynamic Check-Out Time & Included 2:00 PM - 2:45 PM Break**:
  - Original timing: **10:00 AM to 6:30 PM** (Total span = 8.5 hours).
  - Har shift me **2:00 PM to 2:45 PM (45-minute lunch break)** already included hai:
    $$\text{Gross Time } (8\text{h } 30\text{m}) - \text{Break } (45\text{m}) = \mathbf{7\text{ Hours } 45\text{ Minutes Net Work Target}}$$
  - Chahe employee manually "Lunch Out / Lunch In" punch kare ya bhool jaye, 2:00 PM – 2:45 PM window pass hone par **45-minute break automatically apply** ho jata hai!
  - Early school shifts bhi isi 7h 45m target aur 45m break ko follow karti hain:
    - **In at 8:30 AM** ➔ Target Out: **5:00 PM** (Target 7h 45m; out at 5:30 gives +30m OT)
    - **In at 9:00 AM** ➔ Target Out: **5:30 PM** (Exact 7h 45m net work)
    - **In at 9:30 AM** ➔ Target Out: **6:00 PM** (Exact 7h 45m net work)
    - **In at 10:00 AM** ➔ Target Out: **6:30 PM** (Exact 7h 45m net work)
  - Leaving at 5:30 PM after a 9:00 AM arrival is counted as **✅ Full Shift Completed On Time** (NOT early leave).

---

## ⭐ Separate Overtime (OT / Extra Hours) Calculation

* Any work done beyond the daily shift target (7 Hours 45 Minutes net work) is **automatically calculated as separate Overtime (OT)**.
* **Examples**:
  - **In at 9:00 AM, Out at 5:30 PM** (with 45m lunch): Net Work = `7h 45m` &bull; Overtime = `0m` &bull; Status: `Standard Met (Exact)`.
  - **In at 9:00 AM, Out at 6:30 PM** (1 hour late): Net Work = `8h 45m` &bull; **⭐ Overtime = `+1 hr 00 min`**.
  - **In at 8:30 AM, Out at 5:30 PM**: Net Work = `8h 15m` &bull; **⭐ Overtime = `+30 mins`**.
* **Overtime is separated and highlighted everywhere**:
  - **Employee Card**: Glowing gold badge with `⭐ Overtime (OT): +Xh Ym`.
  - **KPI Dashboard Banner**: Dedicated 5th KPI card: `⭐ Total Team Overtime Today: X hrs Y mins`.
  - **Logout Popup**: Gold banner showing exact Extra Overtime hours worked.
  - **Daily Log Table**: Separate column for `⭐ Overtime (OT)` and `Short Hours`.
  - **Weekly Timesheet**: Dedicated column for `⭐ Weekly Overtime (OT)` accumulated by each employee.
  - **PDF Summary Report**: Total overtime logged in header + separate table column.
  - **Owner CSV Export**: Dedicated `Overtime Hours (OT)` and `Short Hours` columns.

---

## 🚪 Flexible Check-Out ("Jo Time Pe Jaana Chahe")

Koi bhi employee **kisi bhi time par nikal sakta hai** (koi hard restriction ya lock nahi hai):
1. **Smart Departure Modal**: Jab koi **"Office Out"** button click karega, turant smart departure popup open hota hai.
2. **Quick Departure Times**:
   - `[ 🕒 Now (Live Time) ]`
   - `[ 04:30 PM ]` (Early finish)
   - `[ 05:00 PM ]` (Target for 8:30 AM arrival)
   - `[ 05:30 PM ]` (School shift target for 9:00 AM arrival)
   - `[ 06:00 PM ]`
   - `[ 06:30 PM ]` (Standard evening target for 10:00 AM arrival)
   - `[ 07:00 PM ]` (Evening Overtime)
   - **Exact Out Time Input**: Minute-level custom time (e.g., `05:15 PM`, `05:45 PM`).
3. **Instant Live Preview**:
   - Out time select karte hi modal ke andar turant live calculation dikhta hai:
     - Net working duration
     - Golden Overtime badge (agar 7h 45m se zyada kaam hua)
     - Short hours warning (agar jaldi nikle)
     - Ya green "Target Met Perfectly" badge!
4. **Accidental Click Protection**: Cancel button se bina logout kiye wapas ja sakte hain.

---

## 📍 Anti-Cheat Live GPS & Area Detection (Zero Backend Needed!)

1. **HTML5 Geolocation API**: Reads actual device hardware GPS & Wi-Fi positioning (`navigator.geolocation`).
2. **Instant Area Reverse-Geocoding**: Resolves human-readable area/city name (e.g. *Sector 62, Noida* or *Okhla Industrial Area*).
3. **Office Distance Calculation (Haversine Formula)**:
   - Within 250m: Marked with `✅ Verified Inside Office`.
   - Outside: Flagged with `⚠️ X.X km from Office` so nobody can fake their attendance from home!
4. **Google Maps Link**: Clickable link to view exact location on Google Maps.

---

## 🏢 Office vs. 🚗 Field Popup Selection

When an employee clicks **"Office In"**:
1. Choose arrival time (8:30 AM, 9:00 AM, 9:30 AM, 10:00 AM, or live time).
2. Choose **🏢 Office** (Robotics Lab) or **🚗 Field** (School Site / Client Workshop).
3. If Field is selected, enter school or client name.
4. Live GPS Area is verified automatically.

---

## 👑 Owner Space: Chirag's Password-Protected CSV Export

* **Protected CSV**: Only **Chirag (Owner)** can download the raw attendance & overtime CSV data.
* **Credentials**:
  - **Default ID**: `chirag`
  - **Default Password**: `123`
* **Custom ID & Password Setup Space**:
  - Click **"Owner Space (Chirag)"** in the top navigation.
  - Set custom Username and secret Password anytime.
* **Office Geofence Setup**:
  - In Owner Space, click **"Set Current GPS as Office Location"** to lock the office coordinates.

---

## 🚀 How to Run in Terminal

Terminal (PowerShell ya CMD) me chalayein:
```powershell
python -m http.server 8000
```
Browser me open karein: 👉 **[http://localhost:8000](http://localhost:8000)**

*(Ya direct `run.bat` ya `index.html` par double click karein!)*
