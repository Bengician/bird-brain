# 🐦 Bird Brain

**Bird Brain** is a premium, browser-based web app that turns your eBird checklists into a competitive "Rank" score. Upload a CSV exported from eBird, and Bird Brain calculates a score based on rarity, seasonal scarcity, novelty bonuses, and flock multipliers.

Unlike the original version, this build features **Cloud Sync** via Supabase, allowing you to manage multiple birding profiles and keep your history safe.

---

## ✨ Features

- 📤 **eBird CSV Integration**: Seamlessly upload checklists exported directly from eBird.
- ☁️ **Cloud Profiles**: Create and switch between multiple user profiles (e.g., Birding Partners) with data synced to a Supabase backend.
- 🧮 **Advanced Scoring Engine (v3.2)**:
  - **Rarity Curve**: Exponential scoring based on regional frequency data.
  - **Seasonal Scarcity**: 1.5× bonus for out-of-season sightings.
  - **Novelty Bonuses**: Rewards for new discoveries (400% for Life Birds, 200% for second sightings).
  - **Flock Multipliers**: Linear multipliers for high-volume counts.
- 📊 **Dynamic Breakdowns**: Expand any species to see the exact math (Base × Season × Novelty × Count) behind its score.
- 📋 **Deep History**: Review previous checklists with full color-coded rarity badges and score breakdowns.
- 📱 **Modern UI**: A "glassmorphism" mobile-first design built with Tailwind CSS.

---

## 🧠 How Scoring Works (v3.2)

The algorithm is designed to feel rewarding. Instead of punishing repeat sightings, it provides massive "Booster" bonuses for new discoveries.

### 1️⃣ Base Score (The Rarity Curve)
Calculated using a logarithmic scale from regional frequency data:
`Base Score = 10 × log10(1 / frequency) × 10`

### 2️⃣ Seasonal Scarcity (1.5× Bonus)
Birds found outside their peak frequency window (less than 25% of their annual peak) receive a **1.5× multiplier**.

### 3️⃣ Novelty Bonuses
The more unique a bird is to your personal history, the higher the bonus:
- **Life Bird (1st Sighting):** 400% Score
- **2nd Sighting:** 200% Score
- **Repeats (3rd+):** 100% Score

### 4️⃣ Flock Multiplier (Linear)
The score for the observation is multiplied by the number of individuals recorded.
`Final Score = Base × Season × Novelty × Count`

---

## 🏷️ Rarity Tiers

| Tier | Frequency | Color Code |
|---|---|---|
| **Mega Rare** | < 2% | Purple |
| **Rare** | < 10% | Red |
| **Scarce** | < 20% | Orange |
| **Uncommon** | < 30% | Yellow |
| **Common** | ≥ 30% | Gray |



---

## 🛠️ Setup & Configuration

This app requires a **Supabase** project to handle user profiles and data persistence.

1. **Create a Supabase Project**: Head to [supabase.com](https://supabase.com).
2. **Database Tables**: Create the following tables:
   - `profiles`: Columns `username` (text, unique).
   - `checklist_data`: Columns `username` (text, primary key), `data` (jsonb), `history` (jsonb), `updated_at` (timestamp).
3. **Insert Credentials**: Update the following constants in the `index.html` file:
   ```javascript
   const SB_URL = 'YOUR_SUPABASE_URL_HERE';
   const SB_KEY = 'YOUR_SUPABASE_ANON_KEY_HERE';