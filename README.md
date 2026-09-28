<!-- Replace with your final logo once exported: <p align="center"><img src="assets/logo.png" width="120" alt="logo"></p> -->

# Touch Assay Timer

**An offline, browser-based timer and data logger for *C. elegans* gentle touch assays.**

**[Open the app → (https://dv-welp.github.io/touch-assay-timer/)**
Works in any browser. On a phone, use "Add to Home Screen" to install it like an app.

## Why this exists

The gentle touch assay is usually run by hand: a separate timer app, a cell counter for responses, a paper notebook, then manual entry into a spreadsheet before any plotting or statistics. This tool handles the acquisition, logging, and organisation steps. You perform the assay; the app times the stimuli, records each response, and exports plot-ready tables.

<!-- Optional: add your before/after workflow figure here (assets/workflow.png) -->

<p align="center">
  <img src="assets/01-setup.jpg" width="19%" alt="Assay setup">
  <img src="assets/02-timer.jpg" width="19%" alt="Timer">
  <img src="assets/03-tap.jpg" width="19%" alt="Recording taps">
  <img src="assets/04-export.jpg" width="19%" alt="Export">
  <img src="assets/05-saved-assays.jpg" width="19%" alt="Saved assays">
</p>
<p align="center"><sub>Setup · Timer · Tap · Export · Saved assays</sub></p>

## How it works

1. **Set up** your assay: genotypes, ISI, number of stimulations, and bin size.
2. **Select a genotype** and press **Start Timer**. The app emits a cue for each stimulus interval (ticks, voice, or a mix of both; see Settings).
3. **Tap** when the animal does not respond. No tap within the interval is recorded as a response (1); a tap is recorded as no response (0).
4. Press Start Timer again for the next animal. There is no cap on animals per sitting, and you can switch genotypes freely.
5. **Finish the trial** (one sitting), then **export** to Excel. Come back any time to start a new trial, re-export, or delete.

Each animal is one *run* and each sitting is one *trial*. The in-app instructions explain how assays, trials and runs fit together.

Runs with fewer recorded values than the total stimulation count are marked ineligible for analysis, which is useful for discarding animals that leave the field.

## Export

One `.xlsx` workbook per export, with separate sheets for each trial's **raw data** and **analysed data**, plus **pooled** sheets across trials.

- **Raw:** everything recorded, always preserved.
- **Analysed:** binned responses with mean and SEM, ready to paste into Origin, Prism, Excel, or R.
- **Pooled:** the same analysis across multiple trials (completed trials only by default; abandoned trials can be included optionally).

<p align="center">
  <img src="assets/export-raw.png" width="32%" alt="Raw sheet">
  <img src="assets/export-analysed.png" width="32%" alt="Analysed sheet">
  <img src="assets/export-pooled.png" width="32%" alt="Pooled sheet">
</p>

## Built to be trusted

- **Crash-safe:** data is saved to IndexedDB after every interval, asynchronously so it never interferes with a running assay. Trials interrupted without being finished are kept as *abandoned* trials.
- **Read-only raw data:** once recorded, raw data is never modified.
- **Explicit analysis rules:** anything excluded from analysis (ineligible runs, abandoned trials, a partial final bin) is flagged and visible, and you choose whether to include it.
- **Offline:** no internet connection needed after the first load, and data stays on your device.

## Tech

Vanilla HTML, CSS and JavaScript. Progressive web app (service worker + manifest). IndexedDB for storage. No backend, no accounts, no tracking.

## Roadmap

- Version 2.0: plotting and statistical analysis (R/Python)
- Suggestions and issues are welcome via the Issues tab.

## Running locally

```bash
git clone https://github.com/dv-welp/touch-assay-timer.git
cd touch-assay-timer
python3 -m http.server 8000   # then open http://localhost:8000
```

## License

MIT. See [LICENSE](LICENSE).

## Author

Devyani Vadawale
