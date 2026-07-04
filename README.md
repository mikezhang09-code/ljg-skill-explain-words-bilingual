# ljg-skill-explain-words

单词灵魂解剖师 (Word Soul Master) — 一个 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) Skill，深度解构一个词的核心语义，直击词的灵魂。**支持中英双语**：输入中文或英文皆可，输出「中文」「English」两个母语级版本以及一个「印刻」挑战。

## 功能

- **双语解构**：「中文」「English」两个区块，各为母语级原创解释（非互译）。
- **单词解剖**：
  - **原始画面**：挖掘最物理、最具体的词源画面（中文词从字形本源出发，如甲骨文；西文词从词根画面出发）。
  - **核心意象**：提炼极简的核心意象公式（例：`A + B = C`）。
  - **边界区分**：通过与近义词的结构性对比（边界），清晰界定该词**不是**什么。
  - **深度阐述**：结合词源，直击痛点，落脚于成年人共通的处境。
  - **成人场景**：提供一个 30–40 字的成人生活微场景，用情境强化记忆。
  - **桥接损耗**（可选）：跨语种翻译时，指出对应的桥接词丢失了原词的何种神韵。
- **一语道破**：每个区块各有一句独立的中英双语哲学金句（从不同视角切入）。
- **印刻挑战**：文末提供一个 24 小时内可在生活中实践的取用挑战，帮助用户真正掌握并使用该词。
- **反向查词 (reverse lookup)**：输入中文词，自动给出最贴切的英文对应词并深度解构（例：缘分 → serendipity）。
- 直接在对话中 Markdown 输出，轻量无依赖。

## 安装

```bash
/plugin marketplace add mikezhang09-code/ljg-skill-explain-words-bilingual
/plugin install ljg-explain-words
```

## 使用

在 Claude Code 中输入（英文或中文皆可）：

```
/ljg-explain-words Serendipity
/ljg-explain-words 缘分
```

## 输出示例

输入一个词后，输出「中文」「English」「印刻」三个区块（示例）：

```markdown
## 中文

### serendipity /ˌserənˈdɪpəti/ 机缘巧合；意外发现珍宝的能力

- **原始画面**：三位锡兰（Serendip）王子在旅途中，总能从看似无关的线索里推断出自己并未寻找的真相。
- **核心意象**：不刻意寻找 + 敏锐的眼睛 + 偶然的相遇 = 命运的馈赠
- **边界**：serendipity ≠ luck（运气是被动撞上好事，而 serendipity 是当幸运降临时你有能力认出并接住它）；≠ coincidence（巧合只是概率的随机相撞，不含心智 of 发现与洞察）。
- **解释**：它不仅仅是好运，而是一种**有准备的偶然**。当命运把线索洒在你的必经之路上，只有那些保持警觉、对世界充满好奇的头脑，才能把无关的碎片拼凑成无价的发现。它发生在寻找 A 的路上，在拐角处遇见了更美的 B。
- **场景**：你翻箱倒柜寻找旧相册，却在书页里抖落出一张多年前写着鼓励话语的明信片，正好治愈了你今天的沮丧。
- **桥接损耗**：中文的“机缘巧合”强调了偶然（巧），但漏掉了原词中“凭借敏锐洞察力在无意中发现”的主动心智。

> "You cannot search for serendipity; you can only become worthy of it.
> 机缘无法被搜寻，只能被配得上。"

## English

### serendipity /ˌserənˈdɪpəti/ — 机缘巧合

- **Original Image**: three princes of *Serendip* who keep deducing things they were never looking for.
- **Core Metaphor**: not seeking + a sharp eye + a chance encounter = a gift you didn't ask for
- **Boundary**: serendipity is not luck (luck is passive and blind; serendipity requires the active eye to notice the gift); not coincidence (coincidence is statistical variance; serendipity requires human interpretation to have meaning).
- **Insight**: coined by Horace Walpole in 1754, serendipity is the active faculty of recognizing fortune when it arrives by accident. It is the reward of the **attentive wanderer**. You set out to map a path to one destination, only to stumble upon a sanctuary you didn't know existed. It demands we embrace the detour.
- **Scene**: you got lost in a foreign city, missed your train, and ended up sitting in a small café where you met your future business partner.

> "Chance favors the connected mind. 偶然，偏爱善于联结的头脑。"

## 印刻

- 观察今天生活中发生的一个“意外”，写下它如何指引你发现了一件本没预料到的好事。
- Observe an unexpected detour in your day today and note down how it led to a discovery you weren't looking for.
```

## License

MIT
