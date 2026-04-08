# MLB R1 AT BAT

**v2.2.0** — Live MLB scores, box scores, and pitch-by-pitch at-bat tracking built for the Rabbit R1 screen (240×282).

![MLB R1 AT BAT QR Code](qr-code.png)

---

## Install

1. Pick up your R1 and scroll to the **Creations** card
2. Tap **Create** → **Add via QR code**
3. Point the camera at the QR code above
4. Done — scroll to the bottom of your card stack to find it

**Live URL:** https://player585.github.io/MLB-R1-AT-BAT/

---

## Tabs

### Scores
Live game cards sorted by status (live → pre-game → final). Each card shows team abbreviations, full names, scores, and an inning-by-inning linescore grid with R/H/E totals. Live games display the current inning arrow (▲/▼) and out count. Scroll wheel moves focus between games. PTT click opens the selected game's box score.

### Box Score
Full batting and pitching stats for both teams. Batting table includes player name, position, AB, R, H, RBI, HR, BB, K, AVG, OBP, SLG. Pitching table includes IP, H, R, ER, BB, K, HR, PC-ST, ERA. Win/Loss/Save decisions shown at the bottom for final games. Horizontally scrollable for wide stat columns.

### At Bat
Live at-bat tracker with real-time data from the MLB live feed API. Refreshes every 10 seconds. Select a game from the card list, then view:

- **Scoreboard** — Away/home abbreviations, scores, current inning with top/bottom arrow
- **Diamond** — Base runners with occupied bases lit up
- **B/S/O Count** — Ball, strike, and out indicator dots
- **Strike Zone** — Mini zone with color-coded pitch location dots (red = strike, green = ball, yellow = in play)
- **Matchup** — Current batter vs pitcher with SEASON/GAME stat toggle
- **Last Pitch** — Pitch type, speed (mph), result, spin rate (rpm)
- **Pitch Sequence** — Table of every pitch in the current at-bat with pitch number, type code, mph, and result
- **On Deck / In the Hole** — Next two batters
- **Recent Plays** — Last 5 completed at-bats with event type and full description, scoring plays highlighted green

---

## Stat Toggle

The matchup panel has a **SEASON / GAME** pill toggle (default: SEASON).

| Mode | Batter Stats | Pitcher Stats |
|------|-------------|---------------|
| SEASON | AVG, OBP, SLG, HR, RBI, OPS | ERA, K, W-L, PC, ER, OUTS |
| GAME | AB, H, R, HR, RBI, BB | IP, K, H, ER, PC, OUTS |

OUTS is computed from innings pitched (e.g. 5.2 IP = 17 outs). The toggle persists across auto-refreshes.

---

## Fullscreen Modes

Tap any of these elements in the At Bat detail to expand it to fill the R1 screen. Tap the screen, press PTT, or press Escape to close.

| Tap Target | Fullscreen View |
|-----------|-----------------|
| Strike Zone | Large 180×200 zone with labeled pitch dots, color legend, pitch count |
| Diamond | Large base diamond with runner names at each base, inning + outs |
| B/S/O Count | Large numeric count (e.g. 1-2), oversized dot rows, inning indicator |
| Matchup Stats | Full batter/pitcher stats in tile grid with SEASON/GAME toggle |
| Last Pitch or Pitch Sequence | Last pitch header (type, speed, result, spin) + full sequence table with untruncated results |
| Play Description or Recent Plays | Current play highlighted, last 10 completed plays with inning indicators, scrollable |

The scroll wheel works inside all fullscreen overlays for scrollable content.

---

## R1 Hardware Controls

| Input | Scores | Box Score | At Bat List | At Bat Detail | Fullscreen |
|-------|--------|-----------|-------------|---------------|------------|
| **Scroll Wheel** | Move focus between game cards | Move focus between stat rows | Move focus between game cards | Scroll between sections | Scroll content |
| **PTT Click** | Select game → Box Score | Refresh box score | Select game → At Bat detail | Refresh live data | Close overlay |
| **Long Press** | Cycle to next tab | Cycle to next tab | Cycle to next tab | Cycle to next tab | — |
| **Screen Tap** | — | — | — | Expand tapped element | Close overlay |

### Keyboard Fallbacks (browser testing)

| Key | Action |
|-----|--------|
| Arrow Down/Up | Navigate focus or scroll |
| Arrow Left/Right | Cycle tabs |
| Enter/Space | Select game or refresh |
| Escape | Close fullscreen / go back |
| Backspace | Go back to game list |

---

## Data Source

All data from the free [MLB Stats API](https://statsapi.mlb.com/api/v1):

| Endpoint | Used For |
|----------|----------|
| `/schedule?sportId=1&date=YYYY-MM-DD&hydrate=linescore` | Scores tab game list |
| `/game/{pk}/boxscore` | Box Score tab |
| `/v1.1/game/{pk}/feed/live` | At Bat tab (live feed, plays, pitch events, boxscore) |

Auto-refresh intervals:
- Scores: every 30 seconds
- At Bat detail: every 10 seconds

---

## Tech

- Single `index.html` file, zero dependencies, zero build step
- Fonts: Inter (body) + JetBrains Mono (data/stats)
- Dark/light theme toggle
- Designed for 240px viewport with R1 hardware event listeners (`scrollUp`, `scrollDown`, `sideClick`, `longPressStart`, `longPressEnd`)
- Hosted free on GitHub Pages

---

## Version History

| Version | Changes |
|---------|---------|
| v2.2.0 | Pitch Sequence + Recent Plays fullscreen modes, scroll wheel in overlays |
| v2.1.0 | 4 fullscreen tap-to-expand modes (zone, diamond, count, stats) |
| v2.0.1 | Fix scroll in At Bat tab, section-based navigation |
| v2.0.0 | At Bat tab, SEASON/GAME toggle, ER + OUTS stats |
| v1.2.2 | Original Scores + Box Score tabs |
