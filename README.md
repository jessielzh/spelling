# Spelling Practice

A single-file spelling trainer for a Grade 4 poetry vocabulary list.

The browser reads each word aloud and **never shows it**, so it's a real test
rather than a copying exercise — that's the part a paper worksheet can't do on
its own, because someone has to say the word out loud.

- **Test** — hear the word, type it. Wrong answers get letter-by-letter feedback
  (`rythm` → *"you missed the h"*) and must be retyped correctly before moving on.
- **Practice** — see the word with its syllable chunks and meaning, and copy it.
- A word counts as learned after two correct cold spellings; misses come back
  later in the same round.

## Running it

Open `index.html`. That's all — no build step, no server, and it works offline.
Speech uses the browser's built-in Web Speech API (best in Safari or Chrome).

## Using a different word list

Edit the `WORDS` array at the top of `index.html`:

```js
const WEEK = "Aug 28";
const WORDS = [
  { w:"rhythm", m:"the beat of a poem", c:"rhy·thm" },
  // w = word   m = short meaning   c = syllable chunks (optional)
];
```

Progress is stored in `localStorage` keyed by `WEEK`, so changing the week
starts a clean slate without touching the previous one.
