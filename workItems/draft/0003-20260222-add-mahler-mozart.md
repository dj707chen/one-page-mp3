# Add Mahler and Mozart Works to APP_DATA

**Created:** 2026-02-22

## Description

Extend `APP_DATA.artists` in `app.js` with works for Mahler and Mozart once their audio files and lyrics are available. The `assets/` directory already has subdirectories for these composers (currently empty).

## Pre-requisites

- Audio MP3 files sourced and placed under `assets/Mahler/` and `assets/Mozart/`
- Lyrics text for each work obtained

## Steps

1. Populate `assets/Mahler/` and `assets/Mozart/` with MP3 files
2. Add composer entries to `APP_DATA.artists` in `app.js`, following the existing structure:
   ```js
   {
     name: "Wolfgang Amadeus Mozart",
     works: [{
       title: "...",
       movements: [{
         title: "...",
         src: "assets/Mozart/.../Chapter1.mp3",
         lyrics: [{ text: "..." }]
       }]
     }]
   }
   ```
3. Verify the left nav tree lists all composers in ascending alphabetical order (the UI sorts automatically)
4. Test playback and lyrics display for each new work

## Acceptance Criteria

- Mahler and Mozart appear in the left navigation tree alongside Huang
- Their works and movements are selectable and playable
- Lyrics display correctly; highlighting works (with or without timestamps)
- Alphabetical ordering in the nav tree is correct
