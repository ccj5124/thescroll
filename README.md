# The Scroll

A social feed built on purpose to be addictive. After sixty seconds it turns on you and names every trick it just used, with your own numbers next to each one.

Made for a PYP Exhibition on phone addiction.

**Play it:** https://ccj5124.github.io/thescroll/

## How it works

For the first sixty seconds it is just an app called Loop. Nothing on screen hints that it is a lesson. Then the screen cuts to white and the whole thing becomes a cold session report.

Every number in the report is really measured while you play, not invented:

- time inside, swipes, likes, refreshes
- how far your finger actually travelled, in metres
- real things gained: 0

Then it lists the five techniques it used on you, and marks each one with what it did to *you* specifically:

| Technique | Marker | What it means |
| --- | --- | --- |
| Infinite scroll | `∞` | you never once saw a bottom |
| Variable rewards | `×3` | gold cards you hit |
| Near misses | `×4` | times it dressed up a nothing as a rare drop |
| Streaks | `38 run` | your longest unbroken run of swipes |
| The red number | `5 unread` | nobody messaged you, and it still climbed |

It closes on the point that matters: you are not weak, you lost to a machine that adults were paid to tune against you. Willpower is not the fix, changing the setup is. Five concrete things to change follow.

Bilingual, English and Chinese, toggled from the top right at any time.

## Running it

One file, no build step, no dependencies.

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`. Opening `index.html` straight off disk works too.

The only network request is the Google Fonts stylesheet. Everything else, including the artwork, is generated in the page, so it runs fine offline once the fonts are cached, and falls back to system fonts if they never load.

## Notes for running it at a booth

- Hand the device over and say nothing. The reversal only lands if the player was not warned.
- Add it to the iPad home screen to get it fullscreen with no browser chrome.
- A round is sixty seconds and **Play again** fully resets, so a queue keeps moving.
- Good question to ask once the report is up: *was that your self control, or was that the design?*

## Tuning

The reward schedule lives in `makeCard()` in `index.html`. Gold cards use a variable-ratio schedule with a pity timer at 18 cards, which lands every session between two and four hits, so the `×N` markers in the report are never zero. `DURATION` at the top of the script sets the round length in seconds.

## Licence

MIT. Take it, change it, run it at your own school.
