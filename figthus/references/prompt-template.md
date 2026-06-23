# 生图提示词模板

每张图单独生成。根据正文内容替换变量，不要把多张图拼在一起。

## 双角色正文配图模板

```text
Generate one standalone 16:9 horizontal Chinese article illustration.

Visual DNA:
Pure white background. Minimalist black hand-drawn line art. Slightly wobbly pen lines. Lots of empty white space. Sparse red/orange/blue handwritten Chinese annotations. Clean absurd product-sketch feeling. Lowly damaged desk-tool mood. No gradients, no shadows, no paper texture, no complex background, no commercial vector style, no PPT infographic look, no cute stationery mascot poster, no children's illustration, no realistic UI.

Recurring IP characters required:
烂笔头: a nearly used-up pencil stub, short, skinny, angled forward, dirty muted yellow paint, exposed rough wood, blunt crooked graphite tip that may snap, tiny thin legs, dot eyes, stubborn serious expression. Tail has a clearly visible oversized bent silver metal ferrule with 2-3 crimp rings and a tiny almost-used-up gray-pink eraser cap. 烂笔头 makes the first mark, pushes a draft forward, or externalizes the idea.

破橡皮: a broken eraser fragment, squat, blunt, dirty pink-gray and gray-white two-material body, both halves damaged, jagged chipped pink side, missing corner, graphite stains, old erased marks, irregular crack seam, tiny short legs, half-lidded skeptical eyes. 破橡皮 corrects, doubts, wipes false clarity, checks evidence, stops loops, or enters the “裂开了” state under pressure.

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
Black for main line art and graphite traces. Muted yellow and wood beige for 烂笔头. Dull gray-pink and dirty gray-white for 破橡皮. Orange only for main flow/path/arrows. Red only for key warnings/problems/results/cracks. Blue only for evidence notes, feedback, or secondary notes.

Constraints:
One image explains only one cognitive action or core structure. Keep the main subject around 40%-60% of the canvas. Preserve at least 35% blank white space. Use 3-6 short handwritten Chinese labels. Do not write a title in the top-left corner. Do not write the structure type on the image. Do not make it a formal diagram, course slide, dense explainer, or UI screenshot. Do not draw a fresh full pencil. Do not draw an intact clean eraser. Do not make cute children's stationery mascots. Do not copy model-sheet poses or legacy Xiaohei compositions. It should be clear but not instructional, strange but clean.
```

## 单角色正文配图模板

```text
Generate one standalone 16:9 horizontal Chinese article illustration in Figthus style.

Use only {烂笔头 / 破橡皮} as the active character because the cognitive action is {开始/外化/第一版/试错 OR 擦改/证据/校准/停止/裂开了}.

The absent character's force must still be visible through traces: {铅笔线 / 擦痕 / 灰屑 / 空白 / 断芯 / 证据单}.

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

### 增强角色分工

```text
Regenerate this illustration with the same core meaning and simple layout, but make the role split clearer: 烂笔头 should visibly create or push the first trace, while 破橡皮 should visibly correct, erase, check evidence, or stop the wrong path. Keep it sparse, white, hand-drawn, damaged, deadpan, and not cute.
```

### 让破橡皮进入“裂开了”状态

```text
Edit or regenerate the image while preserving the same composition and core meaning. Make 破橡皮 enter the high-pressure “裂开了” state: its broken pink and gray-white halves split along the irregular seam, with chipped edges and graphite dust. Do not use rope or external binding. Keep the character skeptical and tired, not cute.
```
