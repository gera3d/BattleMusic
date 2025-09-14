# BattleMusic

🎵 **A World of Warcraft Vanilla (1.12) addon that automatically plays epic battle music during combat!**

Transform your combat experience with custom music that starts when you enter battle and stops when combat ends. Perfect for Turtle WoW and other Vanilla servers.

## ✨ Features

- **Automatic Combat Detection**: Music starts when you enter combat, stops when combat ends
- **Random Track Selection**: Randomly selects from your music collection for variety
- **Zone Change Protection**: Music stops when changing zones for seamless gameplay
- **Minimap Button**: Convenient minimap button for quick access to settings
- **Easy Configuration**: Simple `/bmusic` command or minimap button opens the settings menu
- **Debug Mode**: Track what's happening behind the scenes
- **Custom Music Support**: Use any MP3 files you want

### 🎬 Video Demo (Outdated)
https://www.youtube.com/watch?v=YXQPcDtmPDo

---

## 🚀 Quick Start Guide

### 1. Install the AddOn
- Download and extract to `World of Warcraft\Interface\AddOns\`
- Ensure the folder is named exactly `BattleMusic` (rename if needed)
- Launch World of Warcraft

### 2. Add Your Music
- Navigate to `Interface\AddOns\BattleMusic\music\`
- Copy your `.mp3` files into this folder
- **No renaming required** - use any filenames you want
- Run `Update Playlist.bat` in the music folder *(Note: Currently using default playlist)*
- Restart WoW to load new music

### 3. Configure Settings
Open the configuration menu in one of two ways:

**Option A: Minimap Button** 🎯
- Look for the drum/music note icon around your minimap
- Left-click to open the settings menu

**Option B: Chat Command**
```
/bmusic
```

![Configuration Menu](https://github.com/user-attachments/assets/7964eee1-bb7d-4ed5-92aa-38b0b912add3)

**Available Settings:**
- **Display Track Name**: Shows the current song name in chat when it starts
- **Debug Mode**: Displays technical information for troubleshooting
- **Show Minimap Button**: Toggle the minimap button visibility on/off

---

## ⚙️ Advanced Configuration

### Manual Song Limit (Currently Unused)
```
/script battleMusic.songs=NUMBER
```
*Example: `/script battleMusic.songs=10`*

### Linger Timer [DISABLED]
```
/script battleMusic.linger=NUMBER
```
*Example: `/script battleMusic.linger=15.5`*
*Note: This feature is currently disabled due to technical issues*

---

## 🔧 How It Works

### Technical Overview
- **Event-Driven System**: Uses WoW's built-in event system to detect combat state changes
- **Combat Detection**: 
  - `PLAYER_REGEN_DISABLED` = Combat starts → Music begins
  - `PLAYER_REGEN_ENABLED` = Combat ends → Music stops
  - `ZONE_CHANGED_NEW_AREA` = Zone change → Music stops
- **Random Selection**: Uses `math.random()` to pick tracks from your collection
- **Minimap Integration**: Custom minimap button with tooltip and click handlers
- **Saved Settings**: Configuration is saved per character (including button visibility)

### Current Playlist System
The addon currently uses a hardcoded playlist of 4 default tracks:
- `combat_1.mp3`
- `combat_2.mp3` 
- `combat_3.mp3`
- `combat_4.mp3`

*Note: Dynamic playlist generation via `Update Playlist.bat` is planned but not yet implemented.*

---

## 🐛 Known Issues & Limitations

### ⚠️ Currently Disabled Features
- **Linger Timer**: Music continuing after combat ends (code exists but doesn't work)
- **Dynamic Playlist**: `Update Playlist.bat` generates code but isn't integrated yet

### 🔍 Troubleshooting
- **No Music Playing**: Ensure you have MP3 files in the `music/` folder
- **Config Menu Not Opening**: Try `/reload` and then `/bmusic`
- **Music Continues Playing**: Zone change or `/reload` will stop it

---

## 🛠️ Development Notes

### File Structure
```
BattleMusic/
├── BattleMusic.lua     # Main addon logic
├── BattleMusic.toc     # Addon manifest
├── BattleMusic.xml     # UI frame definition
├── README.md           # This file
└── music/              # Your MP3 files go here
    ├── Update Playlist.bat
    ├── Put your music files here.txt
    └── [Your MP3 files]
```

### Author's Notes
*"I've rewritten most of the functionality of this addon to make it more reliable and fix some bugs. I've focused on making this addon as easy to setup as possible with the new Batch file included.*

*Song lingering has been disabled for the moment because I could not get it working. I've left my attempt in the main lua file for review. If someone wants to submit a PR to fix it, be my guest."*

---

## 📝 Contributing

Found a bug or want to add a feature? Contributions are welcome!

- **Linger Feature**: Help fix the post-combat music continuation
- **Dynamic Playlists**: Integrate the batch file playlist generation
- **UI Improvements**: Enhance the configuration interface

---

## 📋 Compatibility

- **WoW Version**: Vanilla 1.12 (Interface 11200)
- **Server**: Tested on Turtle WoW
- **Audio Format**: MP3 files supported
- **Dependencies**: None required 
