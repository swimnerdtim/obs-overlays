# Barbie Castaway - Linear Story System

Johnny Castaway-style episodic storytelling for swim meet scoreboards.

## The Concept

Instead of random animations, Barbie's story unfolds in **real time**:
- Each "day" lasts 24 real hours
- Viewers return to see "What's Barbie doing today?"
- Story progression persists across sessions
- ~60 days total story arc

## Files

- **barbie-castaway.html** - Linear day player with scoreboard
- **day1-scene1-surfboard.png** - Surfboard washes in
- **day1-scene2-floating.png** - Barbie floats in face-down
- **day1-scene3-sitting-up.png** - Sits up, looks around
- **day1-scene4-shrug-okay.png** - Shrugs "...okay"

## How It Works

**First visit:**
- localStorage saves current timestamp as "story start"
- Day 1 sequence plays (20 seconds)
- Then idles with subtle bobbing animation

**Return visits (same day):**
- Loads same day
- Replays sequence or shows idle state

**Next day (24h later):**
- Automatically advances to Day 2
- New sequence plays
- Story continues

## Testing Commands

Open browser console and run:

```javascript
// Restart from Day 1
__barbie.reset()

// Jump to specific day (e.g., Day 5)
__barbie.skipToDay(5)

// Check current day
Math.floor((Date.now() - Number(localStorage.getItem('barbie_castaway_day_v1'))) / (24*60*60*1000)) + 1
```

## Day 1 Timeline

```
0:00 - Surfboard washes in from left
0:08 - Barbie floats in behind surfboard
0:15 - Sits up on beach
0:18 - Shrugs "...okay"
0:20+ - Idle bobbing animation
```

## Story Structure (Planned)

**Day 1:** Arrival (✅ DONE)
**Days 2-5:** Settling in (exploring, claiming lifeguard stand)
**Days 6-14:** Routine (fishing attempts, signal attempts, small failures)
**Days 15-20:** Hope (builds signal, boat passes, keeps trying)
**Days 21-40:** Living (storms, rebuilding, personalizing space)
**Day ~60:** Twist (city skyline visible all along)
**Day ~61:** Rescue (casual, no drama)
**Day ~62:** Reset (loop begins again)

## Cost per Day

- ~2-4 unique images per day
- $0.32 per image (Gemini 3 Pro)
- **~$0.64-$1.28 per day**
- Full 62-day story: **~$40-80 one-time cost**

## Expansion Strategy

### Phase 1: Days 1-5 ($6.40)
Build complete "arrival + settling in" arc
Test audience engagement

### Phase 2: Days 6-20 ($19.20)
Add routine + hope sequences
Establish story rhythm

### Phase 3: Days 21-62 ($53.76)
Complete full story with twist ending
Loop system activates

## Why This Works

**Traditional scoreboards:** Static or random animations
**Barbie Castaway:** Episodic content people return for

Coaches ask: "What day is Barbie on?"
Parents check: "Did she build the signal yet?"
Kids want: "The Barbie scoreboard, not the boring one!"

**Differentiator:** No other swim timing product has narrative content.

## Technical Notes

- Story state in localStorage (survives page reloads)
- Checks for day change every 60 seconds
- Each day function plays sequence, then idles
- Can skip days for testing
- Images load async (no blocking)

## Future Enhancements

- Multiple story arcs (Beach Day, Fashion Show, Road Trip)
- Seasonal variations (Christmas, Halloween themes)
- Random chance events (1% probability special scenes)
- Weather integration (storms on rainy days)
- Special animations for records broken

---

**Status:** Day 1 complete ($1.28)
**Next:** Days 2-5 ($1.60-$3.20)
