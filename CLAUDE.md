# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A **Claude Code Skill plugin** ("单词灵魂解剖师" / Word Soul Master) that deconstructs a single word — **English or Chinese** — into its core semantics and a bilingual epiphany, engineered so the word **sticks in adult memory** (imagery + contrast + lived scene + retrieval). There is no application code, build, lint, or test — the entire product is a prompt. "Running" it means installing the plugin into Claude Code and invoking `/ljg-explain-words-bilingual <word>`.

The long-term plan (not yet built) is to wrap this skill in a dead-simple, Google-style single-box **mobile dictionary** app. Phase 1 (current) is the bilingual skill; keep the skill's output structurally stable so it can later be parsed/cached into app cards without rework.

## Repository layout

- `skills/ljg-explain-words-bilingual/SKILL.md` — **the actual product.** YAML frontmatter (`name`, `description`) controls when the skill triggers; the Markdown body is the prompt that defines the output. Editing the skill = editing this file.
- `.claude-plugin/plugin.json` — plugin manifest (name, author).
- `.claude-plugin/marketplace.json` — marketplace manifest; `plugins[].source: "./"` points at this repo root.
- `README.md` — install/usage docs (Chinese).

Install/usage (from README):
```
/plugin marketplace add lijigang/ljg-skill-explain-words
/plugin install ljg-explain-words-bilingual
/ljg-explain-words-bilingual Serendipity
```

## The output contract (SKILL.md body) — v2

This is the spec — changes to behavior must preserve or deliberately revise this structure. Output is Markdown emitted directly into the conversation (no files, no HTML), authored in a "语言哲学大师" voice with strict length discipline. The skill **auto-detects input language** and always emits **three sections in a fixed order**: `## 中文`, `## English`, `## 印刻`. The 中文/English pair are *native deconstructions of the same meaning, not translations of each other*. Those three `##` headers are the stable split points the future app will parse on — keep them verbatim.

Each of the two language sections contains, in order:

1. **Headword line** — `### {word}  /{IPA or pinyin}/  {中文释义}`
2. `原始画面` / `Original Image` — most physical etymological image. **Chinese headwords must use 字形本源** (oracle-bone / component decomposition); Western headwords use Latin/Greek/Old English root imagery.
3. `核心意象` / `Core Metaphor` — an "X + Y = Z" formula.
4. `边界` / `Boundary` — the word vs. its two nearest neighbors, one structural (not tonal) distinction each.
5. `解释` / `Insight` — capped (解释 ≤250字, Insight ≤180 words), **bolded** keywords, must land on a universal adult experience.
6. `场景` / `Scene` — a 30–40 word/字 lived micro-scene for which only this word fits (episodic memory hook, not an example sentence).
7. `桥接损耗` / `Lost in the Bridge` — **optional bullet, at most once per entry**, emitted only in the section whose headword ≠ the user's input word (i.e. the bridged side), and only when the bridge is genuinely lossy. The section whose headword *is* the input word must never carry it. Bridge headwords must be real dictionary words (or accepted loanwords like *sajiao*) — never coinages.
8. **一语道破 / epiphany** — one bilingual aphorism in a `>` blockquote. The two sections carry **distinct** aphorisms (different angles).

`## 印刻` (Imprint) closes every entry: one 24-hour **retrieval challenge** (generation effect — user must find/name/use the word in their own life), expressed in one Chinese line + one English line.

**Cross-language / reverse lookup:** when input and section language differ, that section uses the truest equivalent word as its headword (Chinese input `缘分` → English section may list 1–3 candidates, then deep-dives one, e.g. *serendipity*). Same-language sections never carry the bridge-loss bullet.

**Etymology honesty rule:** disputed or folk etymologies must be flagged ("一说 / disputed"), never invented — this extends to *components*: a plain suffix (面子's 子) must not be assigned a fabricated meaning, and motivational-myth readings (危机 = "danger + opportunity", sincere = *sine cera*) are banned from every bullet. Trust-critical for a dictionary product.

**Aphorism originality rule:** the 一语道破 blockquotes must be original. Famous quotes (Emerson, Thoreau, proverbs) may not be passed off unattributed; if quoted at all, attribute, max once per entry.

**Refusal guard:** if the skill is invoked (even explicitly) on a multi-word concept (机会成本, "compound interest"), it must not produce an entry — it emits one line redirecting to `ljg-explain-concept` and stops.

## Gotchas to respect

- **Scope boundary / sibling skill.** This skill is for a *single word* (English or Chinese). Its `description` delegates **multi-word concepts and ideas** to a separate skill, `ljg-explain-concept` — that's the line, single lexical item vs. multi-word idea. Preserve it in the `description` (it's what Claude uses to route), and don't broaden this skill to cover concepts.
- **Parse-point stability.** The three `##` headers (`中文` / `English` / `印刻`) and the bold bullet labels are the app's future parse anchors. `桥接损耗` / `Lost in the Bridge` is the only *optional* anchor — the app parser must tolerate its absence.
- **No section creep.** The skill's power is compression: soul, borders, scene, strike, retrieve. Resist adding register notes, word families, frequency data, or other lexicographic apparatus.

> Note: manifests (`plugin.json` / `marketplace.json`) were previously reconciled to the bilingual markdown behavior. `SKILL.md` remains authoritative; keep the manifests in sync on future behavior changes (the v2 description adds the memory-engineering framing).
