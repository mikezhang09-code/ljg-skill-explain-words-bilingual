# ljg-skill-explain-words-bilingual

单词灵魂解剖师 (Word Soul Master) — 一个 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) Skill，深度解构一个词的核心语义，直击词的灵魂。**支持中英双语**：输入中文或英文皆可，输出「中文」「English」两个母语级版本以及一个「印刻」挑战。

## 功能

- **双语解构**：「中文」「English」两个区块，各为母语级原创解释（非互译）。
- **单词解剖**：
  - **原始画面**：挖掘最物理、最具体的词源画面。**任何中文标题词（包括桥接翻译过来的汉字词）必须从字形本源出发**（如甲骨文、构件拆解）；西文词则从词根物理画面出发。
  - **核心意象**：提炼极简的核心意象公式（例：`A + B = C`）。
  - **边界区分**：通过与近义词的结构性对比（边界），清晰界定该词**不是**什么。
  - **深度阐述**：结合词源，直击痛点，落脚于成年人共通的处境。
  - **成人场景**：提供一个 30–40 字的成人生活微场景，用情境强化记忆。
  - **桥接损耗**（条件项）：整个词条中至多出现一次。仅当标题词是跨语种桥接词且确有损耗时输出（且必须是字典里真实存在的词）；输入词同侧的区块禁止输出。
- **词源诚实**：词源存疑时标明“一说/disputed”。严禁发明平凡构件的含义（如“面子”的“子”）、严禁采纳励志学谣言（如“危机”的“机”是 opportunity、sincere 来自无蜡）。**事实与故事分级**：词根构成可直陈，但起源叙事（如罗马士兵盐发饷）一律标“相传/一说”，越是好听的故事越需警惕。
- **一语道破（双语原创金句）**：两个区块的引用块各包含一句独立的中英双语哲学金句（即必须同时含有中英两句作为一对，不能单语），从不同视角切入。金句必须为原创，拒绝无署名的名人名言及名言改写（riffs）。
- **量身定制的印刻挑战**：直接输出两行内容（第一行中文，第二行英文），**禁止输出标签或提示词**。必须由该词独有的意象生成，且为24小时内可完成的**产出式动作**（如说出、写下），禁止冥想/感受类动作。
- **反向查词 (reverse lookup)**：输入中文词，自动给出最贴切的英文对应词并深度解构（若确无完全等值词，**须明写“无完全对等 / no full equivalent”**）。
- **单词限制与拒答**：本技能仅适用于单个词。如输入多词概念或术语（如“机会成本”），将一句话说明并引导至 `ljg-explain-concept`。
- 直接在对话中 Markdown 输出，轻量无依赖。
- **长度纪律**：解释 ≤250字，Insight ≤180 words，场景 ≤30–40字，输出前自数，超长即删。

## 安装

```bash
/plugin marketplace add mikezhang09-code/ljg-skill-explain-words-bilingual
/plugin install ljg-explain-words-bilingual
```

## 使用

在 Claude Code 中输入（英文或中文皆可）：

```
/ljg-explain-words-bilingual Serendipity
/ljg-explain-words-bilingual 缘分
```

## 输出示例

输入一个词后，输出「中文」「English」「印刻」三个区块（示例）：

```markdown
## 中文

### 机缘 /jī yuán/ 恰好被你接住的偶然

- **原始画面**：机——弩机，一触即发的枢纽；缘（緣）——从糸，衣物的**镶边**，引申为丝线般把两端牵到一起的关联。机缘 = 一个待触发的枢纽 + 一根看不见的线。
- **核心意象**：上弦的枢纽 + 牵引的丝线 = 机缘。
- **边界**：机缘 ≠ 运气（运气是被动砸中，机缘要你伸手接住）；≠ 巧合（巧合只是概率相撞，机缘多了一层"被你认出"的心智）。
- **解释**：机缘的两个字各管一半：**机**说时刻——枢纽恰好在此刻可触发；**缘**说关联——那根线恰好牵到你。所以机缘从不属于闭着眼赶路的人：线一直在洒，枢纽一直在响，差别只在你**有没有在看**。成年人的机缘往往伪装成岔路和延误——你在找 A 的路上，拐角处遇见了更好的 B。
- **场景**：他为找旧相册翻箱倒柜，抖落出一张多年前朋友写满鼓励的明信片——正好接住了他今天的沮丧。
- **桥接损耗**：serendipity 自带锡兰三王子的**推断力**——凭敏锐在无意中"识破"珍宝的主动心智；机缘偏向佛家的"缘"，多了宿命的牵引，少了那双侦探的眼睛。

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

在今天的工作或交谈中，主动记录一次因“意外改道”而带来的惊喜收获。
Today, actively document one pleasant surprise that arose from an unexpected detour in your schedule.
```

## License

MIT
