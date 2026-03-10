# MEMORY.md - Long-Term Memory

## Quick Reference

**Current active projects:**
1. Night Swim Podcast Website (DEPLOYED, LIVE) ⭐ **NEW** (Mar 10, 2026)
2. Twitter Bot for @SwimNerds - ENHANCED (automated, live, FIXED) ⭐ **FIXED** (Mar 10, 2026)
3. Google Drive → YouTube Uploader (ready to deploy) ⭐ **NEW**
4. Tiny Pace Clock Drip Campaign (conversion initiative) ⭐ **NEW**
5. Training App Page Overhaul (conversion initiative) ⭐ **NEW**
6. Swimnerd Calculator with 15m Chunks (complete, ready for deployment) ⭐ **ENHANCED**
7. LIAC Scoreboard Theme (deployed, live)
8. Barbie Theme for Swimnerd Live (complete)

**Key file locations:**
- Night Swim website: `/Users/tim/.openclaw/workspace/nightswimpod/`
- Twitter bot: `/Users/tim/.openclaw/workspace/swimnerd/twitter-bot/`
- YouTube automation: `/Users/tim/.openclaw/workspace/swimnerd/gdrive_to_youtube.py`
- Automation docs: `/Users/tim/.openclaw/workspace/swimnerd/AUTOMATION_DOCS.md`
- Themes: `https://swimnerdtim.github.io/obs-overlays/themes/`

---

## Active Projects

### 🌐 Night Swim Podcast Website - DEPLOYED (Mar 10, 2026) ⭐ **NEW**
**Status:** ✅ Live at https://swimnerdtim.github.io/nightswimpod/

**What it is:**
Complete website rebuild for Night Swim Podcast. Migrated from Lovable.dev to self-hosted GitHub Pages.

**Built in ~45 minutes:**
- React + Vite static site
- 3 pages: Home, Episodes, About
- Responsive design (mobile, tablet, desktop)
- Dark navy theme + bright green accents
- Auto-deploy on git push

**Pages:**
1. **Home** - Latest episode embed, highlights grid, about section, subscribe CTAs
2. **Episodes** - Filterable grid (All, Hot Takes, Interviews, Events, Training, News)
3. **About** - Mission, host bios (Dax Hill & Elvis Burrows), stats

**Features:**
- YouTube video embeds
- Episode filtering
- Platform links (YouTube, Spotify, Apple)
- Email signup form (UI only, needs backend)
- Social media icons
- GitHub Actions auto-deployment

**URLs:**
- Live site: https://swimnerdtim.github.io/nightswimpod/
- Custom domain: nightswimpod.com (needs DNS pointing)
- GitHub repo: https://github.com/swimnerdtim/nightswimpod

**Key files:**
- Episodes data: `src/data/episodes.json`
- Deploy docs: `DEPLOY_STATUS.md`
- Workflow: `.github/workflows/deploy.yml`

**How to update episodes:**
1. Edit `src/data/episodes.json`
2. Commit + push
3. Site auto-deploys in ~2 minutes

**Next steps:**
- Point DNS (A records to GitHub Pages IPs)
- Add episode auto-importer (Jay → YouTube → site update)
- Email signup backend integration
- SEO optimization

**Built:** 2026-03-10 while Nate was at swim practice

---

### 📱 Twitter Bot for @SwimNerds - ENHANCED (Feb 2026) ⭐ **UPGRADED**
**Status:** ✅ Enhanced version ready, cron update pending

**What it does:**
1. **News commentary** - Manual review: I generate 5 draft tweets from swimming news, send to Nate via WhatsApp, he picks which to post
2. **Night Swim auto-poster (ENHANCED)** - Fully automated with transcript extraction:
   - Checks YouTube at 1pm & 6pm EST
   - Extracts video transcript automatically
   - Posts main tweet with title + transcript excerpt (150 chars) + link
   - Auto-replies with full episode link (if clip)
   - **SEO benefit:** More text = better Twitter/X algorithm discoverability

**Key files:**
- Enhanced poster: `/Users/tim/.openclaw/workspace/swimnerd/twitter-bot/post_nightswim_enhanced.py` ⭐
- Legacy poster: `/Users/tim/.openclaw/workspace/swimnerd/twitter-bot/post_nightswim.py`
- Twitter creds: `twitter-bot/twitter_credentials.json`
- Current cron: `0 13,18 * * * ...post_nightswim.py` (needs update)

**New features:**
- ✅ Transcript extraction from YouTube captions
- ✅ Automatic reply threading with full episode links
- ✅ Duration detection (clip vs full episode)
- ✅ Better engagement with more text content

**How to use:**
- News drafts: Say "generate drafts" → I send 5 options via WhatsApp → Nate replies which to post
- Night Swim: Fully automated, no action needed

**Next step:** Update cron job to use `post_nightswim_enhanced.py`

**Test posts (successful):**
- Sam Williamson 27.08 comeback
- Nicholas Santos at 45

**Important filters:**
- ❌ Skip SwimSwam (they don't like us)
- ❌ Skip college commits/recruiting
- ✅ Post Olympics, world records, pro swimmers, comebacks

**Daily logs:** Check `memory/YYYY-MM-DD.md` for detailed session notes

---

### 🎬 Google Drive → YouTube Uploader (Feb 2026) ⭐ **NEW**
**Status:** ✅ Built and tested, ready to deploy

**What it does:**
Fully automated video uploading from Night Swim Google Drive folder to YouTube:
- Downloads videos from Google Drive
- Generates rich metadata (title, description, tags)
- Uploads to YouTube with progress tracking
- Prevents duplicates
- Supports scheduling (future publish times)
- Automatic temp file cleanup

**Key file:**
`/Users/tim/.openclaw/workspace/swimnerd/gdrive_to_youtube.py`

**Google Drive folder:**
- Folder ID: `1axXdzlLKF4paXlQtrXLGDOWOu0e9oYRJ`
- Current videos: 6 ready to upload (CHAMPS SEASON, AUSTIN APPLEBEE, SWIMMER NUTRITION, SAFE SPORT, KAATSU, +1 more)

**Test command:**
```bash
cd /Users/tim/.openclaw/workspace/swimnerd
python3 gdrive_to_youtube.py --test
```

**Upload command:**
```bash
python3 gdrive_to_youtube.py --limit 3 --privacy public
```

**Features:**
- Upload limits (prevent mass uploads)
- Privacy controls (public/private/unlisted)
- Scheduling support (--schedule-hours N)
- Duplicate tracking (uploaded_videos.json)
- Progress bars (download + upload %)
- Automatic cleanup

**Next step:** Run first batch when Nate is ready

**Complete docs:** `/Users/tim/.openclaw/workspace/swimnerd/AUTOMATION_DOCS.md`

---

### 💰 Conversion Initiatives - Swimnerd AI Growth (Feb-Mar 2026) ⭐ **NEW**
**Status:** Strategy approved, pending execution

**Goal:** Convert existing customers and organic traffic to Swimnerd AI subscriptions (recurring SaaS revenue)

#### Project #1: Tiny Pace Clock Drip Campaign

**Strategy:** Target customers who buy hardware (tiny pace clocks) and convert them to software subscribers

**7-10 day email sequence:**
1. **Day 1:** Order confirmation + soft AI intro
2. **Day 3:** Creative pace clock use cases + AI preview
3. **Day 5:** Full AI demo with social proof
4. **Day 7:** Before/after testimonial (pain point: "Stop spending 90 minutes planning practice on Sunday night")
5. **Day 10:** Limited-time offer for pace clock customers

**Key insight:** These customers already trust the brand and care about their program - highest conversion potential

**Next steps:** 
- Write actual email copy
- Set up email automation
- Track open rates, click-through, trial signups, trial → paid conversions

#### Project #2: Training App Page Overhaul (swimpractice.com)

**Current problem:** Page gets traffic but doesn't convert - messaging is weak

**New framework:**

**Hero section:**
- Headline: "Stop Wasting Sundays Planning Practice. AI Does It in 30 Seconds."
- Subhead: Championship-level practices based on your team, season, goals
- Visual: Animated demo of AI generating practice
- CTA: "Try Free - No Credit Card Required"

**Key sections:**
1. Social proof (testimonials, program logos, usage stats)
2. How it works (3 simple steps)
3. Before vs After (90 min planning → 30 seconds)
4. Features that matter (championship pacing models, evidence-based zones, explains WHY sets work)
5. Clear pricing (free trial, monthly cost, value anchor: "Less than 1 hour of coaching pay, saves 5+ hours/month")

**Core conversion angle:** Coaches already spend hours planning practice - show them the time savings + quality improvement

**Next steps:**
- Write page copy
- Design/build new page
- A/B test headlines and CTAs

**Last discussed:** Feb 28, 2026 (memory/2026-02-28.md)

---

### 🎨 LIAC Scoreboard Theme - LIVE (Feb 2026)
**Status:** Deployed and live

**What it is:**
- Full 10-lane scoreboard overlay for Long Island Aquatic Club
- Built for OBS streaming software
- Shows race timer, swimmer names, splits, final times, places

**Live URL:** https://swimnerdtim.github.io/obs-overlays/themes/liac/

**Design:**
- LIAC colors: Blue (#0069B3) and Red (#CE1126)
- 10 lanes (vs Barbie's 8)
- First place gets gold sparkle animation
- Demo mode with sample race data
- BroadcastChannel API for Swimnerd Live integration

**Files:** `/Users/tim/.openclaw/workspace/obs-overlays/themes/liac/`

---

### 💖 Barbie Theme for Swimnerd Live - COMPLETE (Feb 2026)
**Status:** Complete, in use by customers

**What it is:**
- Hot pink themed overlay for swim meet streaming
- Customer (lgbeno) built Mario theme, we built Barbie theme
- Barbie drives pink convertible across screen every 8 seconds
- Sparkles, glowing animations, crown for 1st place

**Files:** `/Users/tim/.openclaw/workspace/obs-overlays/themes/barbie/`
- Custom fonts: Pacifico (headers), Righteous (numbers)
- AI-generated Barbie convertible image (Gemini)
- Works with OBS Browser Source

**Built for:** Nate's daughters Eve and Perry (they wanted Barbie without sunglasses!)

---

### 📺 YouTube Automation (Night Swim) - IN PROGRESS
**Status:** Authentication setup complete, automation postponed

**What exists:**
- YouTube OAuth tokens: `/Users/tim/.openclaw/credentials/youtube-tokens-nightswim.json`
- Pipeline script: `/Users/tim/.openclaw/workspace/swimnerd/nightswim_pipeline.py`
- Purpose: Auto-upload Night Swim clips from Google Drive

**Current use:** Twitter bot uses YouTube API to check for new episodes

---

## Twitter API Setup
- **Account:** @SwimNerds (15.3K followers)
- **Cost:** $100/month Twitter API access (Nate paid)
- **Permissions:** Read + Write (regenerated Feb 13, 2026)

---

## Swimnerd AI
- **API:** `https://swimnerd-ai.azurewebsites.net/api/Chats/ask`
- **Key:** `g78901efgh234ijk3456`
- **Use:** Generates swimming commentary for Twitter bot

---

## Commands to Remember

**Generate news drafts:**
```bash
cd /Users/tim/.openclaw/workspace/swimnerd/twitter-bot
python3 generate_drafts.py 5
```

**Post approved drafts:**
```bash
python3 post_approved.py "3, 5"
```

**Check Night Swim status:**
```bash
python3 post_nightswim.py --test
tail -f logs/nightswim.log
```

**View cron jobs:**
```bash
crontab -l
```

---

## @SwimNerds Voice Guidelines
- Short punchy insider commentary
- NOT instructional tips
- Examples: "Santos is back." / "No slouches at the China Open."
- Skip boring college recruiting stories

---

## Important Context
- **YouTube channels:** Night Swim (active), Inside with Brett Hawke (inactive)
- **News sources:** Swimming World, @kylesockwell, @Braden_Keith, etc.
- **Bird CLI:** Tried but blocked by Twitter, using official API instead

---

## People & Context

**Nate's Family:**
- **Eve and Perry** - Nate's daughters (met during Barbie theme project)
- **Eve:** Noticed Barbie had sunglasses, wanted them removed (we regenerated the image)

**Swimnerd Ecosystem:**
- **Swimnerd Live** - Scoreboard/timing software ($499/yr SaaS)
- **Night Swim** - Podcast with Dax & Elvis (daily YouTube uploads at 12:30pm & 5:30pm)
- **Inside with Brett Hawke** - Older podcast series (1,085 interviews, currently inactive)
- **@SwimNerds** - Twitter account (15.3K followers)

**Key Contributors:**
- **lgbeno** - Customer who built Mario theme templates (open source)

---

## GitHub & Deployment

**Repos:**
- `swimnerdtim/obs-overlays` - Public themes (LIAC, Barbie, TMNT)
- SSH key on Mac: `ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIHW26a4yapuZy/libl64+2Z70gPVFfCUypwv/QoxcKx1`

**Live Sites:**
- Themes: https://swimnerdtim.github.io/obs-overlays/themes/
- LIAC: https://swimnerdtim.github.io/obs-overlays/themes/liac/
- Barbie: https://swimnerdtim.github.io/obs-overlays/themes/barbie/
- TMNT: https://swimnerdtim.github.io/obs-overlays/themes/tmnt/

---

## 🏊 Swimnerd Calculator - COMPLETE (Feb 14-16, 2026) ✅

**Status:** ✅ Production ready, awaiting deployment decision from Pavan

**What it is:**
Interactive swimming calculator with 4 tabs:
1. **Personal Bests** - Quick reference with split tooltips
2. **Meet Goals** - 4 pacing models (Personalized, Championship, British, Australian)
3. **Training Zones** - 6 zones with detailed checkpoints, printable
4. **Progression** - Complete meet history (1,819 swims across 16 events)

**Key achievements:**
- ✅ Built 103 championship speed charts (Olympics, Worlds, NCAA)
- ✅ Extracted 1,819 swims from SwimCloud Raw Data
- ✅ Created interactive pacing calculator with 4 models
- ✅ Built training zones calculator with detailed checkpoints
- ✅ Fixed all bugs (tab switching, time formatting, sort order)

**Final deliverable:**
- File: `/Users/tim/.openclaw/workspace/swimnerd/calculator_final.html` (288 KB)
- Self-contained: All data embedded inline, no dependencies
- Handoff doc: `/Users/tim/.openclaw/workspace/swimnerd/CALCULATOR_HANDOFF_FOR_PAVAN.md`

**Data coverage:**
- 16 events (25 Back → 400 IM)
- 1,819 total swims (all 3 courses)
- 103 championship speed charts
- Most recent swims shown first
- Times >60s formatted as MM:SS

**Next step:** Pavan decides deployment approach (GitHub Pages, website integration, or React/Vue conversion)

---

## Recent Work: Swimnerd Calculator - Complete Audit & Enhancement (Feb 14, 2026) ✅

**Status:** ✅ Production-ready HTML calculator with all SCY splits + cleaned UI

**What was accomplished:**
1. ✅ **Audited all 6 existing tabs** - found and fixed critical data quality issues
2. ✅ **Built new Time Converter tab** - personalized conversion factors SCY/SCM/LCM
3. ✅ **Added ALL SCY personalized splits** - 15 events with checkpoint data (Feb 14 evening)
4. ✅ **Cleaned up Meet Goals UI** - chronological split boxes, much cleaner display

### Issues Found & Fixed:

**Meet Goals Tab:**
- ❌ 3 SCM events (100 Free, 100 Back, 100 Fly): checkpoint times going BACKWARD
- ❌ Australian 100 Free LCM: nonsense data (49s at 25m)
- ✅ **FIXED:** Applied corrections using championship pacing data
- File: `/Users/tim/.openclaw/workspace/swimnerd/MEET_GOALS_CORRECTIONS.md`

**Progression Charts Tab:**
- ❌ 2 outlier times (24.86s, 25.05s in 100 Back LCM) - impossibly fast
- ✅ **FIXED:** Deleted rows 180-181 (likely 50m times mislabeled as 100m)

**Other Tabs:**
- ✅ RPE Pace Charts: No issues
- ✅ Personal Bests: No issues
- ✅ Practice Goals: No issues
- ✅ Race Strategy: Excellent (evidence-based from championship data)

### Time Converter Tab (NEW):

**Created:** `/Users/tim/.openclaw/workspace/swimnerd/build_time_converter.py`

**Features:**
- Personalized conversion factors calculated from actual PBs
- Comparison to standard (elite average) factors
- Quick reference converter for all events
- Performance insights about turn/underwater work

**Key Finding:**
- Average 3-4% slower conversion than standard elite swimmers
- SCY → LCM: 1.162x (vs 1.12x standard)
- **Opportunity:** Improve underwater kicks and streamlining off turns
- **Exception:** Breaststroke conversions BETTER than standard ✅

**Deliverables:**
- New tab added to spreadsheet
- Summary doc: `/Users/tim/.openclaw/workspace/swimnerd/TIME_CONVERTER_SUMMARY.md`

**Spreadsheet:** https://docs.google.com/spreadsheets/d/10eTIYp137vUVF9Wbialg_JuELzQT6wqEupRMZsbLGSs/edit

**All 7 tabs now complete:** Meet Goals, RPE Pace Charts, Progression Charts, Personal Bests, Practice Goals, Race Strategy, Time Converter

**Model:** Opus 4 (added to allowlist for complex analysis)

---

### Evening Session (Feb 14, 2026) - SCY Splits + UI Cleanup ✅

**Problem:** Meet Goals tab missing SCY personalized splits, UI was cluttered

**What we fixed:**
1. ✅ **Extracted ALL SCY splits** from `splits_data.json`:
   - 50/100/200 Free, Back, Breast, Fly
   - 100/200/400 IM
   - All 15 SCY events now have personalized checkpoint data
   - Built `scy_meet_goals_complete.json` with all splits

2. ✅ **Fixed 200 IM SCY** - was showing "no data", now displays 4 checkpoints (21.65/47.26/77.04/102.77)

3. ✅ **Cleaned up Meet Goals UI**:
   - Changed from 2-column grid to **chronological flex boxes**
   - Each checkpoint now in its own clean box (50y → 100y → 150y → 200y)
   - Fixed text overflow issue (21.80 running into "100y:")
   - Much cleaner visual hierarchy

**Files updated:**
- `/Users/tim/.openclaw/workspace/swimnerd/calculator_updated.html` - main calculator
- `/Users/tim/.openclaw/workspace/swimnerd/build_complete_scy_data.py` - SCY extraction script
- `/Users/tim/.openclaw/workspace/swimnerd/scy_meet_goals_complete.json` - all SCY data
- `/Users/tim/.openclaw/workspace/swimnerd/meetGoalsData_complete.js` - merged data object

**Current display for each event:**
- **SCY events:** Personalized splits only (your actual race data)
- **SCM events:** Personalized + British Model (15 checkpoints)
- **LCM events:** Personalized + British + Australian Models

**Next steps discussed:**
- Build Swimnerd speed charts from additional meet data (SwimCloud, Omega timing)
- Add NCAA Model for SCY events (already have Race Strategy data with NCAA 2025 pacing)

---

### 📊 Master Speed Charts Library - COMPLETE (Feb 15, 2026) ✅

**Status:** ✅ **79 championship speed charts extracted and merged**

**What we built:**
Comprehensive library of world-class race pacing data from championship finals:
- **LCM (47 events)**: 13 from Paris 2024 Olympics + 34 from 2025 World Championships Singapore
- **SCM (32 events)**: Complete coverage from 2024 World Championships Budapest
- **SCY (0 events)**: To be added (NCAA 2025 data)

**Data sources:**
1. Paris 2024 Olympics (LCM) - 13 events extracted from Omega timing XLSX files
2. **2025 World Championships Singapore (LCM)** - 34 finals extracted from LENEX XML (NEW!)
3. 2024 World Championships Budapest (SCM) - 32 finals from LENEX XML
4. NCAA 2025 Championships (SCY) - pending

**File locations:**
- **Master file**: `/Users/tim/.openclaw/workspace/swimnerd/master_speed_charts_final.json`
- Individual extractions: `worlds_2025_lcm_finals.json`, `scm_worlds_2024_finals_complete.json`, etc.
- Extraction scripts: `extract_lcm_worlds_2025_fixed.py`, `extract_scm_lenex.py`

**Data structure:**
Each speed chart includes:
- Event name (e.g. "200m Free"), gender, course
- Competition name and year
- Sample size (n=8 finalists typically)
- Checkpoint splits with average time and pacing percentage
- Individual finalist data (athlete, nation, time, splits)

**Technical learnings:**
- LENEX XML is gold standard for timing data (structured hierarchy)
- Omega timing XLSX files work but require custom parsers for different formats
- Time parsing needs to handle HH:MM:SS.HH format (not just MM:SS.HH)
- Finals identified by `round="FIN"` attribute in LENEX

**Next steps:**
1. Add NCAA 2025 SCY data (if available)
2. Integrate into calculator HTML as "Championship Model" dropdown option
3. Replace existing meet goal pacing models with this comprehensive dataset
4. Show all 79 speed charts across 3 courses in calculator

---

### 🎉 **Swimnerd Calculator - Championship Model Complete (Feb 15, 2026)** ✅

**Status:** **PRODUCTION READY**

**What we built:**
Interactive swimming calculator with **4 pacing models**:
1. 📊 Personalized - Swimmer's actual splits
2. 🏆 Championship - Top 8 finalists from world meets ⭐ **NEW**
3. 🇬🇧 British Model - Research-based
4. 🇦🇺 Australian Model - Research-based

**Championship Model coverage:**
- **58 events ready:** 34 LCM (Worlds 2025) + 24 SCY (NCAA 2025)
- Top 8 finalists only (medal contenders)
- Auto-scales to swimmer's goal time

**Files:**
- `calculator_updated.html` - Interactive calculator (self-contained)
- `championship_data_for_js.json` - 58 championship speed charts
- **GitHub repo:** `swimnerd-speed-charts/` (ready to push)

**Bugs fixed (Feb 15 evening):**
1. ✅ Gender suffix lookup (`100-free` → `100-free-men` or `-women`)
2. ✅ CORS issue (embedded data inline, no fetch needed)
3. ✅ SCY data extraction bug (corrected all 24 events with proper elite pacing)

**How to use:**
1. Open `calculator_updated.html` in browser
2. Click Meet Goals tab
3. Select event (100 Free, 200 IM, etc.)
4. Click goal box (PB, -1%, -2%, -3%)
5. See 4 models side-by-side with scaled splits

**Example: 100 Free SCY (42.56s goal)**
- Championship Model shows: 50y = 20.34s, 100y = 42.56s
- Based on NCAA 2025 Division I finalists (n=8)

**Next steps:**
- Push to GitHub (instructions in `PUSH_TO_GITHUB.md`)
- Deploy to production
- Test with real swimmers

---

### 🔧 WhatsApp Group Mention Detection Bug - FIXED (Feb 17, 2026) ✅

**Status:** ✅ **Bug identified and patched** → ⏳ **Pending user testing**

**Problem:**
- Bot received group messages but `wasMentioned` was **always false**
- `mentionedJids` was **always null** even with explicit `@tim` mentions
- Messages not processed into sessions due to failed mention detection

**Root Cause:**
Bug in `extractMentionedJids()` function (`/opt/homebrew/lib/node_modules/openclaw/dist/web/inbound/extract.js`):
1. Only checked specific message type paths
2. Missed general `contextInfo` extraction
3. Only checked `mentionedJid` (singular), not `mentionedJids` (plural)
4. Missing `conversation` message type

**Fix Applied:**
Patched `extractMentionedJids()` to:
- Use `extractContextInfo()` helper (finds contextInfo across all message types)
- Check both `mentionedJid` AND `mentionedJids` variants
- Added conversation message type checks
- Kept all legacy path checks for compatibility

**Next Step:**
Test in WhatsApp groups (SWIMNERD LIVE, Night Swim Podcast) by sending `@tim` mention

**Config:**
- `groupPolicy: "open"` (all groups allowed)
- No filters (bot uses AGENTS.md rules for when to respond)

---

### 📏 15m Chunks Model - COMPLETE (Feb 28, 2026) ✅

**Status:** ✅ Production ready, integrated into calculator

**What it is:**
Ultra-detailed pacing model for 100 LCM events (Free, Back, Breast, Fly) showing 15m splits for:
- **15m from start** - Underwater + breakout
- **15m turn out** - 7.5m in + 7.5m out  
- **15m to finish** - Final sprint to touch

**Features:**
- **Gender neutral** - one model for both men and women
- **Time range:** 45.0s → 58.0s (extrapolated from Nate's images)
- **26 data points** per event (0.5s increments)
- **Auto-scaling** - matches any goal time proportionally

**Integration:**
1. **New "15m Chunks" tab** - standalone calculator
2. **Added to Meet Goals** - 5th pacing model alongside Personalized, Championship, British, Australian
3. **Only shows for 100 LCM events** - contextual display

**Key files:**
- `calculator_with_chunks.html` - Production calculator (6,717 lines)
- `chunks_15m_data.json` - Complete dataset (4 strokes × 26 times)
- `15M_CHUNKS_SUMMARY.md` - Feature documentation
- `15M_CHUNKS_EXAMPLE.md` - Visual examples + stroke comparison

**Example (100 Free LCM @ 50.0s):**
- 15m start: 6.11s (underwater efficiency)
- 15m turn: 7.30s (wall execution)
- 15m finish: 8.00s (final sprint)

**Stroke patterns identified:**
- **Back:** Fastest underwater (5.86s vs 6.11s free)
- **Breast:** Explosive start (5.22s), slow finish (8.29s) 
- **Fly:** Front-loaded, balanced pacing
- **Free:** Most even negative split

**Use case:** Identify weak spots (slow start? slow finish?) and target training

**Built:** 2026-02-28
**Ready for:** Deployment alongside existing calculator features

---

---

### 🔄 SwimCloud Calculator Importer - COMPLETE (Mar 2, 2026) ✅

**Status:** ✅ Complete 3-step pipeline

**What it is:**
Automated tool to generate personalized Swimnerd Calculators from SwimCloud data for ANY swimmer.

**How it works:**
1. **Step 1:** Scrape time IDs (manual event entry + browser automation)
2. **Step 2:** Get detailed splits for each time
3. **Step 3:** Generate custom calculator HTML

**Key files:**
- `swimcloud-importer/step1_get_time_ids.py` - Scrape time IDs
- `swimcloud-importer/step2_get_splits.py` - Get detailed splits
- `swimcloud-importer/step3_generate_calculator.py` - Generate calculator
- `swimcloud-importer/README.md` - Full documentation

**Features:**
- Works for ANY SwimCloud swimmer ID
- Extracts all PBs across SCY/SCM/LCM
- Captures full progression data
- Generates calculator with swimmer's name + ID in header
- All tabs working (Personal Bests, Meet Goals, Training Zones, Progression, 15m Chunks)

**Usage:**
```bash
cd /Users/tim/.openclaw/workspace/swimnerd/swimcloud-importer
python3 step1_get_time_ids.py 166348  # Get time IDs
python3 step2_get_splits.py           # Get splits
python3 step3_generate_calculator.py  # Generate HTML
```

**Output:** `calculator_{swimmer_id}.html` ready to open in browser

**Built:** 2026-03-02
**Status:** Production ready

---

**Last updated:** 2026-03-02 (SwimCloud importer pipeline built) ✅
**Next:** Test with additional swimmers beyond Michael Andrew
