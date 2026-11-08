# MP3 Song Player with Lyrics Highlighting

This is a MP3 song player based on HTML and JavaScript, displaying multiple lines of lyrics, highlighting the currently
sung line of lyrics.

## Flow of modifying lyrics

1. Change the text file, e.g line 1 of `assets/AnlunHuang/ChineseRequiem/Chapter1-Lyrics.txt`

```text
 ( Prayerfully 以祷告的心 )
```

2. `AI` copied it to `index.html` line 635:

```javascript
                 { text: " ( Prayerfully 以祷告的心 ) " },
```

From now on, the text file is now used by the program.

3. Timing the lyrics
Load the app HTML page, manually time the lyrics, then export to .js file
`assets/AnlunHuang/ChineseRequiem/Chapter1.timing.js`
