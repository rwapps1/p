# My Parkrun Dashboard

A single-file, self-contained dashboard for tracking your parkrun history — best times, locations, distance, milestones, and more — with the ability to load a new spreadsheet and export everything as a PDF.

No installation, no server, no account. It's one HTML file that runs entirely in your browser.

---

## Opening the dashboard

Double-click **`parkrun-dashboard.html`**, or drag it into a browser window.

**Use a full browser** — Chrome, Safari, Firefox, or Edge. The dashboard loads a few small libraries (for charts, spreadsheet reading, and PDF export) from the internet the first time you open it, so:

- You'll need an internet connection when you open the file.
- **In-app/embedded browsers** (e.g. the built-in browser inside another app) may block downloads. If "Download as PDF" doesn't do anything there, open the file in a regular browser instead — this is a restriction of those embedded views, not the dashboard itself.

---

## What's on the dashboard

- **Hero stats** — total parkruns, total distance, total time run, locations visited, average time
- **All-time personal best** — your fastest time ever, where and when you ran it, and how long it's stood
- **Yearly Best Times** — a chart and table of your fastest time, run count, and distance for each year
- **Location Breakdown** — a chart and cards showing every course you've run, how many times, and your best there
- **Personal Best Timeline** — every run flagged as a PB in your sheet, in date order
- **Milestones** — progress toward the 50 / 100 / 250 / 500 / 1000 run clubs
- **More Stats** — first run, most recent run, most-visited course, fastest year, longest gap between runs, and PBs logged

All numbers are calculated live from whatever spreadsheet is currently loaded — nothing is hardcoded.

---

## Uploading a new sheet

Use the **"Upload a new sheet"** box at the top to replace the data with an updated spreadsheet (`.xlsx`, `.xls`, or `.csv`). The whole dashboard recalculates automatically — no page reload needed.

**Your sheet must only include four columns, in this order:**

| Location | Date | Race Time | Personal Best |
|---|---|---|---|

- **Location** — text, e.g. `Barnsley`
- **Date** — a real date value (or `YYYY-MM-DD` / `DD/MM/YYYY` text)
- **Race Time** — your finish time, e.g. `28:45` (mm:ss) or `1:02:10` (h:mm:ss)
- **Personal Best** — anything (e.g. `PB`) in this cell marks the run as a PB; leave it blank otherwise

A header row is optional — the dashboard detects and skips one if it's there.

> **Note on time formatting:** some spreadsheet tools store race times oddly if they're typed into a field expecting hours:minutes rather than minutes:seconds. The dashboard automatically detects and corrects for this, so times should come out right either way — but if a time ever looks obviously wrong after upload, double-check how that cell was entered.

---

## Downloading as PDF

The **"Download as PDF"** button captures the whole dashboard as a full-colour, landscape PDF:

- The upload/download controls themselves are left out of the PDF.
- Sections that scroll on screen (the yearly table and location cards) automatically expand to show everything in the PDF, however many years or locations you've got — no cut-off content, no matter how much your data grows.
- The file is compressed automatically (starting at high quality and stepping down only if needed) to keep the size manageable, and the final file size is shown once it's done.

---

## Notes

- Nothing is uploaded anywhere — all data and calculations stay in your browser.
- The dashboard doesn't save your upload for next time; it starts from the original data each time you open the file. Keep an updated copy of your spreadsheet if you want to reload it later.
- Built with [Chart.js](https://www.chartjs.org/), [SheetJS](https://sheetjs.com/), [html2canvas](https://html2canvas.hertzen.com/), and [jsPDF](https://github.com/parallax/jsPDF), loaded from a CDN on open.
