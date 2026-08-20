# 生图提示词模板

每张图单独生成。根据正文内容替换变量，不要把多张图拼在一起。

`narrative-comic-6` 是唯一例外：它生成一张本身就包含 3×2 六格的合成连环画。先读取 `narrative-comic.md` 并完成 beat sheet，不能把下面的单图模板连续调用六次后再拼贴。

## 六宫格叙事连环画模板

```text
Generate one single square Chinese editorial narrative comic in Figthus style. This is one complete 3 columns × 2 rows comic page, not a collage of unrelated illustrations. Use clear white outer margins and narrow white gutters. Reading order is left-to-right across the top row, then left-to-right across the bottom row. Keep the same recurring characters, materials, line treatment, and color semantics across all six panels.

Delivery mode: narrative-comic-6.
Coverage scope: {whole-article | local-complete}
Source boundary: {整篇文章 | 具体章节/段落/论证范围}
Central viewpoint: {一句核心判断}
Reasoning spine: {问题/张力 → 核心主张 → 关键理由或证据 → 文中已有的条件/边界/代价/关键含义 → 结论}
Excluded material: {这张图明确不覆盖什么}
Narrative promise: {读者从什么问题/旧理解出发；经过什么关键理由、证据或转折；最后理解什么核心判断与含义}
Main title outside the panels, optional: {不超过 12 个汉字；没有必要时省略}
Persistent visual thread: {持续出现的角色 / 纸条 / 铅笔线 / 工具 / 问题卡}

Use Figthus character-led visual DNA: restrained hand-drawn graphite/charcoal line art, damaged lowly desk-tool characters, off-white or clean white background, very limited semantic accent colors, dry and slightly absurd, not cute, not a commercial cartoon, not a PPT or infographic. Preserve the Figthus character identity rules exactly. Each panel must show a distinct action and a visible consequence; do not repeat a standing pose with changed text.

Panel 1 — question/tension:
Scene: {范围内真正的问题、目标或张力具体出现}
Change: {读者知道这张图要回答什么}
Argument job: {问题/张力}
Caption: {6–14 个汉字的短句；需要准确长句则后期叠字}

Panel 2 — old answer/pressure:
Scene: {常见答案失效，或现实压力具体出现}
Change: {表面解释显出不足}
Argument job: {旧解为何失效/现实压力}
Caption: {短句}

Panel 3 — central turn:
Scene: {核心主张或决定性证据以动作出现}
Change: {文章真正的判断被提出}
Argument job: {核心主张/决定性转折}
Caption: {短句}

Panel 4 — reasoning:
Scene: {机制、理由、案例或证据被具体展开}
Change: {核心主张得到支撑}
Argument job: {关键理由/证据/机制}
Caption: {短句}

Panel 5 — qualification/deepening:
Scene: {原文已有的条件、边界、代价、后果或更深含义以可见物件呈现}
Change: {核心判断被理解得更准确}
Argument job: {条件/边界/代价/后果/关键含义}
Caption: {短句}

Panel 6 — landing:
Scene: {与第一格呼应的可见结果/下一步}
Change: {新的判断收束}
Argument job: {结论/含义/下一步}
Caption: {短句}

Text rule: use only a small panel number and one brief, legible Chinese caption per panel. No paragraphs, dense dialogue bubbles, UI cards, complex diagrams, or duplicated title in every panel. If Chinese spelling must be publish-perfect, generate the visual base without captions and provide the six captions separately for later layout.

Completeness constraint: the six panels together must let a reader recover the central viewpoint, why it holds, the boundary, consequence, or key implication supported by the source, and its conclusion without reading the source article. Do not claim whole-article coverage when the panels only represent one fragment. Do not invent evidence, counterexamples, conditions, or boundaries that are not present in the source.

Negative constraints: do not imitate the reference dog mascot, bright yellow background, exact phrases, composition, or palette. No cute stationery advertising, manga screentones, glossy vector art, photorealism, dense course slide, arbitrary 6-topic list, or weak scene continuity.
```

## 默认：克制物件小品模板

当 restrained-object-vignette 成立时，优先使用这段模板，再填入文章动作：

```text
Generate one standalone editorial object vignette, preferably square or with the brief-specified ratio.

Visual mode: restrained-object-vignette.

Warm white or pale cream background. One small worn object, one physical action, one visible consequence. Keep the subject around 20%-45% of the canvas and leave 55%-80% quiet negative space. Use deep charcoal or soft graphite lines with natural variable width, open contours, small gaps, and tactile abrasion. Use one muted accent color only.

Use the broken eraser as a physical object, not a mascot: retain the pink left half, gray-white right half, chipped outer-left pink edge, graphite smudges, old erased marks, and damaged material. Use a side, three-quarter, top, or contact view. Do not force legs, eyes, mouth, hands, dialogue, nameplates, Chinese labels, arrows, nodes, frames, or a title.

Cognitive action: {擦掉假清楚 / 压住后果 / 让确定性弯一下 / 重新开出空白 / 其他物理动作}
Composition: {物件与线、擦痕、灰屑、断面或空白的具体关系}
Visible consequence: {被擦掉的部分、留下的残线、变形的线、开出来的新空白或被阻止的路径}

Negative constraints: no fixed Xiaohei character, no cute stationery mascot, no full infographic, no explanatory scene, no polished vector outline, no saturated color, no realistic shading, no decorative clutter.
```

如果去掉腿、脸和对白后，动作关系不成立，再切换到下面的 trace-object 或 character-led 模板。

## 角色出场决策

每张图先写角色出场决策，再进入提示词：

```text
Role decision:
{单角色：只让烂笔头/破橡皮出场，因为核心动作是...；另一方只通过...痕迹在场。
或
双角色：两者同屏，因为烂笔头负责...，破橡皮负责...，这组互动正是文章锚点。}
```

不要把双角色当默认模板。只有当两者各自承担不同、不可互换的动作时，才使用双角色。

## 双角色正文配图模板

```text
Generate one standalone 16:9 horizontal Chinese article illustration.

Role decision:
Use both 烂笔头 and 破橡皮 because {双角色互动必要性}. 烂笔头负责 {生成/外化/写入/推进动作}；破橡皮负责 {擦改/证据/校准/停止/验收动作}. If either character would only stand beside the scene, use the single-character template instead.

Visual DNA:
Pure white background. Minimalist black hand-drawn line art. Slightly wobbly pen lines. Lots of empty white space. Sparse red/orange/blue handwritten Chinese annotations. Clean absurd product-sketch feeling. Lowly damaged desk-tool mood. No gradients, no shadows, no paper texture, no complex background, no commercial vector style, no PPT infographic look, no cute stationery mascot poster, no children's illustration, no realistic UI.

Recurring IP characters required:
烂笔头: a nearly used-up pencil stub, short, skinny, angled forward, dirty muted yellow paint, exposed rough wood, blunt crooked graphite tip that may snap, tiny thin legs, tiny black dot eyes, stubborn serious expression. Tail has a clearly visible oversized bent silver metal ferrule with 2-3 crimp rings and a tiny almost-used-up gray-pink eraser cap. 烂笔头 makes the first mark, pushes a draft forward, or externalizes the idea.

破橡皮: a broken eraser fragment, squat, blunt, dirty pink-gray and gray-white two-material body, eyes drawn only as two very short flat black horizontal strokes, tiny short legs clearly visible under the body. In front or three-quarter-front view, keep its identity fixed: the pink half is on the viewer's left, the gray-white half is on the viewer's right, the main chipped bite marks and jagged missing edge are on the outer left edge of the pink half, the upper-left pink corner is also worn down, and the two colors meet at an irregular near-vertical crack seam. The gray-white half is rounded but dirty, with graphite stains, old erased marks, and gray smudges; do not move the main missing chunk to the gray-white right side. 破橡皮 corrects, doubts, wipes false clarity, checks evidence, stops loops, or enters the “裂开了” state under pressure.

Eye identity rule:
烂笔头 always has tiny black dot eyes. 破橡皮 eyes must be two very short flat black horizontal strokes only. Do not swap their eye styles. For 破橡皮, do not draw eye whites, pupils, oval eye shapes, full eyelid shapes, eyelashes, big round eyes, surprised eyes, smile eyes, cute cartoon eyes, or emoji-like expressions. Variations must stay inside each character's own eye type: 烂笔头's dot eyes may become smaller or slightly offset under pressure; 破橡皮's short black line eyes may become uneven, broken, shorter, or one-eye-closed under pressure, but must remain short black strokes only.

Theme:
{正文配图主题}

Cognitive action:
{这张图要画的认知动作，不是概念名词}

Core idea:
{这张图要表达的核心意思}

Role split:
烂笔头: {它正在做什么}
破橡皮: {它正在做什么}
Visible traces:
{铅笔线 / 断芯 / 擦痕 / 灰屑 / 空白 / 证据单 / 裂缝}

Structure type:
{推出第一版 / 擦掉假清楚 / 证据回流 / 停止规则 / 重启空白 / 并行修正 / 失败分类 / 其他}

Composition:
{具体画面：角色在哪里、正在做什么、主要物件是什么、信息如何流动}

Suggested elements:
{元素1} / {元素2} / {元素3} / {元素4}

Chinese handwritten labels:
{标注词1} / {标注词2} / {标注词3} / {可选标注词4} / {可选标注词5}

Color use:
Black for main line art, structure, main text, and graphite traces. Muted yellow and wood beige for 烂笔头. Dull gray-pink and dirty gray-white for 破橡皮. Orange only for main flow, path, arrows, or A-to-B movement. Red only for key warnings, errors, danger, stop signals, broken tips, cracks, or bad results. Blue only for evidence notes, feedback, system states, secondary notes, or local object annotations. Green only for verified, kept, passed, usable, or continue marks; use rarely. Purple only for hidden model guesses, latent states, or uncertain intermediate states in AI/model-mechanism illustrations; use very rarely. Color is semantic, not decorative; use 1-2 annotation colors in most images, 3 at most.

Blue annotation rule:
Do not default to “blue text plus a downward arrow.” If the blue label is close to the object, use local annotation: place the label near the object and, if needed, add only one very short thin blue handwritten underline beneath the text or along the object edge. If the object is far from the label or direction must be explicit, use a short thin slightly curved blue hand-drawn arrow with an open two-stroke arrowhead. Do not use floating ticks, ambiguous corner marks, closed circles, full frames, target marks, or cast-list-like boxes.

Constraints:
One image explains only one cognitive action or core structure. Keep the main subject around 40%-60% of the canvas. Preserve at least 35% blank white space. Use 3-6 short handwritten Chinese labels. Do not write a title in the top-left corner. Do not write the structure type on the image. Do not make it a formal diagram, course slide, dense explainer, or UI screenshot. Do not draw a fresh full pencil. Do not draw an intact clean eraser. Do not make cute children's stationery mascots. Do not copy model-sheet poses or legacy Xiaohei compositions. It should be clear but not instructional, strange but clean.
```

## 单角色正文配图模板

```text
Generate one standalone 16:9 horizontal Chinese article illustration in Figthus style.

Use only {烂笔头 / 破橡皮} as the active character because the cognitive action is {开始/外化/第一版/试错 OR 擦改/证据/校准/停止/裂开了}.

Role decision:
Use only {烂笔头 / 破橡皮} because {这个核心动作只属于这一方}. Do not draw the other character as a character. The absent character's force must still be visible through traces: {铅笔线 / 擦痕 / 灰屑 / 空白 / 断芯 / 证据单}.

Follow the same visual DNA and constraints as the duo template.

Theme:
{正文配图主题}

Cognitive action:
{这张图要画的认知动作}

Composition:
{具体画面}

Chinese handwritten labels:
{3-5 个短标注}
```

## 图像编辑提示

### 去掉左上角标题

```text
Edit the provided image. Remove only the handwritten title "{要删除的文字}" and its underline from the top-left corner. Fill that area with the same clean white background, matching the surrounding blank page. Preserve everything else exactly: characters, labels, paths, line style, composition, aspect ratio, and image quality. Do not add any new text or objects.
```

### 修正文案

```text
Edit the provided image. Replace only the handwritten label "{错误文字}" with "{正确文字}". Preserve the same small handwritten style, color, line quality, character positions, composition, and white background. Do not add any new objects.
```

### 明确出场逻辑

```text
Regenerate this illustration with the same core meaning and simple layout, but make the character logic clearer. Use both characters only if both are doing distinct work. Otherwise keep only the character that owns the main cognitive action, and show the absent character's force through traces such as pencil lines, eraser dust, blank space, broken graphite, or an evidence slip. Keep it sparse, white, hand-drawn, damaged, deadpan, and not cute.
```

### 让破橡皮进入“裂开了”状态

```text
Edit or regenerate the image while preserving the same composition and core meaning. Make 破橡皮 enter the high-pressure “裂开了” state: its broken pink and gray-white halves split along the irregular seam, with chipped edges and graphite dust. Do not use rope or external binding. Keep the character skeptical and tired, not cute.
```
