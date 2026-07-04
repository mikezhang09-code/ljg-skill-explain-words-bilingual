# Regression Test Suite — ljg-explain-words-bilingual

Run this suite (or a subset) after **any** edit to `SKILL.md`. Each word was chosen because it once exposed a real failure; the pass criteria below are the fixes' proof of life.

## Protocol

- **Cold sessions only**: one word per fresh session, zero prior entries in context. (Round-2 lesson: models copy their own cached outputs instead of regenerating from the spec — contaminated runs produced three unreadable results.)
- Run in the model that will power the product; cross-model results go in separate columns, never mixed.
- Grade against the per-word criteria below **plus** the universal checklist at the bottom.

## Test words

| # | Word | Input lang | What it tests | Pass criteria |
|---|------|-----------|---------------|---------------|
| 1 | 危机 | 中文 | Motivational-myth ban | 机 = 弩机/trigger-pivot everywhere; "danger + opportunity" appears in **no** bullet, incl. 桥接损耗 |
| 2 | sincere | EN | Named folk etymology | *sine cera* ("without wax") debunked or absent; *sincerus* root given; deep root hedged as uncertain |
| 3 | salary | EN | **Procedural** honesty (unnamed story) | *sal-* root stated as fact; "soldiers paid in salt" hedged (相传/一说/disputed/popular narrative) |
| 4 | 面子 | 中文 | No fabricated component meanings | 子 identified as plain noun suffix (or passed over) — never "表层/覆盖物" |
| 5 | envy | EN | Bridge-headword 字源 + quote originality | 中文 block opens from 字形 (嫉从疾 or similar), not recycled Latin; both aphorisms original (spot-search the quotes) |
| 6 | nostalgia | EN | Real-word bridge headwords | 中文 headword is 怀旧 or 乡愁 — never a coinage (乡愁病) |
| 7 | 委屈 | 中文 | Untranslatable path | 1–3 EN candidates listed; 无完全对等 stated; Lost in the Bridge names the voluntary-bending asymmetry |
| 8 | integrity | EN | Abstract-word boundary + 印刻 specificity | Boundary cuts vs honesty/authenticity structurally; 印刻 derives from wholeness/integer imagery, not generic self-help |
| 9 | deadline | EN | Control (has always passed) | Quality holds; prison-line origin kept; time-sense leap may be flagged as debated |
| 10 | 敷衍 | 中文 | 印刻 format (zh-input path) + candidates | Two bare 印刻 lines, no "一行中文/One English line" labels; productive action; candidates + 无完全对等 |
| 11 | resilience | EN | 印刻 format (en-input path) | Same as #10; *resilire* "leap back" root; boundary vs toughness/endurance structural |
| 12 | 机会成本 | 中文 | Negative test (refusal) | **No entry produced.** One-line redirect to `ljg-explain-concept` |
| 13 | sunk cost | EN | Negative test, English side | Same as #12 |

## Universal checklist (every entry)

1. Exactly three `##` headers, verbatim: `中文` / `English` / `印刻` (ignore stray `---` rules when parsing).
2. Every blockquote is a **bilingual pair** — one English + one Chinese sentence. Monolingual = fail.
3. 桥接损耗 / Lost in the Bridge: **at most once per entry**, only in the section whose headword ≠ the user's input word.
4. Chinese headwords (incl. bridge headwords) open from 字形本源; Western headwords from Latin/Greek/OE roots — never crossed.
5. Origin *narratives* hedged (相传/一说/disputed); root *composition* may be stated as fact.
6. Both aphorisms original (no unattributed quotes **or riffs** on famous lines).
7. 印刻: two bare lines (中文 then English), no scaffolding labels, productive action (say/write/find/do), derived from the word's own imagery.
8. Lengths: 解释 ≤250字, Insight ≤180 words, 场景/Scene 30–40 字/词. (Known variance: some models run ~10–15% hot — see below.)
9. 边界 distinctions are structural (who holds whom, who feeds on whom), never tonal ("stronger", "more formal").

## Known residual variance (app-layer QA, not prompt fixes)

- **Length caps drift ~10–15%** on some models → enforce mechanically in the app pipeline.
- **Candidates/无完全对等 line occasionally skipped** on the zh→en path → app validator should require it when input is Chinese.
- **训诂 disagreements are real** (e.g. 韧: 刃 as phonetic 「从革，刃声」 vs. semantic blade-vs-leather reading — both defensible) → the app needs an etymology **verification/arbitration pass** (second model call: "list every factual etymology claim; flag disputed/folk items") before caching any entry. A prompt cannot settle philology; a checker with sources can at least surface it.

## History

- v1 → v2: added 边界/Boundary, 场景/Scene, 印刻, 桥接损耗, length caps, honesty rule (review, 2026-07).
- v2 → v2.1: bridge-loss made single-sided via headword self-check; refusal guard; quote originality; no coined headwords; component-fabrication ban (after Gemini round 1: 8/8 double-sided bridge loss, Emerson/Thoreau quotes, 面子 fabrication, 机会成本 not refused).
- v2.1 → v2.2: bilingual quote pairing made explicit; 字源 extended to bridge headwords; riff ban; word-specific 印刻 (after round 2 + contamination discovery).
- v2.2 → v2.3: honesty rule made procedural (narratives hedged by category); 印刻 rewritten to prevent label leakage + ban contemplative tasks; self-count length rule; explicit 无完全对等 (after round 3: salt legend, label leakage in 4/6).
- v2.3 verified: salary/敷衍/resilience cold runs passed all trap checks (2026-07-05).
