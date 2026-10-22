# Basic Vocab Test (Parts A & B)

Self-contained, offline HTML tools for HK high-school ESL students. Each part estimates mastery of high-frequency English (**Oxford 3000–style bands**) as **one number from 0 to 3000**.

| File | Task |
|------|------|
| `basic-vocab-test-part-a.html` | **Part A** — choose the **closest meaning** of the underlined word (canonical) |
| `basic-vocab-test-part-b.html` | **Part B** — choose the **opposite meaning** of the underlined word |
| `README.md` | This guide |

The old `oxford3000-vocab-estimate.html` name is retired; **Part A is the canonical closest-meaning test**.

No CDN, no server, no install. System fonts only. Parts share the same adaptive engine, UI rules, debug mode, and results sentence; only the item task and item banks differ.

## How to open (phone / laptop)

### Phone (recommended for class)

1. Copy the HTML file you need (`basic-vocab-test-part-a.html` and/or `basic-vocab-test-part-b.html`) to the phone (AirDrop, Drive, WhatsApp file, USB, LMS, etc.).
2. Open in a mobile browser (iPhone: Files → Safari; Android: Downloads → Chrome).
3. Stay on the page until the result screen. Nothing is uploaded.

Works **offline** after the file is on the device. “Hear” buttons need Web Speech API (`speechSynthesis`); if unavailable, hear controls are disabled and the test still works.

### Computer

Double-click the HTML file, or drag it into Chrome / Edge / Safari / Firefox.

## How students use it

1. Optional: enter **Name / ID**.
2. Tap **Start test**.
3. Answer questions (opening block of 8, then adaptive). Each item: underlined word → **closest** (Part A) or **opposite** (Part B) meaning; optional Hear buttons.
4. During the test: **Question N** + **time remaining** only.
5. **Results:** one sentence only — `The estimated score of {Name} at {HH:MM} on {D Mon YYYY} is {N} / 3000.` (Asia/Hong_Kong; Name defaults to “Student” if blank) — plus **New sitting**.

Teacher notes are behind a collapsed control on the start screen. Typical sitting: ~12–15 minutes. Hard caps: 20 minutes or ~100 items (including opening).

## Design summary (shared)

### Item format

- Situational sentence with **one underlined target word**.
- Part A prompt: **closest meaning**; Part B prompt: **opposite meaning**.
- Exactly **4** options, structure-matched (same word count). Prefer the clearest correct choice; distractors are parallel in form.
- **Hear sentence** + **Hear** per option when speech is available.

### Part A example (closest)

> After she opened her birthday present, she looked very <u>happy</u>.
>
> Choose the closest meaning of the underlined word.
>
> A. glad &nbsp; B. heavy &nbsp; C. hungry &nbsp; D. angry

### Part B example (opposite)

> The soup is too <u>hot</u> to eat right now.
>
> Choose the opposite meaning of the underlined word.
>
> A. cold &nbsp; B. loud &nbsp; C. tall &nbsp; D. soft

### Opening block (every sitting)

1. Draw **8** very easy Band-1 items from the opening pool (24 items).
2. Opening answers **count in the score** as Band 1.
3. Then apply the same band-move rules as every other block.

### Band moves (every block of 8)

- **≥7/8** → jump **+2** bands  
- **≥75% but &lt;7/8** (6/8) → **+1**  
- **40–74%** → stay  
- **&lt;40%** → **−1**  
- Progress UI: Question N + time remaining only (no band labels).

### Stop rules

- Do **not** stop for precision while **still climbing** (last move was up, or ≥75% on the highest visited band with a higher band available).
- Soft aim **~12–15 min** and soft item cap **~90** when not climbing; precision stop (ME ≤ ±150 and ≥3 blocks) only when not climbing.
- Hard stop: **20 min** or **~100 items**.
- **Final probe:** before a non-hard stop, if the highest visited band scored ≥75%, run one real block at the next higher band (if any). Impute only bands above that last real high-band probe.

### Scoring / imputation

- Visited bands: empirical correct rate.
- Unvisited easier bands: rate = 1.0.
- Skipped mid-bands (after a +2 jump): mastered (1.0) if surrounded by strong (≥75%) results; else interpolate.
- Unvisited harder bands (above last real probe): mild decay (×0.85 per step); if top rate &lt;0.40 → 0.0.
- Estimate = round(Σ (rate_b × 500)), clamped 0–3000.

### Item banks

| Part | Task | Main pool | Opening pool |
|------|------|-----------|--------------|
| A | Closest meaning | ≥50 items × 6 bands (300) | 24 Band-1 |
| B | Opposite meaning | ≥50 items × 6 bands (307) | 24 Band-1 |

### Hidden debug mode

If **Name / ID** is exactly `debug` (case-insensitive), a live stats panel appears (band, rates, estimate, climb/stop flags). For teachers/developers only.

## Classroom notes

- Part A and Part B can be used on different days or as a pair; scores are comparable in scale but are **not** the same items.
- Students should not see band labels or teacher notes during a sitting.
- Offline files travel easily; no accounts or uploads.
