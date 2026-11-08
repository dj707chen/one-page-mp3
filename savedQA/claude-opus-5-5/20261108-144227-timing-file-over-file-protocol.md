# Session 2026-11-08 — Timing file not picked up when opened as file://

## Ask

> I deleted local storage for file:///Users/weiping/sharing/one-page-mp3/index.html,
> /Users/weiping/sharing/one-page-mp3/assets/AnlunHuang/ChineseRequiem/Chapter1.timing.json should be select to time
> the selection of Chapter1 lyrics, but looks like it was not

## Answer

**Cause:** the page was opened as `file://`. The app loaded the timing file next to the MP3 with `fetch()`, and
browsers block `fetch()` of local files from `file://` pages. The error was caught and silently ignored, so Chapter 1
fell back to "0 / 55 lines timed". The JSON itself was fine: 55 lines, matching the 55 lyric lines exactly.
(Reproduced in headless Chrome: empty localStorage, `file://` → no timing.)

**Fix:** the timing file is now `<audio>.timing.js` instead of `<audio>.timing.json`. It holds the same JSON, wrapped
in a single `onePageMp3Timing( ... );` call, so the app can load it with a `<script>` tag, which browsers allow from
`file://` pages.

- Auto-load: `<script src="…/Chapter1.timing.js">` replaces `fetch()`. A missing file is skipped quietly. A recording
  in this browser (localStorage) still takes priority over the file.
- Save / Export now write `.timing.js` (same layout: one lyric line per row, easy to hand-edit).
- Load accepts `.timing.js` and older `.timing.json` files.
- `assets/AnlunHuang/ChineseRequiem/Chapter1.timing.js` was generated from the existing `Chapter1.timing.json`
  (verified identical content). The `.json` file is no longer read automatically and can be deleted.

**Verified** in headless Chrome, both `file://` and `http://`: with empty localStorage, selecting Chapter 1 shows
"55 / 55 lines timed · Chapter1.timing.js". Chapter 2 (no file) stays untimed with no errors.

**Note:** timing only drives the highlight in **Auto** mode. The page starts in Manual mode unless opened with
`?highlight-mode=auto`, so switch to Auto to see it.
