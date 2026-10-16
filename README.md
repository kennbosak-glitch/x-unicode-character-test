# The X Unicode Character Test

**Which Unicode characters actually survive publishing on X — and render on real devices?**
That dataset didn't exist. So we made it, live, in public.

On 2026-10-16, Kenn Bosak ([@KennethBosak](https://x.com/KennethBosak)) published a 5,495-character test payload covering every symbolic character block in Unicode — plus a 633-character working vocabulary — as a single threaded post. This repo is the complete archive: the payload, the codepoint manifest, the read-back, and the verified results.

**The archive thread:** https://x.com/KennethBosak/status/2110960889155158291

## The headline results

A character test has **three layers**, and they give three different answers:

| Layer | Result |
|---|---|
| **Storage** (X's API read-back) | 5,460 of 5,495 stored codepoint-identical. Exactly **one** character stripped outright: `⫝̸` U+2ADC FORKING. 39 folded into equivalent forms (Ω→Ω, K→K, Hebrew presentation forms → base letters) — same visible glyphs, different plumbing. |
| **Render — Samsung/Android** (Galaxy Z Fold audit) | Two blocks draw as **blank space**: Geometric Shapes Extended (~278 of 291) and Symbols for Legacy Computing (250 of 250). Stored perfectly, visible to nobody. |
| **Render — desktop Chromium** | The mirror image: those two blocks render fully, but the APL symbol run (Misc Technical) and parts of Supp Math-B box out (~100–130 tofu). |

**No renderer is universal. Render truth is per-device font stack.**

## What survived everything

A **633-character vocabulary** (crypto symbols + ten styled alphabets) and a **726-character ornament kit** (box-drawing, dingbats, operators, fractions, signage) passed *every* layer — stored identically, and confirmed rendering on both Android/Samsung and desktop Chromium. Those lists are the practical output of this test: characters you can actually use in posts and be sure your audience sees them.

## Files

- `payload.txt` — the exact text that was posted (12,347 characters, 5,495 glyphs, 27 labeled blocks)
- `manifest.json` — every glyph in the payload, as `[block, codepoint]` pairs
- `published-thread-readback.txt` — the full thread text pulled back through the X API after publishing
- `RESULTS.md` — the complete findings, block by block, including the render-layer corrections
- `tier1-vocabulary.txt` — the 633 certified characters (crypto symbols + styled registers)
- `tier2-ornaments.md` — the 726 certified ornaments and text-art construction characters

## Method (steal this)

1. Build the payload from the official `UnicodeData.txt`, block by block, glyphs space-separated, each block labeled.
2. Publish it (X's composer caps a single post at ~3,874 weighted units on the app path — thread it).
3. Pull the published text back through the API (`note_tweet`), NFC-normalize both sides, and diff codepoint-by-codepoint against the manifest.
4. Audit the *render* separately, on real devices — storage survival is not visibility.
5. A Block Elements addendum (U+2580–259F, 32 characters) was certified the same way in a live reply in the thread: 32/32 stored.

## Credits

Test designed and published by **Kenn Bosak** and **Skynet** (his AI). Prompted by a simple observation: everybody styles posts with Unicode, and nobody had ever published the receipts for what actually works.

*Suggested by [@maximusmaximus](https://x.com/maximusmaximus) in the archive thread: "You gotta auto post all these tests in GitHub." — Done.*
