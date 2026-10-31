# Astera Studio mockup

A chat-first analytics tool with pipeline monitoring and light editing on phone, tablet and desktop. Built by Abdul Saboor (FAST-NUCES, batch 2027) for the Astera Software internship assessment.

All data is made up. It is a fictional company, Northwind Retail, and there is no backend.

## How to open

- **Locally:** unzip the folder and double-click `index.html`. It works offline, with no install and no server.
- **Live link:** https://astera-studio-1.vercel.app/
- **Seeing the responsive layouts:** resize the browser window, or use your browser's device mode, at 375, 768, 1024 and 1440 pixels wide.

## Try this (about two minutes)

1. **Chat:** tap the first suggested question, "Which regions missed their Q3 target?". Notice the "Stale" tag: the pipeline behind this answer has failed.
2. **Pin and dashboard:** pin the chart, then open **Dashboard** to see it under the pinned charts, next to the KPIs, the freshness strip and the pipeline status.
3. **Failed pipeline:** open **Regional Targets** from the Pipelines list. Find the failed Join step and use **Re-run from this step**. Watch the steps change one by one, the stale tags disappear, and Target attainment move from 94% to 92%.
4. **Filters and drill-down:** change the date range or region on the dashboard, then tap a bar in the regional chart to drill down.
5. **Phone layout:** shrink the window to phone width and open a pipeline. You get a vertical step timeline with a jump strip at the top. Tap a step to open it, change a value, and try Preview, Apply and Undo.

## How the layout adapts

| | Phone (under 640px) | Tablet (640 to 1099px) | Desktop (1100px and up) |
|---|---|---|---|
| **Navigation** | Bottom tab bar | Slim left rail | Full left sidebar with the pipeline list |
| **Dashboard** | One column, swipeable KPI row, filters in a bottom sheet | KPI row of four, charts in two columns | KPI row and a wider chart grid, inline filter chips |
| **Pipeline detail** | Vertical step timeline, jump strip, step opens in a bottom sheet | Canvas with an inspector panel on the right, and a List and Canvas toggle | Canvas, inspector panel, and a data preview table |
| **Editing** | Safe edits only | Safe edits only | Safe edits, plus the Add step menu |

## Design decisions

- **Timeline instead of canvas on phones.** Steps read top to bottom, each with a description, status and rows in → rows out. Dragging boxes and wires is hard with fingers, so the phone doesn't ask for it.
- **Safe edits on touch.** Change a value, toggle or rename a step, change the schedule, move a step, or re-run. Adding or rewiring steps is desktop-only, and the screen says so.
- **Draft, Preview, Apply, Undo.** No edit changes a pipeline directly. You see the effect first and can always undo.
- **Provenance and freshness.** Every chart shows which pipeline feeds it, its status, and how fresh the data is.
- **Failure as a designed state.** The failed step, a plain-language reason, and a re-run button, with stale tags on everything it feeds.
- **No colour-only meaning.** Status is always an icon plus text.

## Folder structure

```
index.html
css/styles.css
js/data.js        mock data
js/charts.js      Chart.js helpers
js/pipeline.js    pipeline views, inspector, draft logic
js/app.js         router, state, dashboard, chat, shared UI
fonts/            bundled fonts
logo/             Astera logo files
vendor/           Chart.js (local copy)
README.md
NOTE.md
```

## Tech notes

- Vanilla HTML, CSS and JavaScript. No framework and no build step.
- Classic `<script>` tags, so it opens straight from a zip.
- Chart.js is bundled in `vendor/`. Fonts and logos are local, so there are no external requests.
- Hash routing: `#/chat`, `#/dashboard`, `#/pipelines`, `#/pipeline/<id>`.
- Light and dark themes follow the system setting, and motion respects the reduced-motion setting.
- Pinned charts are remembered in `localStorage`, and the app still works if storage is blocked.

## Known limitations

- All data is made up, and chat answers are scripted keyword matches, not a real model.
- Structural editing (adding or rewiring steps) is a stub.
- The data preview on desktop shows illustrative sample rows, not a full output.
- Everything resets on refresh, apart from pinned charts.

## Credits

Astera's colours, type style and logos are used as a visual reference from the public Astera website, for this assessment only. AI tools helped write parts of the code. The details are in `NOTE.md`.
