# Sports League Management System (SLMS)
## Skill Development Course (SDC) • Problem Statement #50 • Review 2 Submission

[![Vite](https://img.shields.io/badge/Vite-5.4-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![React](https://img.shields.io/badge/React-18.3-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![CSS Grid & Flexbox](https://img.shields.io/badge/CSS-Grid%20%26%20Flexbox-264DE4?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
[![LocalStorage](https://img.shields.io/badge/Storage-LocalStorage-10B981)](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
[![Milestone](https://img.shields.io/badge/Milestone-Review%202%20Full%20Implementation-emerald)](https://github.com)

---

## 📌 Project Overview (Review 2 Milestone)
The **Sports League Management System (SLMS)** is an end-to-end, multi-sport tournament and spectator portal built with React, CSS Grid, Flexbox, and HTML5 LocalStorage persistence.

This repository contains the **Review 2 (Phase 2 Full Implementation)** milestone, transitioning from the architectural wireframes of Review 1 to a **100% functional, live interactive system**.

---

## 🌟 Key Functional Features Implemented in Review 2

### 1. Admin Module & Tournament Management
- **Full CRUD for Multi-Sport Tournaments**: Create Football, Cricket, and Basketball leagues with season configurations, rules, and logos.
- **Franchise & Squad Roster Management**: Add clubs, specify home stadiums and head coaches, and manage athlete rosters (jersey numbers, tactical positions, goal statistics, and MVP ratings).
- **Fixture Scheduling & Status Workflow**: Schedule clashes across `UPCOMING`, `LIVE`, and `COMPLETED` operational states.

### 2. Real-Time Live Match Controller (The Core Engine)
- Referees toggle fixtures to `LIVE` with single-click precision.
- **Score Controller**: Real-time increment/decrement (+1 / -1 Goal/Point) for home and away teams.
- **Match Clock & Preset Controls**: Advance match minutes or toggle `HT` (Half-Time) and `FT` (Full-Time).
- **Incident Logger**: Publish timestamped match events (⚽ Goals, 🟨 Yellow Cards, 🎯 Wickets) which immediately stream to the fan portal.

### 3. Dynamic Standings Algorithm (`getStandingsForLeague`)
- Zero hardcoding of league ranks.
- Scans completed fixtures in LocalStorage, applies deterministic points rules (3 for Win, 1 for Draw, 0 for Loss), computes Goal Difference (GF - GA), and sorts teams dynamically on the fly.

### 4. Interactive 8-Column CSS Grid Stadium Ticketing
- **CSS Grid Seating Map**: Constructed using `grid-template-columns: repeat(8, 1fr)`.
- **Seat Tiers**: VIP, Premium, and General Admission with dynamic price calculation.
- **Digital QR Admission Passes**: Generates unique scannable alphanumeric QR passes (`SLMS-PASS-XXXXXX`) stored in `slms_tickets` and viewable under "My Passes".

---

## 🏛️ Full System Architecture (Review 2)

```
                            +-----------------------------------+
                            |          AppProvider              |
                            |  Central State & LocalStorage Sync|
                            +-----------------+-----------------+
                                              |
                     +------------------------+------------------------+
                     |                                                 |
         +-----------v-----------+                         +-----------v-----------+
         |     Admin Module      |                         |   User / Fan Module   |
         +-----------+-----------+                         +-----------+-----------+
                     |                                                 |
         +-----------+-----------+                         +-----------+-----------+
         | - LeagueManager       |                         | - UserDashboard       |
         | - TeamManager (Roster)|                         | - LiveScores Center   |
         | - FixtureManager      |                         | - Dynamic Standings   |
         | - LiveMatchControl    | <=== Reactive Sync ===> | - CSS Grid Ticketing  |
         | - TicketSales         |                         | - MyTickets & QR Pass |
         +-----------+-----------+                         +-----------+-----------+
                     |                                                 |
                     +------------------------+------------------------+
                                              |
                               +--------------v--------------+
                               |     Browser LocalStorage    |
                               | - slms_users                |
                               | - slms_leagues              |
                               | - slms_teams                |
                               | - slms_fixtures             |
                               | - slms_tickets              |
                               +-----------------------------+
```

---

## 👥 3-Person Team Roles & Defence Breakdown

| Presenter | Role | Review 2 Defense Responsibilities |
| :--- | :--- | :--- |
| **Presenter 1** | **Architecture & Auth Lead** | Review 1 recap, AppContext state synchronization, LocalStorage serialization, and route guards. |
| **Presenter 2** | **Admin Operations & Match Engine Lead** | Live demo of League/Team CRUD, scheduling fixtures, and the Real-time Live Match Controller (+1 Goal, Match Events). |
| **Presenter 3** | **Algorithms, CSS Grid & Ticketing Lead** | Dynamic points table sorting algorithm, 8-column CSS Grid seat booking, QR pass generation, and Chrome DevTools LocalStorage inspection. |

---

## 🔍 Evaluator Inspection & DevTools Verification

To verify that all project criteria are 100% satisfied:
1. Open the app in Chrome at `http://localhost:3000`.
2. Press **F12** to open Chrome DevTools.
3. Navigate to **Application ➔ Storage ➔ Local Storage ➔ `http://localhost:3000`**.
4. Observe all structured JSON keys:
   - `slms_users`
   - `slms_leagues`
   - `slms_teams`
   - `slms_fixtures`
   - `slms_tickets`
5. Test booking a ticket or updating a live score; refresh the browser to confirm zero data loss!

---

## 🚀 Running the Review 2 Project Locally

```bash
# 1. Clone the repository
git clone https://github.com/sriram-40219/sports-league-review-2.git

# 2. Navigate to project directory
cd sports-league-review-2

# 3. Install dependencies
npm install

# 4. Start the development server
npm run dev
```
