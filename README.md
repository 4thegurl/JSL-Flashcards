# JSL Flashcards

Japanese study flashcards with a furigana toggle. Runs in any browser, installs to your phone's home screen, and works offline once loaded. Data lives in `decks.json` — the app just reads it.

## One-time setup (GitHub Pages)

1. Make a new repo (public), e.g. `jsl-flashcards`.
2. Add these files to it: `index.html`, `decks.json`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`.
3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pick `main` / `root`, Save.
4. Wait ~1 min. Your app is live at `https://<your-username>.github.io/jsl-flashcards/`.

## On your phone

- Open the Pages URL in Safari (iOS) or Chrome (Android).
- **Add to Home Screen** → it installs with the 学 seal icon and opens full-screen like a native app.
- Load it once on wifi; after that it works with no signal (trains, planes).

## Adding cards (works from phone too)

1. Ask for a breakdown as usual — you'll get a ready-to-paste card object.
2. On GitHub, open `decks.json` → pencil (Edit) icon.
3. Paste the new object into the `cards` array (mind the comma between objects).
4. Commit. Live everywhere in a few seconds.

Card format:

```json
{"jp": "乗り換える", "furigana": "のりかえる", "en": "to transfer (trains)", "deck": "Verbs"}
```

- `deck` groups cards into tabs. Current decks: Grammar, Vocab, Verbs, Expressions, Keigo. A new `deck` value automatically creates a new tab.
- `furigana` shows under the Japanese and toggles with the あ button. If a card has no kanji, set `furigana` equal to `jp` (or leave it) and nothing extra shows.

## Controls

- **Tap card** — flip. **Swipe** left/right — next/previous.
- **あ** — show/hide furigana. **⇄** — shuffle the current deck.
- Keyboard: `Space` flip, `←/→` navigate, `F` furigana, `S` shuffle.

## Updating the app itself

If you edit `index.html` or icons, bump the `CACHE` version in `sw.js` (e.g. `jsl-v1` → `jsl-v2`) so phones pull the new version instead of the cached one. Editing only `decks.json` needs no bump — it's fetched fresh each load.

## Local preview (optional)

Opening `index.html` by double-click won't work — browsers block `fetch` on `file://`. Use VS Code's Live Server, or `python -m http.server` in the folder, then visit `localhost:8000`.
