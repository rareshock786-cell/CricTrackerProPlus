🏏 CricTracker-ProPlus

CricTracker-ProPlus is a local-first cricket coaching, training and match tracker. It's a Progressive Web App (PWA) — meaning it runs in your browser, installs like a real app on your phone, tablet or computer, and keeps working even with no internet connection.

There is no server, no account in the cloud, and no monthly fee. Everything you enter lives on your own device.

What it does
Dashboard — a command-center overview of your cricket life: today's activity, recent sessions, active goals, weekly/monthly summaries, milestones, total runs and wickets, and a "No. of Days" counter.
Matches — record full match performances, split into four sections:
Venue — overs, location, date, result
Batting — runs, balls faced, fours, sixes
Bowling — overs bowled, economy, wickets, runs conceded, extras
Fielding — run-outs/stumpings, catches
Plus free-text match notes.
Training Tracker — log batting drills, bowling drills, and fitness sessions with duration, intensity, notes and a session rating.
Journal — a reflective log for training, match, fitness or general entries: what went well, what went wrong, what you learned, and your focus for next time. Includes search, a list view, and a calendar view.
Calendar — see training, matches, journal entries and goals laid out by day.
Goals & Settings — set Target Ratings (1–10) for Batting, Bowling, Fielding and Fitness, manage your appearance, your passcode, and your data backups.
Custom Appearance — a full color palette editor (hue, saturation, brightness, opacity, HEX/RGB/HSL, saved palettes, presets) so you can theme the app however you like, in light or dark mode.
Security — your data is protected by a personal passcode you set yourself, encrypted locally on your device with AES‑GCM. There's no "master password" and nobody but you can unlock it. Auto-lock and manual lock are both supported.
How your data is stored

CricTracker-ProPlus keeps your data in two places:

IndexedDB (your browser's built-in local database) — this is the main copy the app always reads and writes to. It works completely offline.
A JSON backup file (CricTracker-ProPlus.json) — an optional mirror of your data that you keep on your own computer, like a safety copy. This is entirely optional, but strongly recommended in case you ever clear your browser data or switch devices.

The app never uploads your data anywhere. There's no Google Drive sync, no Firebase, no cloud database.

🧒 Setting up Auto-Backup (the super-easy way)

This makes the app automatically save a backup copy of your data to a file on your computer every time you make a change — so you never have to remember to do it yourself.

You only need to do this once. After that, it just works in the background, like magic. ✨

Step 1 — Open Settings

Tap the Goals & Settings tab at the top of the app.

Step 2 — Find the Backup box

Scroll down until you see the box called 💾 Automatic JSON Backup.

Step 3 — Pick a spot for your backup file

Tap the button that says "Set ProPlus Data File".

Your browser will open a little window asking "Save As..." — just like saving a photo or a document.

Pick anywhere easy to remember, like your Desktop or Documents folder.
Don't change the file name — leave it as CricTracker-ProPlus.json.
Tap Save.
Step 4 — Say "Yes, allow it"

Your browser might pop up a small question asking if the app can save to that file. Tap Allow.

Step 5 — You're done! 🎉

That's it — no more steps! Look for the little dot next to the backup box:

🟢 Green dot = your backup is connected and working.
The text underneath will say "Last backup: [time]" so you always know it's up to date.

From now on, every time you add a match, a training session, or a journal entry, CricTracker-ProPlus quietly saves a fresh copy into that file for you — automatically, within a couple of seconds. You never have to click anything again.

Already have a backup file from before?

If you're setting this up on a new device (or reinstalled the browser) and you already have a CricTracker-ProPlus.json file saved somewhere, tap "Use Existing JSON" instead of "Set ProPlus Data File," then pick that file. This connects the app to your existing backup instead of starting a new one.

A few friendly notes
The "Backup Now" button is just an emergency manual button — you normally never need to press it, since backups happen automatically.
The "Restore File" button lets you load your data back in from the backup file (handy if you ever get a new device).
The "Disconnect" button stops the automatic saving, if you ever want to turn it off.
If your browser doesn't support this feature (some browsers don't), the app will tell you and you can use the Export/Import buttons instead — same idea, just one extra click each time.
Your data on the device itself is always safe either way — the automatic file is just an extra safety copy.
Technical notes (for developers / advanced users)
Storage backend: IndexedDB is primary; falls back to localStorage automatically if IndexedDB is unavailable.
Backup file: Uses the browser's File System Access API (showSaveFilePicker / showOpenFilePicker) to keep read/write access to a chosen local file. The file handle is remembered in IndexedDB so the connection survives a page refresh, as long as the browser still grants permission.
Sync behavior: Writes are debounced (~1.5 seconds after the last change) to avoid excessive disk writes. A failed backup write never rolls back or touches your IndexedDB data — your working data always stays safe.
Encryption: The backup JSON is encrypted with AES-GCM using a key derived from your passcode. It is unreadable without your passcode.
Hosting: Deployed via GitHub Pages. GitHub Pages hosts the static app files only — it cannot write back to your local backup file. All read/write backup activity happens directly between your browser and your own computer's file system.
PWA / offline support: A service worker (sw.js) caches the app shell so it keeps working with no internet connection. The cache version is bumped whenever app assets change, so users automatically get the latest version after their next visit.
