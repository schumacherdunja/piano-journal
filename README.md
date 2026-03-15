# 🎹 Piano Journal

*A mobile-first practice tracker for serious piano students — no account, no server, all data stays on your device.*

---

## What it is

Piano Journal is a two-file web app that lives on your phone's home screen. It helps you track practice sessions, manage repertoire, follow the Gebrian spaced repetition method, and monitor BPM progress over time. A companion Stats file gives deeper analysis.

Everything is stored in your browser's local storage — nothing is sent anywhere. Your data belongs to you.

---

## Getting started

### Installing on iPhone
1. Open the tracker URL in **Safari** (not Chrome)
2. Tap the Share button at the bottom of the screen
3. Tap **Add to Home Screen**
4. Tap Add — it appears as an app icon
5. Repeat for the Stats link if you want that as a separate icon

### Installing on Android
1. Open the URL in **Chrome**
2. Tap the three-dot menu → **Add to Home Screen**

### Installing on Mac / Windows
Open in Safari (Mac) or Chrome/Edge (Windows) and use the install option in the address bar or browser menu. It opens as a standalone window without browser chrome.

> **Note:** Both files must be accessed from the same web address for the Stats link to work. If you're using the GitHub Pages version, this is automatic.

---

## The two files

| File | Purpose |
|------|---------|
| `piano-tracker-v2.html` | Main tracker — pieces, practice, today view, session logging, Gebrian schedule, metronome, lesson log |
| `piano-stats.html` | Stats & analysis — BPM progress charts, time per section, monthly calendar, performance plans, insight system |

---

## Core concepts

### Pieces and sections

Add each piece you're working on, then break it into sections (e.g. Exposition, Development, Coda). Within each section you can add sub-sections for finer granularity. Every level can have:

- A **Stage** — Note Learning, Tempo Building, Memorisation, Interpretation, Mock Run-throughs, Peak & Recovery
- A **Difficulty** tag — Hard / Med / Easy — used by the insight system to calibrate what counts as a problem
- **Working BPM** — your current target tempo
- **Performance BPM** — the final target tempo

Tap a section header to expand it and edit these fields. Changes save automatically. Sections stay open while you edit — tap the header again to collapse.

### Logging a session

There are three ways to log:

1. **Practice rotation** — set up slots, run the timer, fill in BPMs at the end
2. **♪ Log button** on any section in the Pieces view
3. **Quick Log** on the Today tab — piece/section dropdown, one tap

Each log records date, duration, BPM range (start → end), note value, rating, and optional notes.

---

## The Practice tab

This is the action hub. Before starting:

- Add Gebrian due sections with **+ Add** (they appear at the top automatically)
- Add any other sections manually using the Add Slot panel
- Set minutes per slot and mode (Free or Clicking Up)
- Set rest between slots and number of rounds

Tap **Start Rotation** to begin. The clock counts down per slot with a progress ring. At the end, fill in BPMs for each slot and save.

### Clicking Up (within practice)

For slots set to Clicking Up mode, tap the *Clicking Up* button during the slot. This runs Gebrian's interleaved method: anchor BPM → target BPM → increment → repeat, with an optional overshoot. Progress through steps with Next.

### Clicking Up (standalone)

Access from the drawer menu → Clicking Up. Select a piece/section, set parameters, tap Begin Session. Log the result at the end.

---

## The Today tab

A read-only dashboard showing:

- Date, day name, practice streak, today's minutes, 7-day total
- 7-day dot calendar — green dot = practised, shows duration
- Gebrian sections due today with inline ♪ Log buttons
- Latest teacher focus reminder with lesson notes
- Recent BPM movements (last session vs previous)
- Quick Log dropdowns per piece for fast logging without going through Practice setup

---

## The Gebrian schedule (Spaced Rep)

Based on Carlo Gebrian's memorisation method. Each section follows a 108-day, 30-session schedule:

| Phase | Pattern |
|-------|---------|
| Phase 1 | 3 consecutive days |
| Phase 2 | Every other day × 3 (days 4, 6, 8) |
| Phase 3 | 7 days rest, then 3 consecutive |
| Phase 4 | 10 days rest, then 3 consecutive |
| Cycles 5–10 | 10 days rest + 3 days each |

To start a schedule: go to Spaced Rep in the drawer, select a piece and section, tap **Start Schedule Today**. Due sections appear automatically in Today and Practice.

Sessions are auto-ticked when you log a session for that section on a due date. Teacher focus sections are always shown in Practice regardless of schedule day. On Thursdays, teacher focus sections are injected into the Gebrian list even if not scheduled.

---

## Lesson Log

Record each lesson with a date, notes, and the sections your teacher focused on. The most recent lesson's focus sections appear throughout the app marked with a 🎓 badge, and they sort to the top of your practice setup.

---

## Stats & Insights (piano-stats.html)

Open from the History tab (Stats button) or directly via bookmark. Four tabs:

| Tab | What it shows |
|-----|--------------|
| History | Session list with BPM tags, time-per-section chart by day/week/month, section comparison |
| Insights | Attention Needed analysis, minutes-per-section chart, monthly calendar, time-per-piece breakdown with BPM progress |
| BPM | BPM progress chart per section over time, with target tempo dashed line |
| Performance | Performance readiness plans — stage timeline, mock run-through log, post-Gebrian maintenance schedule |

### Insight System

The Insights tab analyses each section you have BPM data for and flags issues. Signals are weighted by difficulty — a plateau on a Hard section is normal; the same plateau on an Easy section is a flag.

| Signal | What triggers it | Suggested action |
|--------|-----------------|-----------------|
| Slow progress | BPM gains below threshold for hours practised | Shorter, more focused slots |
| Stalled / Plateau | Last 3 sessions within ±2 BPM | Rest day or drop BPM 20% |
| Poor retention | Losing >5 BPM after gaps under 4 days | Practise more frequently |
| Retention risk | Losing >8 BPM between sessions | Check Gebrian schedule is active |
| Fatigue pattern | Longer sessions consistently rated worse | Keep slots under 15 minutes |
| Near target | At 95%+ of performance BPM | Focus on quality, not speed |

---

## Metronome

Access from the drawer. Tap once to start/stop. Tap the BPM display to type a value directly. Use + / − buttons to nudge. The beat indicator pulses on each beat. Supports quarter, eighth, half, dotted quarter, dotted eighth, and sixteenth note values.

---

## Performance Plans

In Stats → Performance, create a plan by selecting a piece and a performance date. The app calculates a stage timeline working backwards from the date:

Note Learning → Tempo Building → Memorisation → Interpretation → Mock Run-throughs → Peak & Recovery

Log mock run-throughs with a pressure rating and notes. After the performance, a maintenance schedule extends for 6 months with review checkpoints.

---

## Backup and restore

Go to the drawer → Backup. Export saves all your data as a JSON file. Import restores it. Do this regularly — if you clear your browser data, your practice history is gone.

> **Important:** Your data lives only on your device. It is not backed up to any server. Export regularly and keep the file somewhere safe.

---

## Data shared between files

The tracker and stats file share data via browser localStorage:

| Key | Contains |
|-----|---------|
| `pj2-pieces` | All pieces, sections, sub-sections, BPM targets, stages, difficulty tags |
| `pj2-sessions` | All practice sessions with BPM data, ratings, notes |
| `pj2-sr` | Gebrian schedules and tick history |
| `pj2-perf` | Performance plans and mock run logs |
| `pj2-lessons` | Lesson log entries and teacher focus sections |

Both files must be opened from the same origin (same website address) for this sharing to work.

---

## Tips

- Name sections with a leading number (e.g. *1 - Exposition*) — they sort numerically throughout the app
- Set a Performance BPM on each section — this unlocks the progress percentage in Stats
- Tag sections with difficulty before starting — the insight system is calibrated from day one
- The streak counter on Today only counts if you log at least one session that day
- Teacher focus sections always sort to the top of Practice setup regardless of the Gebrian schedule
- On Thursdays, teacher focus sections are automatically added to the practice list as a pre-lesson reminder

---

*Piano Journal — built for daily use on iOS, Android, Mac, and Windows*
