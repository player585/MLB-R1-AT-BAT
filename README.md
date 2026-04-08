# MLB R1 AT BAT

Live MLB scores, box scores, and pitch-by-pitch at-bat tracking for the Rabbit R1.

## Install on Your R1

Scan this QR code with your R1's camera (**Creations card → Create → Add via QR code**):

![MLB R1 AT BAT QR Code](qr-code.png)

**Or visit:** https://player585.github.io/MLB-R1-AT-BAT/

## Features

- **Scores** — Live game cards with inning-by-inning linescore
- **Box Score** — Full batting and pitching stats for any game
- **At Bat** — Live pitch-by-pitch at-bat tracker with:
  - Mini scoreboard (teams, score, inning)
  - Baseball diamond with runner positions
  - Ball/Strike/Out count dots
  - Mini strike zone with pitch locations
  - Batter vs Pitcher matchup with full season stats
  - Last pitch details (type, speed, spin rate)
  - Pitch sequence table for current at-bat
  - On-deck and in-the-hole batters
  - Recent plays with scoring highlights

## R1 Controls

| Input | Scores Tab | Box Score Tab | At Bat Tab |
|-------|-----------|---------------|------------|
| Scroll Wheel | Navigate games | Navigate rows | Navigate games / scroll detail |
| PTT Click | Select game → Box | Refresh box score | Select game → At Bat / refresh |
| Long Press | Cycle tabs | Cycle tabs | Cycle tabs |

## Data Source

All data from the free [MLB Stats API](https://statsapi.mlb.com). Auto-refreshes every 30s (scores) and 10s (at-bat detail).
