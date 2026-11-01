# SWING DECISION PLUS

A pitch-by-pitch, count-by-count hitting approach tracker. Coaches log every pitch of every at-bat (location, pitch type, what the hitter did, and the pitcher), and the app shows each hitter's swing decisions by count, chase and whiff rates, QAB chart stats, and tendencies for every pitcher faced.

## Features
- Separate seasons, each with its own roster, plus archiving
- Pitch logging on a strike zone (catcher view) with pitch type and outcome
- Good/bad swing decision grading, plus chase, zone swing and whiff rates by count
- Full QAB chart stats: QAB, PA, QAB%, H, 1B/2B/3B/HR, TB, AVG, OBP, SLG, OPS, BB/HBP, K, RBI, SAC, SF, HH, AB, HH%
- Season stats table you can sort by any column
- Pitcher reports: pitch mix by count, first-pitch strikes, tendencies
- CSV export of season stats and every pitch
- Coaches edit, players view

## Running it
The app is a single `index.html` file. Right now it stores its roster and at-bats with the Claude artifact data service (`window.claude.use('db')`), so it saves data only when opened as a Claude artifact. If you open it anywhere else, such as GitHub Pages, it shows the logo and a "sign in" message.

To run it as a standalone app, swap that data layer for a backend like Firebase or Supabase. The `db.collection(...)` calls are written in Firestore style, so Firebase is the easiest fit.

## Data collections
- `seasons`: name, at, archived
- `players`: name, season, st (imported totals)
- `abs`: season, pid, at, end, pitcher, rbi, sac, sf, qab, pitches[]
