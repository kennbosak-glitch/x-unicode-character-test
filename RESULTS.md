# X Character Set Test — RESULTS (2026-10-16, Kenn + Skynet)
Archive post (root): https://x.com/KennethBosak/status/2110960889155158291 — self-thread of 5 posts (root + 4 continuations posted by Kenn from the prepared file; X's composer path capped the root at 2,788 chars / 3,874 weighted units, remainder threaded).
Method: full text pulled back via X API (note_tweet), NFC-normalized, diffed codepoint-by-codepoint against the 5,495-glyph manifest (x-charset-test-manifest.json).

## Headline
- 5,495 characters in → 5,460 codepoint-identical out. ZERO blocks failed.
- Reply-guy vocabulary: 633/633 survived. NOTHING struck from skyx-arsenal.md.
- 34 differences = Hebrew presentation forms (U+FB1D–U+FB43 subset) folded by the platform into base Hebrew letter+mark sequences (NFKC-style) — verified present in the thread text; visually equivalent.
- 5 canonical swaps in the root post (U+2126 OHM→U+03A9, U+212A KELVIN→K, U+212B ANGSTROM→U+00C5, U+2329→U+3008, U+232A→U+3009) — NFC normalization, identical glyphs.
- EXACTLY ONE true disappearance: U+2ADC FORKING (neighbors U+2ADB/U+2ADD survived). The only character in the entire symbolic frontier that X's pipeline drops outright.
- Composer finding: the app posting path silently capped the paste at ~3,874 weighted units (not the advertised 25,000) — hence the thread. Weighted counting: most non-Latin glyphs weigh 2.

## CORRECTION — render layer (Kenn's challenge, verified from his full-res thread screenshot, Galaxy Z Fold / Samsung font stack)
Kenn doubted the verdict; he was right to. The codepoint diff measures STORAGE only. Render audit of the actual thread on his phone shows:
- TWO BLOCKS EFFECTIVELY INVISIBLE on Samsung/Android: **Geometric Shapes Extended** (~278 of 291 glyphs draw as BLANK — only the ~13 emoji-presentable colored circles/squares U+1F7E0–1F7EB show) and **Symbols for Legacy Computing** (250 glyphs — entire block blank). Stored perfectly, rendered as nothing (not even tofu).
- Everything else renders on the Fold, INCLUDING the full reply-guy vocabulary (crypto row, all styled registers, circled, fullwidth, small caps — visually confirmed in screenshot) and the combining-mark blocks.
- App behavior note: long thread posts display folded behind "Show more" in thread view; data intact.
- Arsenal impact: NONE — no vocabulary item comes from the two invisible blocks. Frontier guidance updated: Geometric Shapes Extended + Legacy Computing = DO NOT USE (invisible on Samsung). The earlier compose-probe "all rendered" result was Chromium-font-stack only; device stacks differ.

## Render layer 2 — desktop Chromium audit (2026-10-16, full thread, zoomed inspection)
Mirror image of the Samsung result — each font stack fails DIFFERENT blocks:
- Chromium renders Geometric Shapes Extended and Symbols for Legacy Computing FULLY (both blank on Samsung).
- Chromium TOFU: Misc Technical APL run U+234E–U+237A (~35–40 boxes) and Supp Arrows-B/Misc Math-B/Supp Math Operators (~60–90 boxes) — both render FINE on Samsung.
- Vocabulary (incl. full Math Alphanumeric registers + Enclosed Supplement): CLEAN on Chromium too.
CONCLUSION: no renderer is universal; render truth is per-device font stack. The 633-char vocabulary is the intersection confirmed on every tested layer: X storage, Samsung/Android, desktop Chromium.

## Block Elements certification (2026-10-16, Kenn ordered live test in-thread)
SkyX replied in the archive thread (https://x.com/KennethBosak/status/2110966761017545059) with all 32 Block Elements U+2580–259F + a "test still running" note. API read-back: 32/32 stored. Render verdict pending Kenn's Fold eyeball (audience device = deciding stack); Chromium check not rerun.
## DESIGN LAW (Kenn, 2026-10-16): text-art designs = ONE LINE ONLY, max one visible line on X on any device — multi-line art drifts per-device fonts and breaks. Baked into skyx-arsenal.md.
