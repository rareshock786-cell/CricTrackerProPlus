# CricTracker-ProPlus

Local-first cricket coaching and match tracker PWA.

## Included fixes in this build
- Target Rating Goals restored in Goals & Settings.
- Add Match is divided into Venue, Batting, Bowling and Fielding sections.
- Dashboard + Match opens the Matches tab and the Match Record form.
- Matches remain dashboard-only as the "Matches Record" panel.
- Old V2 Activity & Performance analytics card is removed.
- Service-worker cache bumped to v5 so the new UI is picked up after deployment.

## Match fields
Venue: No. of Overs, Location, Date, Result.
Batting: Runs, Ball Faced, Fours, Sixes.
Bowling: Overs Bowled, Economy, Wickets Taken, Runs Conceded, Extras Given.
Fielding: Run-out/Stumping, Catches.

## Storage
IndexedDB is the primary local store. CricTracker-ProPlus.json is a local read/write mirror when the user explicitly selects a file using the File System Access API. GitHub Pages hosts the application; it does not directly write back to the repository.
