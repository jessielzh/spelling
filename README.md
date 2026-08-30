# Spelling Practice

A single-file spelling trainer for a Grade 4 poetry vocabulary list.

The browser reads each word aloud and **never shows it**, so it's a real test
rather than a copying exercise — that's the part a paper worksheet can't do on
its own, because someone has to say the word out loud.

- **Test** — hear the word, type it. Wrong answers get letter-by-letter feedback
  (`rythm` → *"you missed the h"*) and must be retyped correctly before moving on.
- **Practice** — see the word with its syllable chunks and meaning, and copy it.
- **Levels** — the list is split into ~4-5 word levels, shortest first. Warm up
  by copying them, then spell them blind for one to three stars.
- **Stars are always the latest run**, never the best — for a level and for each
  word. The home screen is meant to show how he spells things today.
- **One by one** — the same two passes on a single word, working through the
  week shortest to longest. Each word is scored on how many blind asks it took:
  ⭐⭐⭐ first, ⭐⭐ second, ⭐ third. Any blind pass updates it — a level and
  "Test all" score their words the same way.
- A word counts as learned after two correct cold spellings; misses come back
  later in the same round.

## Running it

Open `index.html`. That's all — no build step, no server, and it works offline.
Speech uses the browser's built-in Web Speech API (best in Safari or Chrome).

## Adding a new week

The word bank holds every test. Append the new week to the **end** of the
`WEEKS` array in `index.html` — don't edit or remove an old one:

```js
const WEEKS = [
  { week:"Aug 28", date:"2026-08-28", words:[...], levels:[...] },
  {
    week: "Sep 4",              // shown on the picker; also the storage key
    date: "2026-09-04",         // test date, drives the "3 days to go" line
    words: [
      { w:"rhythm", m:"the beat of a poem", c:"rhy·thm" },
      // w = word   m = short meaning   c = syllable chunks (optional)
    ],
    levels: [                   // every word must appear in exactly one level
      { n:1, name:"Short & Sweet", emoji:"🌱", ws:["rhyme","theme"] },
    ],
  },
];
```

Pills at the top switch weeks. Progress and stars live in `localStorage` under
each week's own `week` string, so switching back to an old test finds it exactly
as Kai left it, and "Start this week over" only clears the week on screen.

The app opens on the next test that hasn't happened yet; after that date passes
it stays on the latest one. Whichever week is picked by hand is remembered.
