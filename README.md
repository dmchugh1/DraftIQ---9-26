# DraftIQ

A personal fantasy football draft assistant: live recommendations, tiers,
scarcity/urgency alerts, targets/avoids, and draft-board tracking, run
entirely on your own machine.

## Setup

1. Install Python 3.10+.
2. From this folder, install dependencies:
   ```
   pip install -r requirements.txt
   ```

## Running it

```
python app.py
```

Then open **http://127.0.0.1:5000** in your browser. Stop the server with
`Ctrl+C`.

By default it serves on port 5000. To use a different port:

```
PORT=8000 python app.py
```

## Loading your rankings

`uploads/sample_players.csv` is a **format template only** — placeholder
names ("QB Example 1", etc.), not real players or real rankings. It exists
so the app has something to show you immediately and so you can see the
exact column layout expected.

Before you draft, replace it with a real rankings export (from
FantasyPros, ESPN, your own spreadsheet, etc.) using the **Setup** tab's
upload box. Required columns:

| column | notes |
|---|---|
| `name` (or `player`/`player_name`) | player's name |
| `position` (or `pos`) | QB/RB/WR/TE/DEF/K, etc. |
| `rank` | overall rank — required, rows without one are dropped |
| `adp` | average draft position — optional but recommended |
| `team` | optional |

## Notes on this being a single-user tool

This app keeps one draft's worth of state in memory (no accounts, no
database). It's built for one person running it locally for their own
draft — not for hosting somewhere multiple people would use it
simultaneously. If you want to share it with your league or turn it into
something multiple people use at once, that needs a different
architecture (per-user sessions, a real database, etc.) — ask if you want
help scoping that out.

## Data

Nothing here leaves your machine — no accounts, no analytics, no external
calls. Your uploaded CSV and draft progress live only in this folder and
in the running process's memory.
