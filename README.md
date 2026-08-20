# Figthus

> 自动判断最合适的交付，把中文文章变成白底手绘正文配图，或一张有完整观点的六宫格连环画。
>
> 物件小品优先 | 烂笔头 × 破橡皮可选 | 深石墨手绘 | Codex Skill

---

## 这个仓库是什么

Figthus 是一个 Codex Skill，用来指导 AI Agent 为中文文章、帖子、博客、Notion 文档和方法论内容生成正文配图。

它不是通用插画 prompt，也不是 PPT 信息图模板。它的核心目标是：**先理解文章里的认知锚点，再把其中一个判断、流程、结构、状态或隐喻，变成一张有记忆点的手绘解释图。**

Figthus 先自动选择两种交付模式之一：

- **article-illustration**：一张或多张贴近正文段落的认知插图。
- **narrative-comic-6**：一张 3×2 的六宫格连环画，完整承载整篇文章的核心观点，或一个边界明确、可以独立闭合的局部观点。

确定交付后，再选择三种视觉模式；默认先用物件小品：

- **restrained-object-vignette**：破橡皮先作为有磨损的物件出现，不强制腿、眼睛、对白或中文批注。
- **trace-object**：保留一点姿态、接触或擦痕，但不回到完整角色说明图。
- **character-led**：只有认知动作需要两种力量互动时，才启用烂笔头和破橡皮的完整角色规则。

当用户没有指定交付形式时，Figthus 会自动比较六宫格与正文配图：只有观点完整、确有推进、适合独立传播、能形成视觉连续性且可以短文案压缩时，才选择六宫格；否则使用一张或多张正文配图。用户明确指定模式、数量或插入位置时，以用户要求为准。

角色 IP 仍然保留，但不再是每张图的默认入口：

- **烂笔头**：负责先写、先错、先把混沌外化成痕迹。
- **破橡皮**：负责怀疑、擦改、校准、把假清楚擦出空白。

一句话：**不画知识点，画知识点里正在发生的那一下。**

---

## 适合谁用

特别适合：

- 写中文文章，需要正文配图和文章插图的人
- 做知识型内容、方法论内容、AI 工作流内容的人
- 想把抽象判断画成具体认知动作的人
- 想要一种比 PPT 信息图更轻、更怪、更有个人识别度的配图风格的人
- 用 Codex 做内容生产，希望稳定复用一套视觉语言的人

不适合：

- 想要商业插画、品牌 KV 或精致扁平插画的人
- 想要传统 PPT 信息图、复杂架构图或流程图的人
- 想要儿童文具、可爱 IP、表情包风格的人
- 想把大量正文、长段解释或完整课程页塞进一张图里的人
- 需要严格可编辑矢量源文件的人

---

## 它会产出什么

根据 Delivery decision 输出：

- `article-illustration`：按 brief 决定比例的一张或多张正文配图，以及相应 shot list
- `narrative-comic-6`：一张 `01-narrative-comic-6.png` 加一份可后期叠字的 `comic-script.md`
- 每张图的主题、认知锚点、核心意思、可视动作、出场角色和中文标注建议
- 最终 PNG 图片，保存到 workspace 的 `assets/<article-slug>-figthus/`

默认不输出：

- PPTX / PDF / Keynote
- SVG / HTML / Canvas 可编辑图
- 商业海报或封面 KV
- 大段文字型信息图

---

## 视觉风格

Figthus 默认使用“物件优先的残损材料认知草图”风格：

- 物件小品默认使用纯白、暖白或极浅奶油底色，不要明显纸纹、渐变、阴影或复古滤镜
- 深石墨或柔和炭黑手绘线稿，线宽自然变化，允许开放轮廓和细小断点
- 物件小品主体约占 20%-45%，保留 55%-80% 的安静留白；角色正文图再使用 40%-60% 的主体尺度
- 物件小品默认 0 个文字；正文角色图才使用少量红橙蓝中文批注
- 一张图只表达一个核心认知动作、结构、状态或隐喻
- 烂笔头和破橡皮不必每张图同时出现；出场角色必须承担动作，未出场的一方可以通过铅笔线、擦痕、灰屑、空白、断芯或证据单在场
- 一个物件、一个动作、一个后果优先；不要自动添加小黑、吉祥物、腿、眼睛、嘴巴、箭头、节点、边框或左上角标题
- 怪诞、低微、笨拙、清爽，但不幼稚、不卖萌

迁移规则详见 [克制物件小品模式](figthus/references/restrained-vignette.md)。

---

## 示例图库

这些是 Figthus 原生正文插图示例，不是角色设定稿。每张图只压住一个认知动作。

### 第一笔推出去

![第一笔推出去](examples/images/01-first-mark.png)

### 证据拖回来

![证据拖回来](examples/images/02-evidence-return.png)

### 假清楚被擦掉

![假清楚被擦掉](examples/images/03-false-clarity-erased.png)

### 停止闸

![停止闸](examples/images/04-stop-gate.png)

### 从空白重启

![从空白重启](examples/images/05-restart-from-blank.png)

### 裂开了

![裂开了](examples/images/06-cracked-overload.png)

## IP 设定

当前角色基准图：

![烂笔头和破橡皮设定稿](assets/pencil-eraser-ip-design/lanbitou-poxiangpi-reference-v2.png)

完整设定见 [docs/ip-design/lanbitou-poxiangpi-ip.md](docs/ip-design/lanbitou-poxiangpi-ip.md)。

这张设定图只用于校准角色形象，不是正文插图示例。

角色设定与完整身份规则只在 `character-led` 模式启用；物件小品模式不需要加载这张设定图。

---

## 安装

克隆仓库：

```bash
git clone https://github.com/rv198-star/Figthus.git
cd Figthus
```

复制 skill 到用户级 Codex skills 目录：

```bash
mkdir -p "$HOME/.agents/skills"
cp -R ./figthus "$HOME/.agents/skills/figthus"
```

如果只希望它在当前仓库中可用，也可以把 `figthus/` 放到仓库的 `.agents/skills/figthus/`。Codex 会自动发现新增或修改的 skills；如果没有立即出现，重启 Codex。

安装后，在 Codex 里使用：

```text
Use $figthus 自动判断并为这篇中文文章生成最合适的视觉内容。
```

---

## 怎么用

### 让 Figthus 自动决定（推荐）

```text
Use $figthus 为下面这篇公众号文章设计并生成最合适的视觉内容。
不要预设是多张正文配图还是六宫格；先做 Delivery decision，再直接进入更有内容价值的模式。

<粘贴文章>
```

Figthus 会先说明选择 `article-illustration` 还是 `narrative-comic-6`，以及为什么没有选择另一种，然后在用户已要求生成时直接继续，不额外等待确认。

### 只做配图规划

```text
Use $figthus 先不要生图。
请分析下面这篇文章哪里值得配图，输出 5 张左右的 shot list。
每张图写清楚：放在哪段后、主题、认知锚点、可视动作、哪个角色出场、未出场角色留下什么痕迹、建议中文标注词。

<粘贴文章>
```

### 直接生成正文配图

```text
Use $figthus 把下面这篇文章生成 4 张正文配图。
要求：先判断每张图使用 restrained-object-vignette、trace-object 还是 character-led；不要默认让破橡皮拟人化。角色正文图才使用 16:9、纯白和少量中文批注，物件小品优先保持小主体和大留白。
每张图只讲一个认知动作，不要做 PPT 信息图，不要儿童文具海报。

<粘贴文章>
```

### 把文章压成一张六宫格连环画

```text
Use $figthus 把下面这篇文章做成一张 narrative-comic-6 六宫格连环画。
不要把六个段落或六张普通配图硬拼成网格。先选择 whole-article 或 local-complete，写清覆盖范围、核心观点、论证链和排除内容；再给出一句 Narrative promise，并按“起题 → 旧解/压力 → 转折 → 展开 → 限定/深化 → 收束”写六格分镜。最后生成一张 3×2、1:1 的完整合成图，并保存 comic-script.md 供后期校对中文。

<粘贴文章>
```

### 为单个概念生成一张图

```text
Use $figthus 为“结果要带着证据回来，而不是让 AI 原地多试几次”生成一张正文配图。
画面要怪诞但清爽，烂笔头负责推出第一版，破橡皮负责拿证据判断改哪里。
```

### 去掉图里的标题或错误文字

```text
Use $figthus 帮我编辑这张图，去掉左上角的“流程图”标题，其他内容保持不变。
```

更多示例见 [examples/prompts.md](examples/prompts.md)。

---

## 工作流程

这个 skill 的流程是：

1. 读取文章、Markdown、Notion 内容、截图或用户给的主题
2. 提炼核心观点、认知转折、流程结构和适合视觉化的段落
3. 用户未指定形式时，按五项门槛自动选择标准正文配图或 narrative-comic-6
4. 输出简短 Delivery decision；标准模式继续 shot list，漫画模式继续 Coverage contract、叙事承诺和六格分镜
5. 把抽象概念换成可视动作
6. 为每张图选择结构类型：推出第一版、擦掉假清楚、证据回流、停止规则、重启空白、并行修正或失败分类
7. 重新发明一个低科技、怪诞但成立的物理隐喻
8. 选择出场角色：可以双角色同屏，也可以只让烂笔头或破橡皮单独承担核心动作
9. 标准模式每张图单独生成；漫画模式生成一张完整 3×2 合成图
10. 按 QA checklist 检查：白底、留白、出场逻辑、叙事推进、残损状态、短中文标注、非 PPT 感、非旧案例复刻
11. 保存最终 PNG、漫画脚本（如适用），并报告用途和路径

---

## 目录结构

```text
.
├── README.md
├── LICENSE
├── NOTICE.md
├── assets/
│   └── pencil-eraser-ip-design/
├── docs/
│   └── ip-design/
├── examples/
│   ├── images/
│   └── prompts.md
├── figthus/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   ├── assets/
│   │   ├── examples/
│   │   ├── reference/
│   │   └── legacy-xiaohei-examples/
│   └── references/
│       ├── style-dna.md
│       ├── restrained-vignette.md
│       ├── ip-character.md
│       ├── composition-patterns.md
│       ├── narrative-comic.md
│       ├── prompt-template.md
│       └── qa-checklist.md
└── legacy/
    ├── origin/
    └── xiaohei-examples/
```

真正需要安装到 Codex 的是子目录：

```text
figthus/
```

根目录的 README、LICENSE、NOTICE、docs、assets 和 examples 是 GitHub 分享与开发文档。

---

## 注意事项

- 先选认知动作，不画概念名词。
- 图片里的中文文字越短越稳定。
- 每张图只讲一个核心结构，不要把文章做成说明书。
- 烂笔头和破橡皮不是必须同时出场；如果只出现一个角色，画面里也要有另一种力量留下的痕迹。
- 如果去掉出场角色画面仍然完全成立，说明角色太装饰了。
- 角色设定图只用于校准形象，不要复刻构图。
- 上游小黑示例只作为 legacy 来源材料，不是 Figthus 示例图库。
- AI 图像模型可能出现错字、幻觉标签、风格漂移或多余标题，生成后需要检查。
- 如果中文错字严重，优先减少标注词并重生成。

---

## Origin / Attribution

Figthus forked and adapted the structure and method spine of [Ian Xiaohei Illustrations](https://github.com/helloianneo/ian-xiaohei-illustrations), an MIT-licensed Codex Skill by Ian.

The original MIT license is retained in [LICENSE](LICENSE). See [NOTICE.md](NOTICE.md) for retained legacy assets and provenance notes.

---

## License

MIT License. See [LICENSE](LICENSE).
