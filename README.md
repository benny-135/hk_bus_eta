# 🚌 香港巴士到站時間預報
## Hong Kong Bus ETA Display Board

A real-time bus arrival information display board for Hong Kong, designed for **desktop and tablet** use. Built as a single self-contained HTML file with zero dependencies beyond Google Fonts — just open in any modern browser.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Desktop%20%7C%20Tablet-green.svg)
![HTML](https://img.shields.io/badge/built%20with-HTML%20%2F%20CSS%20%2F%20Vanilla%20JS-orange.svg)
![Data](https://img.shields.io/badge/data-data.gov.hk%20Open%20API-red.svg)

---

## ✨ Features

### 🚍 Multi-Operator Support
| Operator | Chinese | Routes |
|---|---|---|
| Citybus | 城巴 (CTB) | Urban, cross-harbour, overnight |
| KMB | 九龍巴士 | Kowloon & NT urban |
| Long Win Bus | 龍運巴士 (LWB) | Airport & Lantau |
| NLB | 嶼巴 | Lantau Island |

### 🔄 Joint-Route ETA Merging
Routes operated by **both CTB and KMB** (e.g. 101, 112, 118, 307) are automatically detected. ETA data is fetched from **both operators simultaneously** and merged into a single chronological list — so you always see the next bus regardless of which company is operating at that moment.

### 🖥️ Dual Display Modes
- **Normal mode** — full UI with controls, status bar, route selector and drag-to-reorder
- **Fullscreen mode** — clean display board view, 5 rows filling the entire screen, no controls visible. Designed to be shown on a TV, monitor or large tablet screen in public or at home.

### 📺 Fullscreen Board Design
- Each row occupies exactly **1/5 of the viewport height**
- All text scales with `clamp()` to fill available space
- Route number, destination and ETA are all maximally large
- Remove button and drag handle are hidden
- Scrollable if more than 5 routes are configured

### 🎨 Visual Design
- Route numbers displayed in **Noto Sans HK** with colour coding by operator and route type:

| Colour | Meaning |
|---|---|
| 🟡 Golden Yellow | Citybus (CTB) routes |
| 🔴 Red | KMB routes |
| 🟠 Orange | Long Win Bus (LWB) routes |
| 🟢 Green | NLB routes |
| 🔵 Indigo | Night routes (N prefix) |
| 🔵 Blue | Express routes (X suffix) |
| 🟣 Purple | Special routes (R prefix) |

- Coloured **left accent bar** per row (gradient matching operator)
- Company **logos** displayed where loadable, with text fallback
- **Dual stop names** for joint routes (e.g. CTB name + KMB alternative name shown together)
- Alternating subtle row backgrounds replaced with uniform white + accent bar separation

### 🏷️ Smart ETA Display
- **Primary ETA** — large dominant number on the left
- **Secondary ETAs** — 2nd and 3rd upcoming buses stacked on the right
- Green blinking "到站" for imminent arrivals (≤ 0 min)
- Orange for soon (≤ 10 min), blue for normal
- Duplicate ETAs from joint operators automatically deduplicated (within 30-second window)

### 💾 Persistent Configuration
All selected stops and routes are saved to **browser localStorage** automatically. On next visit, previously configured stops are restored and ETA data is fetched immediately — no reconfiguration needed.

### 🖱️ Drag & Drop Reordering
In normal mode, rows can be **reordered by dragging the grip handle** (⠿) on the left. The dragged row floats with your cursor, a dashed placeholder shows the insertion point, and the new order is saved automatically. Touch-compatible.

### 🌙 Dark Mode
Full dark mode support. Follows system preference by default, with a manual toggle button. All colours, backgrounds and logos adapt accordingly.

### ⚡ Auto-Refresh
ETA data refreshes every **15 seconds** automatically. Only the ETA numbers are re-rendered on each refresh (not the entire row) — preventing flicker and preserving drag-reordered positions.

---

## 🚀 Getting Started

### Option 1 — Open directly
```bash
# Clone the repository
git clone https://github.com/yourusername/hk-bus-eta.git
cd hk-bus-eta

# Open in browser (no server needed)
open index.html
# or on Windows:
start index.html