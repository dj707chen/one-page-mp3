# Lyrics font sizes: current line vs other lines

## Question

what's the difference between the font sizes of selected lyrics and other lines?

## Answer

Defined in `common.css`:

| View | Other lines (`.lyric-line`) | Current line (`.lyric-line.current`) | Difference |
|---|---|---|---|
| Normal | 1.95rem (31.2px) | 2.15rem (34.4px) | +0.2rem (3.2px), about 10% larger |
| Maximized (`#app.lyrics-maximized`) | 2.7rem (43.2px) | 3.1rem (49.6px) | +0.4rem (6.4px), about 15% larger |

(px values assume the browser default root size of 16px.)

- Lines above (`.before`) and below (`.after`) share the base size; they differ from each other only in color/background (and opacity 0.9). `.distant` lines are also the same size, just faded to opacity 0.28.
- The size change animates over 0.3s (`transition: font-size 0.3s ease`).
- In bilingual mode, the original and translation columns inherit the line's size, so both columns of the current line grow together.
- Font size is not one of the URL-param settings; only colors/backgrounds are configurable.

---

## Question

make the difference of font size of current line only 5% larger than other lines

## Answer

Changed the current-line sizes in `common.css`, writing each as base × 1.05 so the 5% ratio is clear:

| View | Other lines | Current line (before) | Current line (now) |
|---|---|---|---|
| Normal | 1.95rem (31.2px) | 2.15rem (34.4px) | `calc(1.95rem * 1.05)` = 2.0475rem (32.76px) |
| Maximized | 2.7rem (43.2px) | 3.1rem (49.6px) | `calc(2.7rem * 1.05)` = 2.835rem (45.36px) |

No JavaScript depends on these sizes; the 0.3s size transition and re-centering after it are unchanged.

---

## Question

default width of the left lyrics panel is 40%, right is 60%; change them to 50% by default

## Answer

Changed `--lyrics-original-width` in `common.css` `:root` from 40% to 50%; the translation column takes the remaining `1fr`, so it is now 50% too. The double-click reset in `app.js` just removes the inline override, so it falls back to the new 50% with no JS change.

Note: a browser that already has a dragged width saved (localStorage `onepagemp3.lyricsOriginalWidth`) keeps showing that width until the divider is double-clicked.
