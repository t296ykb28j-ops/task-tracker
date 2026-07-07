# Life Tracker

A small PWA that plans your week around your goals. You define a pool of goals ("Guitar — 1 hour a day", "Reading — 2 hours a week"), set your waking hours and work hours, and it generates a weekly schedule in the free time that's left. Tap blocks to check them off; each goal shows weekly progress.

Everything runs in the browser — no server, no account. Data is saved in the browser's local storage on your device.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML + CSS + JS) |
| `manifest.json` | PWA manifest (name, icons, standalone display) |
| `sw.js` | Service worker — makes the app work offline |
| `icon-512.png`, `icon-192.png`, `icon-180.png` | App icons (180 is the iOS home-screen icon) |

## Deploy on GitHub Pages

1. Create a new **public** repository on GitHub (any name, e.g. `life-tracker`).
2. Upload all the files above to the **root** of the repo (Add file → Upload files works fine).
3. In the repo: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `(root)` → Save**.
4. Wait a minute, then open `https://<your-username>.github.io/<repo-name>/` on your phone.

GitHub Pages serves over HTTPS, which is required for PWAs — nothing extra to configure.

## Add to home screen

- **iPhone (Safari):** open the URL → Share button → **Add to Home Screen**.
- **Android (Chrome):** open the URL → ⋮ menu → **Add to Home screen** (or the "Install app" prompt).

It launches full-screen like a native app. After the first visit it also works offline.

## Using the app

1. **Setup tab** — set wake time, sleep time, work start/end, and which days you work. Optionally a break length between scheduled sessions.
2. **Goals tab** — add goals. Each has a time devotion (X minutes/hours, per day or per week), a max single-session length (long goals get split), and a color.
3. **Schedule tab** — tap **Generate this week**. Daily goals land on every day; weekly goals get split into sessions and spread across the roomiest days. Tap a block to mark it done. If your goals don't fit in your free hours, a banner tells you what was left over.

Regenerate any time — e.g. at the start of each week (regenerating resets that week's checkmarks).

## Notes

- Data lives only on the device/browser where you use it (no sync between phone and laptop).
- To ship an update, edit the files in the repo and bump the `CACHE` version string in `sw.js` (e.g. `life-tracker-v2`) so installed apps pick it up.
- Sleep times past midnight (e.g. wake 07:00, sleep 00:30) are handled — the day just extends past 12 AM.
