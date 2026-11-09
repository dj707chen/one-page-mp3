# Add Mahler and Mozart Works to APP_DATA

**Created:** 2026-02-22

## Description

Add Mahler and Mozart (artist entries in `APP_DATA.artists` in `app.js`, plus a `work.js` per work in its assets folder) once their audio files and lyrics are available. The `assets/` directory already has subdirectories for these composers (currently empty).

## Pre-requisites

- Audio MP3 files sourced and placed under `assets/Mahler/` and `assets/Mozart/`
- Lyrics text for each work obtained

## Steps

1. Populate `assets/Mahler/` and `assets/Mozart/` with MP3 files
2. For each work, create `work.js` in its assets folder (e.g. `assets/Mozart/<Work>/work.js`), following
   `assets/AnlunHuang/ChineseRequiem/work.js`:
   ```js
   onePageMp3Work({
     id: "...",
     title: "...",
     movements: [{
       id: "ch1",
       number: "I",
       title: "...",
       audio: "assets/Mozart/<Work>/Chapter1.mp3"
     }]
   });
   ```
   Each movement's lyrics go in `Chapter1.timing.js` next to its MP3, not in `work.js`.
3. Add an artist entry to `APP_DATA.artists` in `app.js` that lists those files:
   ```js
   {
     id: "mozart",
     name: "Wolfgang Amadeus Mozart",
     nameSort: "Mozart, Wolfgang Amadeus",
     workFiles: ["assets/Mozart/<Work>/work.js"]
   }
   ```
4. Verify the left nav tree lists all composers in ascending alphabetical order (the UI sorts automatically)
5. Test playback and lyrics display for each new work

## Acceptance Criteria

- Mahler and Mozart appear in the left navigation tree alongside Huang
- Their works and movements are selectable and playable
- Lyrics display correctly; highlighting works (with or without timestamps)
- Alphabetical ordering in the nav tree is correct
