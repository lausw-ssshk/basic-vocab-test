# Item Quality Review — Vocab-Size Tests (Closest / Opposite)

**Reviewer role:** Language-tester quality review (not a full rewrite)  
**Scope:** `closest-meaning-test.html` ITEM_BANK (300) + WARMUP_BANK (24); `opposite-meaning-test.html` ITEM_BANK (307) + WARMUP_BANK (24)  
**Context:** HK Form 1–6 ESL; Oxford 3000-ish bands; adaptive size estimate; prefer short unambiguous options; large randomised pool  
**Date:** 23 Oct 2026 (Asia/Hong_Kong)

---

## 1. Executive summary

Overall quality is **usable for pilot / classroom estimation, not yet bank-stable for high-stakes or published norms**. Closest Meaning is the stronger of the two: structure-matched options, no scored/warmup target overlap, and most keys are clearly best for the intended sense. Opposite Meaning is weaker: antonym keys are often only loosely opposite, and **~80% of scored items leak a construct-irrelevant cue** (all three distractors share the target’s initial letter while the keyed antonym does not). Both banks show factory-style distractor templates (especially Opposite bands 5–6), some exact cross-band duplicates, and a handful of broken or ungrammatical options. **A full rewrite is not needed**; prioritise targeted antonym re-keys, break the initial-letter cue pattern, dedupe, and fix the small set of critical defects listed below.

---

## 2. Counts checked + automated findings

| Check | Closest (300 + 24) | Opposite (307 + 24) |
|---|---|---|
| Items / warm-ups parsed | 300 / 24 | 307 / 24 |
| Bands 1–6 counts | 50 each | 53 / 52 / 50 / 52 / 50 / 50 |
| `options.length === 4` | Pass (all) | Pass (all) |
| `correct` in range | Pass (all = 0; runtime shuffles) | Pass (all = 0; runtime shuffles) |
| `{target}` brace present | Pass (all) | Pass (all) |
| Brace case ≠ `target` | 14 sentence-initial caps only (OK if UI lowercases) | 16 sentence-initial caps only |
| Duplicate targets (scored) | **3 pairs** | **8 pairs** (incl. same-band estimate×2) |
| Exact same sentence+target | 1 pair (`impose`) | 2 pairs (`contribute`, `estimate`) |
| Identical options within item | 0 | 0 |
| Near-identical option pairs (edit ≤2) | 26 (mostly intentional form traps) | 98 (mostly intentional form traps) |
| Structure mismatch (phrase key vs word distractors) | **0** (all 300 WC-matched) | N/A (almost all single-word) |
| Correct much longer/shorter (auto length) | Few mild outliers | **9+** clear imbalances |
| Warm-up ∩ scored targets | **0** (good) | **24/24** (by design; note risk) |
| Spelling/typos (automated scan) | 1 clear grammar error + 1 truncated option | No spelling crashes found |
| Correct-position in source file | Always index 0 (OK — `prepareItem` shuffles) | Same |

### Automated finding notes

- **Runtime shuffle confirmed** in both HTML files (`prepareItem` shuffles option order). Source `correct: 0` is not a bias in live sittings.
- **Near-identical options** are mostly phonological/orthographic distractors (e.g. hungry/angry). Flagged for human review of *fairness*, not as bank corruption.
- **Opposite warm-up overlap:** every warm-up target also appears in band 1 scored. Acceptable for “opening block,” but students who remember warm-up keys get free points on the same lemmas later in the adaptive climb — mild contamination if warm-up is scored or if reuse is visible.

---

## 3. Weakness categories (by severity)

### CRITICAL

#### C1. Opposite: initial-letter cue makes the key stand out (~250/307)

In ~250 Opposite items, **all three distractors share the target’s first letter, and the keyed antonym does not**. Students can adopt “pick the odd-initial word” without knowing meaning. Prevalence is extreme in bands 2–6.

**Examples:**  
`b2_001` important → unimportant vs impossible/immediate/independent  
`b2_009` comfortable → uncomfortable vs careful/common/complete  
`b3_015` survive → die vs support/suggest/succeed  
`b4_015` justify → invalidate vs judge/join/jump  
`b4_031` substantial → tiny vs subsequent/sufficient/suitable  
`b5_044` disrupt → aid vs discuss/display/distribute  
`b6_025` exaggerate → understate vs equip/escape/erode  
`b6_033` exploit → support vs equip/escape/erode  
`b6_041` formulate → discard vs equip/escape/erode  
`b1_029` loud → quiet vs quick/queen/quote  

**Fix hint:** For each item, make **at least one distractor** (ideally 1–2) an attractive *semantic* near-miss that does **not** share the target initial; or give the key the same initial when a fair antonym exists (e.g. loud→low is weak, but quiet can sit beside queer/quilt-style only if one distractor breaks the pattern). Goal: key cannot be found by letter alone.

#### C2. Opposite: keyed “antonym” is not a true opposite (key validity)

Several keys are weak, category errors, or wrong.

| ID | Target → keyed | Problem | Fix hint |
|---|---|---|---|
| `b4_009` | derive → **depart** | Not an antonym | Use *originate elsewhere* sense carefully, or *lose connection with* / *be unrelated to* — better: retarget item or key **originate independently** / **have no origin in** (or drop) |
| `b3_041` | attitude → **hostility** | Hostility *is* an attitude | Key **apathy** / **indifference**, or change target |
| `b3_047` | perspective → **bias** | Bias is a kind of perspective, not opposite | Key **blind spot** / **one-sidedness** is still weak — prefer **narrow view** or retarget |
| `b3_045` | impact → **insignificance** | Awkward; tests “significance” not “impact”; length giveaway | Key **negligible effect** / **none** — or target **significant** |
| `b4_018` | dimension → **void** | Not a clear antonym | Retarget or key **aspectlessness** (bad) — better rewrite stem |
| `b4_023` | proportion → **minority** | Category mismatch (amount vs group) | Key **imbalance** carefully, or **disproportion** |
| `b4_017` | criterion → **exception** | Loose | Key **non-factor** / rewrite |
| `b3_025` | assume → **verify** | Verify ≠ opposite of assume (can assume then verify) | Key **question** / **doubt** / **check before accepting** |
| `b4_043` / `b4_044` | estimate → measure / count | Measuring/counting are related methods, not opposites; **duplicate stem** | One item only; opposite of estimate is hard — consider **know exactly** / **measure precisely** with care |
| `b5_040` | discriminate → **treat** | Incomplete/odd (treat equally?) | Key **treat equally** / **include fairly** as full phrase |
| `b6_029` | exemplify → **contradict** | Weak | Key **misrepresent** / **counterexample needed** — or **obscure** |
| `b6_033` | exploit → **support** | Weak/indirect | Key **protect** / **fairly reward** / **refrain from using** |
| `b2_037` | describe → **hide** | Hide ≠ antonym of describe | Key **omit** / **leave undescribed** / **conceal** with better stem |
| `b3_024` / `b3_033` / `b6_022` | analyse/evaluate → **ignore** | Default “ignore” antonym overused; weak | Prefer **overlook** / **neglect to assess** / **guess without analysis** |

#### C3. Broken / ungrammatical options (Closest)

| ID | Issue | Fix hint |
|---|---|---|
| Closest warm-up `op_020` | Distractor **"a dark"** (truncated) | Finish phrase (e.g. *a dark room*) or replace (*a tablet* / *a cable*) matching structure |
| Closest `b6_261` | Distractor **"be a short explain"** (POS/grammar error) | *be a short explanation* / *be a brief explanation* |
| Closest `b4_179` | Key **"basic and so essential"**; distractor **"frequent in the happening"** (non-English) | Shorten key to *basic / essential*; rewrite distractors as real phrases |
| Closest `b5_234` | **"take in to"** / **"blame him for"** (broken parallelism / odd pronoun) | Align particles; drop *him* |

---

### MAJOR

#### M1. Opposite: recycled distractor templates (factory items)

Same three distractors reused across many lemmas → items feel cloned; once student sees the pattern, later items in the sitting are easier for the wrong reason.

| Distractor triple | Count | Example IDs |
|---|---|---|
| equip \| erode \| escape | **28** | `b6_021`–`b6_048` (establish…hinder stretch) |
| discuss \| display \| distribute | **9** | `b5_038`, `b5_040`–`b5_046`, `b5_049` |
| encounter \| encourage \| endure | **6** | `b6_008`–`b6_013` |
| equip \| escape \| establish | **4** | `b6_017`–`b6_020` |
| consist \| consult \| consume | **3** | `b5_019`–`b5_021` |

**Fix hint:** Unique semantic near-misses per item; allow form traps but rotate letters and meanings.

#### M2. Duplicate / near-duplicate lemmas across bands

**Closest:**  
- `impose` `b4_198` = `b6_262` (same sentence + key)  
- `accumulate` `b5_233` ≈ `b6_288` (same key *pile up*)  
- `advocate` `b5_202` ≈ `b6_291` (same key family)

**Opposite:**  
- `contribute` `b3_029` = `b5_025` (identical sentence)  
- `estimate` `b4_043` + `b4_044` (same sentence, different keys)  
- `public` `b2_051` / `b4_052`; `expand` `b3_006` / `b6_032`; `establish` `b3_032` / `b6_021`; `evaluate` `b3_033` / `b6_022`; `enhance` `b4_011` / `b6_012`; `exclude` `b4_038` / `b6_027`

**Fix hint:** Keep one band placement; replace the other with a new lemma. Never two keys for the same stem unless senses differ clearly.

#### M3. Opposite: key rarer / harder than the target (band misfit)

Keyed antonym harder than target → item measures the option, not the target.

**Examples:** `b2_041` require → **waive** (waive ≫ band 2); `b3_038` persuade → **dissuade**; `b3_039` recognise → **misidentify**; `b3_048` strategy → **improvisation**; `b5_027` conventional → **unorthodox**; `b6_013` enrich → **impoverish**; `b6_026` exceed → **undershoot** (also slightly odd).

**Fix hint:** Prefer high-frequency antonyms (*need → not need / do without*; *persuade → discourage*; *exceed → fall short*).

#### M4. Opposite: length / morphology giveaways

Un-prefixed or long abstract keys vs short same-letter distractors (or reverse).

**Examples:** `b2_004` available → **unavailable** vs able/active/aware; `b3_045` impact → **insignificance**; `b4_015` justify → **invalidate**; `b6_025` exaggerate → **understate**.

**Fix hint:** Match syllable/length roughly; use phrasal antonyms of similar length when needed (*not available*, *make invalid*).

#### M5. Closest: sentence over-support (giveaway overlap with key)

Content words from the key already appear in the stem.

**Examples:**  
`b2_065` information → *useful facts* (stem has *useful*)  
`b2_067` environment → *natural surroundings* (stem has *natural*)  
`b4_165` justify → *give good reasons* (stem has *reasons*)  
`b4_169` hypothesis → *idea to be tested* (stem has *tested*)  
`b4_199` occupy → *take up space* (stem has *space*)  
`b5_249` conform → *follow the rules* (stem has *rules*)  
`b6_255` constrain → *limit or restrict* (stem has *Limited*)  
`b6_276` resilience → *ability to recover* (stem has *recover*)

**Fix hint:** Rewrite stem to remove the synonym/definition word, or shorten the key so it doesn’t echo the stem.

#### M6. Closest: padded / non-natural distractor English

Filler *now* / *fully* / *well* used to force word-count match (~20 items), producing unnatural glosses.

**Examples:** `b2_074`, `b2_075`, `b2_095`, `b3_109`, `b3_117`, `b4_179` (*frequent in the happening*), `b5_250` (*confirm well for*).

**Fix hint:** Prefer real short phrases; matching structure matters more than exact token count. Author preference already allows multi-word answers — use natural ones.

#### M7. Closest band 1: many definitional keys + absurd distractors

33/50 band-1 keys are multi-word definitions (*close companion*, *put in writing*). Fine for easy warm discrimination, but:

- Keys are often **harder English than the target** (*notice with eyes* for *see*).
- Distractors are often absurd category jumps (*friend* → kitchen fridge), so item barely tests meaning nuance.

**Examples:** `b1_005`, `b1_009`, `b1_017`, `b1_041`, `b1_042`; weak synonym `b1_025` good → **fine** (fine ≠ clearly “good idea”).

**Fix hint:** For true band-1 synonyms use *glad/large/little/quick*; reserve definitional format for opaque abstract words in higher bands. Replace *fine* with *nice* / *excellent* / *positive* as fits stem.

---

### MINOR

#### m1. Format bleed / overused “ignore / hide / quit” antonyms (Opposite)

Many verbs keyed to *ignore*, *hide*, *quit*, *keep* regardless of best opposite (`b3_012` report→hide, `b3_009` replace→keep, `b4_005` commit→quit, `b4_041` endure→quit, `b4_002` anticipate→miss).

#### m2. Closest morphological “joke” distractors

`b6_266` undermine → *mark under the line* is a classic trap; fair if band 6, but pair with better semantic distractors than *go through an operation*.

#### m3. Closest `b6_282` thereby

Key *by that means* vs distractor *for that reason* (therefore) — actually a **good** discrimination item; keep. Listed only so it isn’t “fixed” wrongly.

#### m4. Opposite warm-up = band-1 scored lemmas (all 24)

Not wrong for practice, but if warm-up is scored toward the estimate, or if the same lemma reappears soon after, reliability inflates. Prefer warm-up-only ultra-basics that never re-enter the scored pool (Closest already does this).

#### m5. Cultural / HK fit

Generally good (ferry, PE, bullying report, library, MTR-adjacent school life). No major cultural fails spotted in the systematic sample. Minor: a few Western-leaning stems (*Easter* in `b2_051` Closest) — acceptable but not necessary.

#### m6. POS mostly aligned

Both banks usually match POS. Occasional phrase particles feel verb-like when target is noun (Opposite noun items with verbish keys) — low frequency.

---

## 4. Closest vs Opposite — pattern differences

| Dimension | Closest | Opposite |
|---|---|---|
| Overall verdict | **Good bones; polish** | **Needs structural fix** |
| Option structure | Consistently matched (phrase vs phrase) | Single-word; length/morphology often leaks |
| Distractor craft | Mix of form traps + semantic; some padding | Heavy form traps; **template reuse** in B5–B6 |
| Key validity | Mostly solid synonyms/glosses | Many loose / wrong antonyms |
| Construct-irrelevant cues | Mild (definition looks “more meaningful”; some stem echo) | **Severe** (odd-initial key) |
| Warm-up hygiene | Clean (0 overlap) | Full overlap with scored B1 |
| Band 1 style | Definitional + absurd distractors (very easy) | Classic antonym pairs (appropriate) |
| Band 6 | Real academic lemmas; some recycled nonsense distractors (`b6_283`/`b6_284`) | Academic verbs with clone distractors |

---

## 5. Priority fix list (do these first)

1. **Break Opposite initial-letter cue** on at least bands 3–6 (~150+ items): ensure key not uniquely identifiable by first letter.  
2. Re-key or rewrite Opposite **false antonyms:** `b4_009`, `b3_041`, `b3_047`, `b3_045`, `b4_018`, `b4_023`, `b4_017`, `b3_025`, `b5_040`, `b2_037`, `b6_029`, `b6_033`.  
3. Replace Opposite **harder-than-target keys:** `b2_041` (waive), `b3_038`, `b3_039`, `b3_048`, `b5_027`, `b6_026`.  
4. Deduplicate: Closest `b4_198`/`b6_262`; Opposite `b4_043`/`b4_044`, `b3_029`/`b5_025`; then cross-band pairs listed in M2.  
5. Fix broken Closest options: warm-up `op_020` (*a dark*); `b6_261` (*explain* → *explanation*); `b4_179` awkward English; `b5_234` particles.  
6. Diversify Opposite B5–B6 distractor triples (`equip|erode|escape`, `discuss|display|distribute`, `encounter|encourage|endure`).  
7. Soften Opposite length giveaways: `b2_004`, `b3_045`, `b4_015`, `b6_025`.  
8. Closest stem/key echo fixes: `b2_065`, `b2_067`, `b4_165`, `b4_169`, `b4_199`, `b6_255`, `b6_276`.  
9. Closest band-1: replace weakest synonym `b1_025` good→fine; optionally simplify definitional keys for *see/hear/write*.  
10. Closest padding cleanup batch: `b2_074`, `b2_075`, `b2_095`, `b3_109`, `b3_117`, `b5_250`.  
11. Opposite overused ignore/hide/quit: `b3_012`, `b3_024`, `b3_033`, `b6_022`, `b4_005`, `b4_041`.  
12. Closest `b6_283`/`b6_284` absurd recycled distractors (*soak by cloth*) — rewrite as plausible academic near-misses.  
13. Closest `b2_091` allow: *say yes* too close to *give permission* — replace with *force to* / *forbid* (as antonymish distractor) or *require*.  
14. Closest `b3_105` conclude: *confirm without doubt* competes with key — sharpen options.  
15. Decide policy: Opposite warm-ups should **not** reuse scored targets (mirror Closest), or warm-up must be explicitly non-scoring and lemmas blocked from immediate re-draw.  
16. Opposite `b4_048` imply → state (OK-ish as “state explicitly”) — keep but ensure stem forces implicit→explicit contrast.  
17. Opposite `b6_011` engage → bore (acceptable in teaching sense) — OK after letter-cue fix.  
18. Opposite `b3_046` method → chaos — weak; prefer *disorder* / *randomness* or retarget.  
19. Audit all Opposite keys that are *un-/in-/dis-* prefixes for length cue (list in automated dump).  
20. After edits, re-run: duplicate targets, brace check, option WC match (Closest), and a script that flags “key initial ∉ distractor initials.”

---

## 6. What looks solid

- **No corrupt indices / missing braces / empty options** in either scored bank.  
- **Closest option structure is disciplined** (300/300 word-count matched) — matches author preference for multi-word answers with matched distractors.  
- **Closest warm-up hygiene is excellent** (0 target overlap with scored).  
- **Runtime option shuffle** is implemented correctly — no position bias in live test.  
- **HK school context** is generally natural (library, oral exam, bullying report, PE, ferry, exam week).  
- Many Closest higher-band items are **genuinely good** meaning probes, e.g. `b4_163` implement, `b5_217` ambiguity, `b5_229` inevitable, `b6_270` discrepancy, `b6_282` thereby (therefore trap), `b6_296` ambiguous.  
- Opposite band 1 classic pairs (*hot/cold*, *early/late*, *full/empty*) are clear and age-appropriate.  
- Strong Opposite antonyms exist and should be used as models: `b2_025` include→exclude, `b3_006` expand→shrink, `b4_028` distinct→identical, `b5_014` compulsory→optional, `b5_037` dense→sparse, `b6_050` implicit→explicit, `b6_040` fluctuate→stabilise.  
- Pool size (300 / ~307) fits the “large randomised pool, short sittings” design; editing in place is feasible without a full rewrite.

---

## Appendix — Sampling method

- Automated parse via Node `eval` of `ITEM_BANK` / `WARMUP_BANK` from both HTML files.  
- Systematic sample: ≥12 items/band/test (every *n*th + edges) + all 24+24 warm-ups skimmed.  
- Additional full-band dumps for Closest B1 & B6 and Opposite B3–B6 keys for antonym audit.  
- All flagged IDs above were read from the live banks (not invented).

