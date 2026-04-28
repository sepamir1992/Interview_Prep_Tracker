# Interview Prep Tracker

A local, single-file interview preparation tracker for the NeetCode-style roadmap. It helps you track concepts, coding problems, system design notes, review items, streaks, time spent, and overall progress without needing an account, backend, or installation.

## What Is Included

This folder contains:

- `interview_prep_tracker.html`: the complete tracker app.
- `LICENSE`: the project license.
- `.gitignore`: Git ignore rules for the project.

The tracker is built as one HTML file. The styling, roadmap data, and app logic are all inside `interview_prep_tracker.html`.

## License And Attribution

This project is released under the MIT License.

You may use, copy, modify, and share this tracker, but the copyright notice and license must stay with the project.

Credit:

```text
Interview Prep Tracker by Amir
Copyright (c) 2026 Amir
```

## Quick Start

1. Open the `Interview_Prep_Tracker` folder.
2. Double-click `interview_prep_tracker.html`.
3. Your browser should open the tracker.
4. Start on the `Today` tab or open `Roadmap` to begin with the first topic.

No build step is required. You do not need Node.js, npm, Python, or a database.

## Optional: Run With A Local Server

Opening the HTML file directly is usually enough. If you prefer using a local web server, open a terminal in this folder and run one of these:

```powershell
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/interview_prep_tracker.html
```

This is optional. The app is designed to work as a local file.

## What The Tracker Covers

The built-in roadmap has:

- 18 roadmap topics
- 141 coding problems
- 100 core concepts
- 72 system design study items

The topics are grouped into phases:

- Foundations
- Search & Scan
- Trees
- Recursion & Graphs
- DP & Optimization
- Numerics

Each topic includes:

- Concepts to learn
- LeetCode and NeetCode problem links
- Difficulty labels: `E`, `M`, `H`
- Status tracking
- Confidence tracking
- Time logging
- Problem notes
- Related system design concepts

## Main Tabs

### Today

The `Today` tab is the dashboard. It shows:

- A short greeting based on your progress
- Your current streak
- The number of items touched today
- Total solved problems
- Problems due for review
- A 12-week activity heatmap
- A card to continue your last topic

Use this tab when you want to know what to work on next.

### Roadmap

The `Roadmap` tab is where most study work happens.

At the top, you will see topic dots grouped by phase. Click a topic number to jump to that topic.

Inside each topic, you can:

- Check off concepts as you learn them
- Open problem cards
- Visit LeetCode or NeetCode links
- Set problem status
- Mark your confidence from 1 to 5
- Log time spent in minutes
- Mark whether you solved it timed
- Mark whether you can explain the solution
- Mark whether it needs a redo
- Add notes for the problem, concepts, or design items
- Track related system design items

Problem statuses are:

- `Not Started`
- `In Progress`
- `Solved with Hints`
- `Solved Cleanly`
- `Review Needed`

The clean solved count is based on `Solved Cleanly`.

### Stats

The `Stats` tab gives a full progress summary:

- Roadmap solved percentage
- Attempted percentage
- Total time logged
- Concepts completed
- System design progress
- Mastery matrix by topic
- Difficulty distribution
- Search across your notes

Clicking a topic row in the mastery matrix jumps back to that topic.

## Review Queue

The tracker has a simple spaced-review system.

A problem can appear in the review queue when:

- You mark it as `Review Needed`
- You mark it red or shaky
- You check `Need redo`
- You solved it cleanly and enough time has passed based on confidence

Confidence affects review timing:

- Confidence 1: review after about 1 day
- Confidence 2: review after about 2 days
- Confidence 3: review after about 4 days
- Confidence 4: review after about 14 days
- Confidence 5: review after about 30 days

Higher confidence means the tracker waits longer before asking you to revisit the problem.

## Data Storage

Your progress is saved in your browser on your own computer.

The app uses browser storage:

- In normal local browser use, it saves to `localStorage`.
- In supported hosted/artifact environments, it can use `window.storage`.

There is no backend server and no cloud sync.

Important things to know:

- Progress is tied to the browser/profile you use.
- A different browser may not see the same progress.
- Clearing browser site data can delete your tracker progress.
- Moving the HTML file may affect how some browsers treat local storage.
- Export your data before clearing browser data, switching browsers, or moving machines.

## Export And Import

Use the top-right buttons in the tracker:

- The down-arrow button exports your progress as a JSON file.
- The up-arrow button imports a previously exported JSON file.
- The moon/sun button toggles light and dark mode.

Export regularly if the tracker matters to you. The export file contains your saved progress, notes, statuses, activity, and theme setting.

## Recommended Local Workflow

1. Open `interview_prep_tracker.html` in your usual browser.
2. Start with `Roadmap`.
3. Work through one topic at a time.
4. For each problem, set a status and confidence score.
5. Add short notes about the key idea or mistake.
6. Check `Can explain` only when you can explain the solution out loud.
7. Use `Today` at the start of each session to handle review items.
8. Use `Stats` once in a while to find weak topics.
9. Export your data regularly.

## Troubleshooting

### The page opens but looks plain

The app uses Google Fonts. If you are offline or the fonts are blocked, the tracker still works, but the typography may look different.

### My progress disappeared

Check that you are using the same browser and browser profile as before. If you recently cleared site data, local progress may have been removed. Import your latest exported JSON file if you have one.

### The import failed

Make sure you selected a JSON file exported by this tracker. If the file was edited manually and the JSON is invalid, the import will fail.

### I want to use it on another computer

Export your progress from the old computer, copy the JSON file to the new computer, open the tracker there, and import the JSON.

### I want a backup

Use export and store the JSON somewhere safe, such as a backup folder or cloud drive.

## Editing The Tracker

If you want to customize the roadmap, edit `interview_prep_tracker.html`.

The main roadmap data lives in the `TOPICS` constant inside the script section. Each topic has:

- `id`
- `name`
- `phase`
- `intro`
- `concepts`
- `problems`
- `design`

After changing the roadmap, refresh the browser. Existing saved progress is merged with the default topic state when the app loads.

If you add or remove topics, also check navigation logic that assumes the current topic range.

## Privacy

The tracker runs locally in your browser. Your notes and progress are not sent to a server by this app.

External links and resources may contact third-party services when used:

- Google Fonts may load fonts from Google.
- LeetCode links open LeetCode.
- NeetCode links open NeetCode.

## File To Open

Open this file in your browser:

```text
Interview_Prep_Tracker/interview_prep_tracker.html
```
