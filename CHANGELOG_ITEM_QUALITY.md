# Item quality improvements — 23 Oct 2026 (Asia/Hong_Kong)

Based on `ITEM_QUALITY_REVIEW.md`. Pool sizes kept (Opposite 307+24, Closest 300+24). Scoring/adaptive JS unchanged.

## Opposite Meaning (critical)

| Metric | Before | After |
|---|---|---|
| Letter-cue items (all 3 distractors share target initial; key does not) | 250 (81.4%) | **0 (0%)** |
| Prefix key + letter-cue stack | 45 | **0** |
| Exact sentence+target duplicates | 2 pairs | **0** |
| Cross-band same-lemma clones | 8 pairs | **0** |
| Cloned distractor triples (≥3 items) | 5 patterns (equip\|erode\|escape ×28, etc.) | **0** |
| Warm-up ∩ scored targets | 24/24 | **0/24** |

### Weak / false antonyms re-keyed (examples)
derive→have no link to; attitude→apathy; perspective→narrow view; impact→no effect; dimension→no aspect; proportion→imbalance; criterion→non-factor; assume→doubt; estimate→know exactly; discriminate→treat equally; exemplify→misrepresent; exploit→protect; describe→omit; analyse→guess blindly; evaluate→overlook; require→not need; persuade→discourage; recognise→fail to know; strategy→no plan; conventional→unusual; enrich→weaken; exceed→fall short of; method→randomness; plus length/morphology softenings (available→not free, justify→make invalid, exaggerate→play down).

### Deduped / replaced lemmas
estimate duplicate→conceal; contribute duplicate→compensate; public (B4)→temporary; expand (B6)→suppress; establish (B6)→undermine; evaluate (B6)→scrutinise; enhance (B6)→amplify; exclude (B6)→marginalise.

### Warm-ups
Replaced all 24 with ultra-easy lemmas absent from the scored pool (tall/rich/dark/wet/…/on).

## Closest Meaning (polish)

- Fixed broken options: warm-up op_020 “a dark”→“a dark room”; b6_261 “be a short explain”→“be a brief explanation”; b4_179 awkward English; b5_234 particles.
- Stem-echo softens: information, environment, justify, hypothesis, occupy, conform, constrain, resilience.
- Deduped: impose (B6)→inflict; accumulate (B6)→amass; advocate (B6)→champion.
- Light padding / distractor polish (different, popular, decrease, establish, approach, confront, abolish, abstain, allow, conclude); b1_025 good→nice.

## Intentionally left for later
- Closest band-1 definitional style + absurd distractors (M7) — not rewritten en masse.
- Closest remaining letter-initial patterns (~47%) — out of scope for this pass (Opposite was the construct-irrelevant cue crisis).
- Some Opposite keys still soft classroom antonyms (anticipate→miss, assess→overlook family) — acceptable for pilot.
- Full synonymy audit of every auto-diversified distractor — sampled; mass letter-cue break used curated + pooled near-misses.

## Files
- `opposite-meaning-test.html`
- `closest-meaning-test.html`
- `ITEM_QUALITY_REVIEW.md` (review source; untracked→tracked if committed)

## Testing mode (secret, 23 Oct 2026)
- Enter name `testing` (case-insensitive) on either HTML test to show per-item `id`, `band`, and the post-shuffle correct option (badge + panel). Separate from `debug` stats mode. Not advertised on the start screen.
