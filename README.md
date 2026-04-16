# Gym Journal – Java Desktop Workout Application

A full-featured Java Swing desktop application for tracking workouts,
built to run in Eclipse with no external dependencies.

---

## Features

| Feature | Details |
|---|---|
| **Auth** | Register & login via username or email + password |
| **Profile** | Name, username, email, height, weight, BMI calculator |
| **Journal** | Create/edit/delete workout plans per day |
| **Exercises** | Name, plate weight (lbs/side), sets, reps, RPE 1–10 |
| **Calendar** | Monthly view with clickable workout chips per day |
| **Marketplace** | Browse, search, sort, like, download & comment on public workouts |
| **Persistence** | All data saved locally in `~/.workoutjournal/` using Java serialization |

---

## Eclipse Setup (Step by Step)

### Option A – Import Existing Project (Recommended)

1. Open **Eclipse IDE for Java Developers** (Java 11+ required)
2. Go to **File → Import…**
3. Choose **General → Existing Projects into Workspace** → Click Next
4. Click **Browse…** and select the `WorkoutJournal` folder
5. Make sure `WorkoutJournal` is checked → Click **Finish**
6. In the Project Explorer, expand **src → com.workoutjournal**
7. Right-click `Main.java` → **Run As → Java Application**

### Option B – Manual Setup

1. In Eclipse: **File → New → Java Project**
   - Project name: `WorkoutJournal`
   - Uncheck "Use default location" and point to this folder
   - Java version: 11 or higher
2. Click **Finish**
3. Right-click `Main.java` → **Run As → Java Application**

---

## Project Structure

```
WorkoutJournal/
├── .classpath
├── .project
├── README.md
└── src/
    └── com/workoutjournal/
        ├── Main.java                        ← Entry point
        ├── model/
        │   ├── User.java                    ← User data model
        │   ├── Exercise.java                ← Single exercise entry
        │   ├── WorkoutPlan.java             ← Workout plan (collection of exercises)
        │   └── Comment.java                 ← Marketplace comment
        ├── data/
        │   └── DataManager.java             ← Singleton persistence layer
        └── ui/
            ├── UIConstants.java             ← Shared colors, fonts, component factories
            ├── MainFrame.java               ← Root JFrame with CardLayout
            ├── LoginPanel.java              ← Login screen
            ├── RegisterPanel.java           ← Registration screen
            ├── DashboardPanel.java          ← Main tabbed interface
            ├── ProfilePanel.java            ← Edit profile, password, body stats
            ├── CalendarPanel.java           ← Monthly calendar view
            ├── WorkoutJournalPanel.java     ← Manage personal workouts
            ├── AddWorkoutDialog.java        ← Create/edit workout + exercises
            ├── MarketplacePanel.java        ← Browse public workouts
            └── WorkoutDetailDialog.java     ← View workout, exercises, comments
```

---

## Data Storage

All data is persisted automatically using Java object serialization:

- **Location:** `~/.workoutjournal/` (your user home directory)
- **Files:** `users.dat`, `workouts.dat`
- No database, no external libraries required.

---

## Java Requirements

- **Java 11 or higher** (uses `java.time.LocalDate`, etc.)
- **No external dependencies** – pure Java SE + Swing

---

## Quick Start Guide

1. Launch the app → click **Register**
2. Fill in your details and create an account
3. You'll land on the **Journal** tab – click **+ New Workout**
4. Enter a plan name, date, and add exercises with weight/sets/reps/RPE
5. Toggle **"Share publicly"** to post it to the **Marketplace**
6. Switch to **Calendar** to see workouts plotted on the monthly grid
7. Visit **Marketplace** to browse others' workouts, like ❤ and comment 💬
8. Click **⬇ Download** to copy a marketplace workout to your journal

---

## Color Theme

Gym Journal uses a dark, high-contrast gym aesthetic:
- **Background:** Near-black (`#0F0F14`)
- **Cards:** Dark navy (`#1A1A24`)
- **Accent:** Fiery orange-red (`#FF5032`)
- **Success:** Green (`#32C878`)
- **Warning:** Amber (`#FFBE32`)
