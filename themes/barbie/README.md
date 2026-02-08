# Barbie Theme 💖

Hot pink paradise for your swim meet! Perfect for fun invitationals, charity meets, or just bringing maximum vibes to the pool deck.

## 🎨 Features

- Hot pink gradient backgrounds
- Full-screen digital scoreboard (no Cat6 cabling needed!)
- Live race timer with split times
- Dynamic place updates on touch
- Smooth animations
- High contrast for readability

## 📺 Full-Screen Scoreboard (Recommended!)

**Perfect for TVs around the pool deck** - eliminates Cat6 satellite cabling!

- Open `scoreboard.html` on any TV browser or cast it
- Shows 8 lanes with live results
- Race timer, event info, pool records
- Updates via BroadcastChannel API from Swimnerd Live
- **Test it**: `scoreboard_simulator.html`

### What It Shows:
- Event number and name
- Heat info (3 of 4)
- Lane (L) and Place (P) for each swimmer
- Split times (yellow) + Final times (white)
- Live race clock (top right)
- Lengths and pool record (bottom)

## 🎯 OBS Overlays (Alternative)

If you still want OBS overlays instead of full-screen:

- `event_header.html` - Event name and heat info
- `lane_results.html` - Individual lane times and placements
- **Width**: 1920px, **Height**: 1080px

## 📦 Files Included

- `scoreboard.html` - **Full-screen digital scoreboard** ⭐
- `scoreboard_simulator.html` - Test the scoreboard with demo data
- `event_header.html` - OBS overlay (event info)
- `lane_results.html` - OBS overlay (lane results)
- `simulator.html` - OBS overlay simulator
- `styles.css` - Barbie theme styling (shared)

## 🔧 Customization

All colors are defined in CSS variables. Easy to tweak the pink shades!

## 💡 Inspired By

The iconic Barbie aesthetic - playful, bold, and unapologetically pink! 🎀

---

**Built for Swimnerd Live** • Inspired by [lgbeno's work](https://github.com/lgbeno/swimnerd-templates)
