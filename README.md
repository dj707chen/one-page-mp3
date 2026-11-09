# MP3 Song Player with Lyrics Highlighting

This is a MP3 song player based on HTML and JavaScript, displaying multiple lines of lyrics, highlighting the currently
sung line of lyrics.

## Flow of modifying lyrics

The lyrics of each chapter are only in its `.timing.js` file next to the MP3, e.g.
`assets/AnlunHuang/ChineseRequiem/Chapter1.timing.js`. `index.html` has no lyrics; it reads them from these files.

1. Change the text in the `.timing.js` file, e.g. line 1 of the lyrics in `Chapter1.timing.js`:

```javascript
    {"time":0.1,"text":" ( Prayerfully 以祷告的心 )"},
```

   A line not timed yet has `"time":null`. Each time belongs to the line it is on, so when adding or removing
   a line, add or remove its time with it.

2. Timing the lyrics
Load the app HTML page, manually time the lyrics (LYRICS TIMING: Rec), then Save / Export to the same `.timing.js` file.
Saving keeps the text from the file and writes the new times.
