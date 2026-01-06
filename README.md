# 🐦 Bird Brain

**Bird Brain** is a browser-based web app that turns your eBird checklists into a game. Upload a CSV exported from eBird, and Bird Brain calculates a **score** based on rarity, seasonality, novelty, and count — rewarding rare birds, life birds, and out-of-season sightings.

Everything runs **entirely in the browser**. No accounts, no backend, no tracking.

---

## ✨ Features

- 📤 Upload eBird CSV checklists  
- 🧮 Intelligent scoring based on:
  - Rarity
  - Seasonality
  - Life birds & repeat sightings
  - Number of individuals observed
- 🗺️ Region-specific frequency data
- 📊 Detailed per-species score breakdown
- 🏆 Lifetime stats (total score, species, observations)
- 📋 Checklist history with expandable details
- 💾 Persistent storage using `localStorage`
- 📱 Mobile-friendly UI built with Tailwind CSS

---

## 🚀 Live Demo

If hosted via GitHub Pages:

```
https://<your-username>.github.io/bird-brain/
```

---

## 🧠 How Scoring Works

Each observation receives a score based on four components:

### 1️⃣ Base Score (Rarity)

Calculated using a logarithmic scale from regional frequency data:

```
Base Score = 100 × log10(1 / frequency)
```

Examples:
- 1% frequency → ~200 points  
- 10% frequency → ~100 points  
- 50% frequency → ~30 points  

---

### 2️⃣ Seasonal Bonus

Out-of-season birds earn a **1.5× multiplier**.

Applied when:

```
weekly frequency < 25% of annual peak frequency
```

---

### 3️⃣ Novelty Multiplier

Rewards diminish with repeated sightings:

| Sighting | Multiplier |
|--------|------------|
| First (Life Bird) | 1.0× |
| Second | 0.5× |
| Third+ | 0.25× |

---

### 4️⃣ Count Multiplier

Score is multiplied by the number of individuals observed:

```
Final Score = Base × Seasonal × Novelty × Count
```

---

## 🏷️ Rarity Tiers

| Tier | Frequency |
|---|---|
| **Mega Rare** | < 2% |
| **Rare** | < 10% |
| **Scarce** | < 20% |
| **Uncommon** | < 30% |
| **Common** | ≥ 30% |

---

## 📂 CSV Requirements

Bird Brain expects a CSV exported from **eBird** with the following columns:

| Column Name | Required |
|-----------|----------|
| `Species` | ✅ |
| `Observation Date` | ✅ |
| `Count` | ✅ |

Notes:
- A count of `X` is treated as `1`
- One checklist = one date
- Species names must match those used in the frequency dataset

---

## 🌍 Regional Data

Bird Brain uses precomputed weekly frequency data by region.

- Data is fetched from `frequency_data.json`
- Regions are derived automatically
- Users select the region when uploading a checklist
- Data is cached in `localStorage` for offline reuse

---

## 🛠️ Tech Stack

- HTML / Vanilla JavaScript
- Tailwind CSS (via CDN)
- No frameworks
- No backend
- No build step

---

## 📦 Local Development

Clone the repo:

```bash
git clone https://github.com/<your-username>/bird-brain.git
cd bird-brain
```

Open directly in your browser:

```bash
open index.html
```

Or serve locally:

```bash
python -m http.server
```

Then visit:

```
http://localhost:8000
```

---

## 💾 Data Storage

All data is stored locally in your browser:

- Checklist history
- Observation history
- Frequency data cache
- Selected regions

Clearing browser storage will reset the app.

---

## ⚠️ Limitations & Notes

- This is **not** an official eBird product
- Scores are for fun, not scientific comparison
- Species name mismatches may result in “No data” warnings
- Frequency accuracy depends on the underlying dataset

---

## 🧩 Future Ideas

- Leaderboards
- Per-year scoring
- Region auto-detection
- Species search & filters
- Sync across devices
- Custom scoring rules

---

## 📜 License

MIT License  
Feel free to fork, modify, and build on it.

---

## 🙌 Credits

- Frequency data derived from eBird observations
- UI built with Tailwind CSS
- Inspired by birding, gaming, and friendly competition
