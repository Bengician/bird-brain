# 🐦 Birding Scorer

A mobile-friendly web app for scoring your eBird checklists based on species rarity, seasonality, and life birds.

## Features

- 📊 Score checklists based on bird frequency data
- 🎨 Color-coded rarity tiers (Mega Rare, Rare, Scarce, Uncommon, Common)
- 🎬 Animated scoring with real-time tallying
- 📱 Mobile-optimized interface
- 💾 Automatic data persistence in browser
- 📍 Multi-region support
- 📈 Track your birding statistics over time

## Quick Start

### Option 1: Use Online (Easiest)

1. Visit: `https://YOUR-USERNAME.github.io/birding-scorer/`
2. Upload your frequency data CSV (one-time setup)
3. Start scoring checklists!

### Option 2: Download and Use Locally

1. Download `index.html` from this repository
2. Open it in your web browser (Chrome, Safari, Firefox, etc.)
3. Upload your frequency data CSV
4. Start scoring!

### Option 3: Add to Phone Home Screen

**iOS (Safari):**
1. Open the app in Safari
2. Tap the Share button
3. Tap "Add to Home Screen"
4. Name it "Birding Scorer"

**Android (Chrome):**
1. Open the app in Chrome
2. Tap the menu (3 dots)
3. Tap "Add to Home screen"

## Setting Up Frequency Data

### Required CSV Format

Your frequency data CSV must have these columns:

| Column | Description | Example |
|--------|-------------|---------|
| Species | eBird species code | `NORCAD` |
| Week | Week of year (1-52) | `22` |
| Frequency | Observation frequency (0-1) | `0.045` |
| Peak Frequency | Annual max frequency | `0.089` |
| Region | eBird region code | `CA-BC` |

### Example Row:
```csv
Species,Week,Frequency,Peak Frequency,Region
NORCAD,22,0.045,0.089,CA-BC
AMCRO,22,0.234,0.267,CA-BC
```

### Getting Frequency Data

You can obtain frequency data from:
1. **eBird Status & Trends** - Download regional frequency data
2. **eBird Basic Dataset** - Calculate frequencies from historical data
3. Contact the repository owner for sample data

### First-Time Setup:

1. Open the app
2. Click "Upload your frequency data CSV"
3. Select your frequency CSV file
4. Done! The app will remember this data

## Using the App

### Scoring a Checklist

1. Download your checklist from eBird as CSV
2. Tap "Score Checklist" button
3. Select the CSV file
4. Choose your region from the list
5. Watch the animated scoring!

### Understanding Scores

**Base Score:** Calculated from rarity using logarithmic scale
- Rarer birds = higher scores
- 1% frequency bird ≈ 20 points
- 10% frequency bird ≈ 10 points

**Seasonal Bonus:** 1.5x multiplier for out-of-season birds
- Applied when frequency < 25% of annual peak

**Novelty Multiplier:**
- First sighting: 1.0x (full points)
- Second sighting: 0.5x (half points)  
- Third+ sighting: 0.25x (quarter points)

**Count Multiplier:** Score × number of individuals seen

### Rarity Tiers

- 🟣 **Mega Rare**: < 2% frequency
- 🔴 **Rare**: < 10% frequency
- 🟠 **Scarce**: < 20% frequency
- 🟡 **Uncommon**: < 30% frequency
- ⚪ **Common**: ≥ 30% frequency

## Data Storage

- All data stored locally in your browser
- Works offline after initial setup
- No data sent to external servers
- Data persists between sessions
- Use "Reset All Data" to clear history

## Troubleshooting

**CSV won't upload on mobile:**
- Try using Chrome or Safari
- Make sure file has .csv extension
- Try the alternative "tap here to select CSV file" button

**Frequency data not loading:**
- Check CSV has all required columns
- Ensure column names match exactly (case-insensitive)
- Verify no special characters in data

**Scores showing as 0:**
- Verify species codes match between checklist and frequency data
- Check that the region exists in your frequency data
- Ensure week numbers are valid (1-52)

## Technical Details

- Pure HTML/CSS/JavaScript (no build process needed)
- Uses localStorage for data persistence
- Tailwind CSS for styling
- Mobile-first responsive design

## Contributing

Issues and pull requests welcome! Please feel free to:
- Report bugs
- Suggest features
- Improve documentation
- Share frequency data sources

## License

MIT License - feel free to use and modify

## Credits

Created for birders who want to gamify their eBird checklists and track rare finds.
```

**3. `.gitignore`**:
```
# Ignore any local test data
*.csv
test_data/

# OS files
.DS_Store
Thumbs.db
```

**4. `LICENSE`** (MIT License):
```
MIT License

Copyright (c) 2026 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
