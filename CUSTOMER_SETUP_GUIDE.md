# Swimnerd Live Digital Scoreboard Setup Guide

**For Customer Service Use - Bob's Guide to Theme Setup**

---

## Overview

Swimnerd Live digital scoreboards let meet directors display real-time race results on TVs, projectors, or live streams **without expensive Cat6 cabling**. Each theme is a web page that customers load into OBS Studio (free broadcasting software) or directly in a web browser.

**Available Themes:**
- **Barbie** - Hot pink glamour with animated story sequences
- **Johnny Castaway** - Retro Windows 3.1 screensaver nostalgia
- **TMNT** - Teenage Mutant Ninja Turtles sewer adventure with arcade-style animations

**What Customers Get:**
- 8-lane race results with subtractive splits + cumulative times
- Live race timer
- Pool record display
- First-place gold highlighting
- Themed animations and styling

---

## Prerequisites

**Required Software:**
- **OBS Studio** (free) - Download at https://obsproject.com
- **Modern Web Browser** - Chrome, Firefox, or Edge (Safari works but Chrome recommended)
- **Swimnerd Live** - Must have active subscription with race timing data

**Recommended Hardware:**
- Computer/laptop running Windows, macOS, or Linux
- TV or projector for display (1920×1080 resolution recommended)
- WiFi or ethernet connection

---

## Step 1: Download Theme Files

**Option A: GitHub Pages (Easiest)**
1. Go to: https://swimnerdtim.github.io/obs-overlays/
2. Navigate to the theme folder (e.g., `/themes/barbie/`)
3. Open the main HTML file in browser:
   - **Barbie**: `scoreboard.html`
   - **Johnny Castaway**: `johnny-scoreboard.html`
   - **TMNT**: `tmnt-scoreboard.html`
4. Copy the full URL from browser address bar (e.g., `https://swimnerdtim.github.io/obs-overlays/themes/barbie/scoreboard.html`)

**Option B: Download Locally**
1. Go to: https://github.com/swimnerdtim/obs-overlays
2. Click green **Code** button → **Download ZIP**
3. Extract ZIP to a folder (e.g., `C:\Swimnerd\Themes\` on Windows or `~/Swimnerd/Themes/` on Mac)
4. Note the file path to the HTML file you want to use

---

## Step 2: Set Up OBS Studio

### Install OBS (First-Time Setup)
1. Download OBS Studio: https://obsproject.com
2. Install and launch OBS
3. Run Auto-Configuration Wizard (appears on first launch):
   - Select **"Optimize for recording"** or **"Optimize for streaming"**
   - Set canvas resolution to **1920×1080** (Full HD)
   - Click **Apply Settings**

### Create a Scene for the Scoreboard
1. In OBS, look at bottom-left **Scenes** panel
2. Click **+** button → Name it "Swim Meet Scoreboard"
3. Scene is now ready for sources

---

## Step 3: Add Scoreboard as Browser Source

### Add Browser Source
1. In **Sources** panel (bottom-center), click **+** button
2. Select **Browser** from the list
3. Name it (e.g., "Barbie Scoreboard")
4. Click **OK**

### Configure Browser Source Settings

**For GitHub Pages URL (Option A):**
- **URL**: Paste the full GitHub Pages URL
  - Example: `https://swimnerdtim.github.io/obs-overlays/themes/barbie/scoreboard.html`

**For Local File (Option B):**
- **URL**: Leave blank
- **Local file**: Check this box
- Click **Browse** → Navigate to the HTML file (e.g., `C:\Swimnerd\Themes\obs-overlays\themes\barbie\scoreboard.html`)

**Resolution Settings (ALL THEMES):**
- **Width**: 1920
- **Height**: 1080

**Additional Settings:**
- ✅ **Shutdown source when not visible** (saves resources)
- ✅ **Refresh browser when scene becomes active** (ensures fresh data)
- ❌ **Control audio via OBS** (leave unchecked unless theme has sound)

**Custom CSS (OPTIONAL - for advanced users):**
- Leave blank unless customer requests custom styling

4. Click **OK**

---

## Step 4: Connect to Swimnerd Live Data

### BroadcastChannel API (Recommended)
Swimnerd Live sends race data to the scoreboard automatically via JavaScript BroadcastChannel API.

**Setup:**
1. Open Swimnerd Live timing software
2. Go to **Settings** → **Display Options**
3. Enable **"Send Data to Digital Scoreboard"**
4. Select **BroadcastChannel Mode**
5. Test by starting a race - scoreboard should update automatically

### WebSocket Server (Alternative)
If customer has custom WebSocket server setup:

1. In browser source properties, add to URL:
   - `?wsUrl=ws://localhost:8080` (replace with actual WebSocket URL)
2. Swimnerd Live must broadcast race data to this WebSocket endpoint

**Example Full URL:**
```
https://swimnerdtim.github.io/obs-overlays/themes/barbie/scoreboard.html?wsUrl=ws://192.168.1.100:8080
```

---

## Step 5: Test the Scoreboard

### Demo Mode (No Live Data Required)
Each theme has a built-in demo mode for testing:

1. Right-click on Browser Source in OBS → **Interact**
2. A browser window opens with the scoreboard
3. Open browser console:
   - **Windows/Linux**: Press `F12` or `Ctrl+Shift+J`
   - **Mac**: Press `Cmd+Option+J`
4. Type `startDemo()` and press Enter
5. Fake race data will populate the scoreboard

**Expected Behavior:**
- 8 lanes appear with swimmer names
- Splits and times update
- Race timer counts up
- First place gets gold highlight

### Live Race Test
1. Set up a practice race in Swimnerd Live
2. Start the race timer
3. Watch scoreboard update in real-time
4. Touch finish times should populate immediately

**Troubleshooting Live Data:**
- If scoreboard doesn't update, check BroadcastChannel is enabled in Swimnerd Live settings
- Refresh browser source: Right-click → **Refresh**
- Check browser console for error messages (F12)

---

## Step 6: Display on TV/Projector

### Option A: Full-Screen Display Window
1. In OBS, go to **View** → **Fullscreen Projector (Scene)**
2. Select the display (TV/projector) to show on
3. Scoreboard appears full-screen on that display

### Option B: HDMI Output
1. Connect computer to TV via HDMI cable
2. Set TV as extended display (not mirrored)
3. Drag OBS projector window to TV screen
4. Press **F11** to fullscreen

### Option C: Live Stream
1. Set up streaming destination (YouTube, Facebook, etc.) in OBS Settings
2. Click **Start Streaming** - scoreboard goes live
3. Viewers see the themed scoreboard with race results

---

## Theme-Specific Features

### Barbie Theme
- **Hot Pink Design**: Gradient backgrounds, gold first-place highlight
- **Animated Story Canvas**: Top strip shows Barbie's beach adventure
- **Story Progression**: Linear day-by-day story (24 hours per in-story day)
- **Dev Helpers** (Browser Console):
  - `__barbie.reset()` - Restart story from Day 1
  - `__barbie.skipToDay(5)` - Jump to specific day

**Best Use Cases:**
- Family-friendly meets
- Youth swimming events
- Fun/themed meet nights

### Johnny Castaway Theme
- **Windows 3.1 Nostalgia**: Authentic VGA 16-color palette
- **Embedded Screensaver**: Real Johnny Castaway animations play on island
- **Tropical Aesthetic**: Ocean blues, sandy yellows, white lane cards
- **Colors**:
  - Lane numbers: Blue
  - Place numbers: Yellow
  - Splits/times: Green

**Best Use Cases:**
- Retro-themed meets
- 90s nostalgia events
- Tech-savvy audiences who remember screensavers

### TMNT Theme
- **Sewer/NYC Aesthetic**: Dark green gradients, brick textures
- **Pizza Box Header**: Orange/red pizza box with event info
- **Turtle Color Borders**: Lanes rotate between Leonardo (blue), Raphael (red), Donatello (purple), Michelangelo (orange)
- **Luke-Style Animations**:
  - Sewer slide-in (lanes bounce in from left)
  - Pizza bounce (place numbers jump)
  - Turtle power glow (first place pulsates gold)
  - Turtle chase sequence (all 4 turtles run across screen, chased by Shredder + Krang)
- **Retro 8-bit Sprites**: Authentic arcade game pixel art

**Best Use Cases:**
- Kids/teen meets
- Comic-con style events
- Nostalgia for 80s/90s TMNT fans

---

## Common Issues & Fixes

### Scoreboard Not Showing
**Symptom**: Black screen or blank browser source

**Fixes:**
1. Check URL is correct (no typos)
2. If local file, verify file path exists
3. Right-click source → **Refresh**
4. Check OBS browser source width/height is 1920×1080
5. Disable antivirus/firewall temporarily (may block local files)

### Data Not Updating
**Symptom**: Scoreboard shows but times don't update

**Fixes:**
1. Verify Swimnerd Live has **"Send Data to Digital Scoreboard"** enabled
2. Check both Swimnerd Live AND OBS are running
3. Test with `startDemo()` in browser console (F12)
4. Restart both Swimnerd Live and OBS
5. Check BroadcastChannel API is supported (Chrome/Firefox/Edge - Safari may have issues)

### Animations Not Playing (TMNT)
**Symptom**: Lanes appear but no sewer slide-in or turtle chase

**Fixes:**
1. Wait 1.5 seconds after lanes load (animations trigger on delay)
2. Check browser console (F12) for JavaScript errors
3. Refresh browser source
4. Use Chrome browser (best JavaScript performance)

### Story Not Progressing (Barbie)
**Symptom**: Story canvas stuck on same scene

**Fixes:**
1. Check browser console: `localStorage.getItem('barbie_castaway_day_v1')`
2. Reset story: `__barbie.reset()` in console
3. Clear browser cache in OBS Settings → Advanced → Delete Cache
4. Story progresses in real-time (24 hours per day) - may need to wait

### Johnny Castaway Not Animating
**Symptom**: Island appears but Johnny doesn't move

**Fixes:**
1. Wait 30-60 seconds (screensaver has random idle periods)
2. Refresh browser source
3. Check internet connection (iframe loads from external site)
4. If offline, use Barbie or TMNT themes instead

### Text Too Small on Large TV
**Symptom**: Readable on computer but hard to see from distance

**Fixes:**
1. Move closer to TV (10-15 feet ideal viewing distance)
2. Use larger TV (65" or bigger for large rooms)
3. Increase OBS canvas resolution to 4K (3840×2160) if TV supports it
4. Contact support for custom font sizing

### First Place Not Highlighting Gold
**Symptom**: All lanes same color

**Fixes:**
1. Wait for race to finish (highlight only appears after final times)
2. Check place data is being sent by Swimnerd Live
3. Test with demo mode: `startDemo()` in console
4. Refresh browser source

---

## Advanced Customization

### Custom Pool Record
Customers can set their own pool record by editing the HTML file:

1. Open HTML file in text editor (Notepad++, VS Code, etc.)
2. Find this line:
   ```html
   <div class="pool-record">Pool Record: 21.34</div>
   ```
3. Change `21.34` to the actual pool record
4. Save file and refresh OBS browser source

### Custom Event Name
1. In Swimnerd Live, set the event name in race setup
2. Scoreboard pulls event name automatically from BroadcastChannel data
3. If using demo mode, edit HTML file:
   ```html
   <div class="event-name">Men's 50 Freestyle</div>
   ```

### Multiple Themes in One Show
Customers can switch between themes mid-meet:

1. Create multiple scenes in OBS (one per theme)
2. Add different browser sources to each scene
3. Use **Scene Transitions** to switch between themes
4. Hotkeys can be assigned for quick switching

---

## Performance Optimization

### Reduce CPU Usage
- Enable **"Shutdown source when not visible"** in browser source settings
- Close unnecessary programs while running OBS
- Lower OBS canvas resolution to 1280×720 if computer struggles

### Smooth Animations
- Use wired ethernet connection instead of WiFi
- Close other browser tabs on computer
- Disable Windows/Mac visual effects (performance mode)
- Update graphics drivers

### Battery Saving (Laptops)
- Plug into power during meets (don't run on battery)
- Disable sleep mode in power settings
- Lower screen brightness on laptop (projector brightness is what matters)

---

## Support & Troubleshooting

### Before Contacting Support
1. Try demo mode (`startDemo()` in console) to isolate issue
2. Check browser console (F12) for error messages
3. Restart OBS and Swimnerd Live
4. Test with a different browser (Chrome recommended)
5. Clear OBS browser cache (Settings → Advanced → Delete Cache)

### When Contacting Support, Provide:
- Operating system (Windows 10/11, macOS version, Linux distro)
- OBS version (Help → About)
- Browser source URL or file path
- Theme name (Barbie, Johnny Castaway, TMNT)
- Error messages from browser console (F12)
- Screenshot or screen recording of the issue

### Support Channels
- **Email**: support@swimnerd.com
- **Phone**: [INSERT PHONE NUMBER]
- **Live Chat**: swimnerd.com/support (9 AM - 5 PM EST)
- **GitHub Issues** (for bugs): https://github.com/swimnerdtim/obs-overlays/issues

---

## Quick Reference Card (Print This for Bob)

### Setup Checklist
- [ ] OBS Studio installed
- [ ] Theme files downloaded or GitHub Pages URL copied
- [ ] OBS scene created
- [ ] Browser source added (1920×1080 resolution)
- [ ] Swimnerd Live "Send Data to Digital Scoreboard" enabled
- [ ] Demo mode tested (`startDemo()` in console)
- [ ] Live race test successful
- [ ] TV/projector connected and displaying

### URLs for Quick Access
- **GitHub Pages Live Demo**: https://swimnerdtim.github.io/obs-overlays/
- **GitHub Repo (Download ZIP)**: https://github.com/swimnerdtim/obs-overlays
- **OBS Studio Download**: https://obsproject.com

### Theme File Names
- **Barbie**: `themes/barbie/scoreboard.html`
- **Johnny Castaway**: `themes/johnny-castaway/johnny-scoreboard.html`
- **TMNT**: `themes/tmnt/tmnt-scoreboard.html`

### Browser Console Commands
- **Demo Mode**: `startDemo()`
- **Reset Barbie Story**: `__barbie.reset()`
- **Skip Barbie to Day 5**: `__barbie.skipToDay(5)`

---

## Training Script for Bob

**Opening:**
> "Hi [Customer Name], I'm Bob from Swimnerd Live! I'm going to help you set up your digital scoreboard theme today. This is going to eliminate all that Cat6 cabling and make your meet displays super easy. Which theme are you interested in - Barbie, Johnny Castaway, or TMNT?"

**OBS Setup:**
> "First, let's make sure you have OBS Studio installed. It's free software - you can grab it at obsproject.com. Once that's open, we'll create a new scene called 'Swim Meet Scoreboard'."

**Browser Source:**
> "Now we're going to add a Browser source. Click the plus button under Sources, pick Browser, and name it after your theme. I'll give you the GitHub Pages URL to paste in, and make sure to set the width to 1920 and height to 1080."

**Data Connection:**
> "In your Swimnerd Live software, go to Settings → Display Options and turn on 'Send Data to Digital Scoreboard'. This lets the scoreboard automatically update during races."

**Testing:**
> "Let's test it out! Right-click on the browser source, click Interact, then press F12 to open the console. Type `startDemo()` and hit Enter. You should see fake race data populate the lanes. See it working? Perfect!"

**Go Live:**
> "Now just drag the OBS projector window to your TV screen, hit F11 for fullscreen, and you're live! When you start a real race in Swimnerd Live, the scoreboard will update automatically."

**Closing:**
> "You're all set! If anything goes wrong, just refresh the browser source or restart OBS. My email is bob@swimnerd.com if you need help later. Have a great meet!"

---

**Version 1.0 - Last Updated: February 8, 2026**

**Credits:**
- Theme Development: Tim (Swimnerd)
- Original Mario Theme Foundation: Luke G (https://github.com/lgbeno/swimnerd-templates)
- Johnny Castaway JavaScript Port: xesf (https://github.com/xesf/castaway)
