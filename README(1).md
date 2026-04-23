# Interview Prep Tracker

A single-file, offline-first tracker for working through the **NeetCode 150 roadmap** alongside **system design** fundamentals. Built as one self-contained HTML file — no build step, no server, no dependencies.

![Topics](https://img.shields.io/badge/topics-18-534AB7) ![Problems](https://img.shields.io/badge/problems-141-1D9E75) ![License](https://img.shields.io/badge/license-MIT-888)

## What it is

18 topic pages that mirror the NeetCode roadmap dependency graph — from Arrays & Hashing at the top down through Math & Geometry. For each topic, you get:

- **🗺️ Concepts to Learn** — 5–7 foundational ideas per topic (Big-O, hash maps, monotonic stacks, Dijkstra, etc.) with checkboxes and a notes field
- **📝 Problems** — 5–11 curated LeetCode problems per topic, each linked to both the LeetCode problem page and the matching NeetCode video walkthrough
- **🏗️ System Design** — paired real-world design concepts (e.g. Arrays & Hashing pairs with latency/throughput, scaling, caching; Linked List pairs with REST, idempotency, retries, pagination)

Per-problem tracking includes status, 🟢/🟡/🔴 self-rating, confidence 1–5, time spent, checkboxes for *Timed / Can explain / Need redo*, and free-form notes.

## Why

Most LeetCode trackers are spreadsheets. Most roadmaps are static images. This combines the two — you work through the graph in whatever order makes sense, and the tracker remembers everything.

The system design pairing is the less-obvious part. Pairing *Heap / Priority Queue* with *message queues and backpressure*, or *Two Pointers* with *load balancers and CDNs*, keeps coding prep and design prep reinforcing each other instead of being two separate grinds.

## Usage

Just open `interview_prep_tracker.html` in a browser. That's it.

State is saved automatically to `window.storage` (or localStorage in a fork — see Customizing below) every 400ms. Progress persists across sessions.

### Navigation

- 18 colored dots at the top — click any topic
- ← / → arrows to walk through the roadmap in order
- Dots are color-coded by phase:
  - **Foundations** (purple) — Arrays & Hashing, Two Pointers, Stack
  - **Search & Scan** (green) — Binary Search, Sliding Window, Linked List
  - **Trees** (dark green) — Trees, Tries, Heap / Priority Queue
  - **Recursion & Graphs** (orange) — Backtracking, Graphs, Advanced Graphs
  - **DP & Optimization** (red-orange) — 1-D DP, 2-D DP, Intervals, Greedy
  - **Numerics** (gold) — Bit Manipulation, Math & Geometry

## Topic coverage

| # | Topic | Problems | Phase |
|---|-------|----------|-------|
| 1 | Arrays & Hashing | 9 | Foundations |
| 2 | Two Pointers | 5 | Foundations |
| 3 | Stack | 7 | Foundations |
| 4 | Binary Search | 7 | Search & Scan |
| 5 | Sliding Window | 6 | Search & Scan |
| 6 | Linked List | 10 | Search & Scan |
| 7 | Trees | 10 | Trees |
| 8 | Tries | 5 | Trees |
| 9 | Heap / Priority Queue | 7 | Trees |
| 10 | Backtracking | 9 | Recursion & Graphs |
| 11 | Graphs | 10 | Recursion & Graphs |
| 12 | Advanced Graphs | 6 | Recursion & Graphs |
| 13 | 1-D DP | 11 | DP & Optimization |
| 14 | 2-D DP | 10 | DP & Optimization |
| 15 | Intervals | 6 | DP & Optimization |
| 16 | Greedy | 8 | DP & Optimization |
| 17 | Bit Manipulation | 7 | Numerics |
| 18 | Math & Geometry | 8 | Numerics |

**Total: 141 problems** across the NeetCode 150 spine.

## Customizing

All content lives in the `TOPICS` array at the top of the `<script>` block. Each topic has the same shape:

```js
{
  id: 1,
  name: 'Arrays & Hashing',
  phase: 'Foundations',
  intro: 'Short description shown at the top of the topic page.',
  concepts: [
    { name: 'Big-O fundamentals', desc: 'Short description' },
    // ...
  ],
  problems: [
    { n: 217, name: 'Contains Duplicate', diff: 'E',
      lc: 'https://leetcode.com/...', nc: 'https://neetcode.io/...' },
    // ... diff is 'E' | 'M' | 'H'; add prem:1 for LeetCode Premium problems
  ],
  design: [
    { name: 'Latency vs throughput', desc: 'Short description' },
    // ...
  ],
}
```

Add a topic, drop a problem, rewrite an intro — changes take effect on refresh.

### Using localStorage instead of window.storage

The file uses `window.storage` which is provided by the Claude runtime. If you're hosting it standalone (GitHub Pages, file://, your own site), replace the two storage functions near the top of the script:

```js
// Replace this:
async function load(t){try{const r=await window.storage.get(KEY(t));return r?JSON.parse(r.value):null;}catch{return null;}}
async function save(t,v){try{await window.storage.set(KEY(t),JSON.stringify(v));}catch{}}

// With this:
async function load(t){try{const r=localStorage.getItem(KEY(t));return r?JSON.parse(r):null;}catch{return null;}}
async function save(t,v){try{localStorage.setItem(KEY(t),JSON.stringify(v));}catch{}}
```

That's the only change needed to run it anywhere.

## Tech notes

- Single HTML file, vanilla JS, no build step
- ~720px max width, mobile-friendly
- State saves on a 400ms debounce
- All LeetCode links go direct; NeetCode links point to the per-problem page with the embedded video
- A handful of problems (Replace Words, Design Search Autocomplete) don't have NeetCode videos — those show only the LeetCode button

## Credits

- Problem curation follows the [NeetCode 150](https://neetcode.io/practice) roadmap by Navdeep Singh
- System design concept pairing is original to this tracker

## License

MIT
