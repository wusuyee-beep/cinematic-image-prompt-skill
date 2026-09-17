# 电影感生图提示词 Skill

面向 Claude Code / Codex 的中文生图提示词 Skill。它把简短画面想法整理成主体明确、空间稳定、光线可执行、色彩干净的生成提示词，适用于真人电影感、纪实摄影、动漫插画、概念场景、建筑室内和电商产品图。

本项目不是形容词词库。它先解决主体数量、属性绑定、左右前后关系、视觉中心和光源逻辑，再选择机位、景别、视场、景深、色彩、影调与材质，减少 AI 生图常见的漏主体、串颜色、错位置、灰图、脏色和过度锐化。

## 核心能力

- 把一句画面想法补全为可直接使用的中文提示词
- 区分机位、拍摄距离、景别、视场、焦段倾向与透视
- 处理多主体数量、位置、动作和属性绑定
- 设计有来源、有方向、有作用的光线
- 分开色彩关系、饱和度与明暗影调
- 处理参考图职责、画中文字、产品材质和系列一致性
- 根据当前画面生成针对性负向约束
- 通过 100 分审核表自动复核，不合格先改写

## 安装

### Claude Code

```bash
git clone https://github.com/wusuyee-beep/cinematic-image-prompt-skill.git ~/.claude/skills/cinematic-image-prompt
```

### Codex

把仓库复制或链接到 Codex Skills 目录，并保留 `agents/openai.yaml`。

## 使用

```text
使用 $cinematic-image-prompt，把“一个女孩在雨夜公交站等人”改写成电影感生图提示词。
```

```text
使用 $cinematic-image-prompt，按照参考图的人物身份和另一张图的构图，写一版多人写实摄影提示词。
```

用户只要求写提示词时，Skill 不会调用生图工具；只有明确提出“生成图片”“直接出图”或“渲染”时才进入生成流程。

## 结构

```text
cinematic-image-prompt/
├── SKILL.md
├── agents/openai.yaml
├── evals/evals.json
└── references/
    ├── prompt-architecture.md
    ├── visual-language.md
    ├── model-failures.md
    ├── review-rubric.md
    ├── examples.md
    └── sources.md
```

## 方法依据

摄影与视觉语言部分参考 Blain Brown、Bruce Block、Joseph V. Mascelli 与 Kodak 的专业资料；生成方法参考 Google Imagen 官方指南，以及 DOCCI、LayoutGPT、Attend-and-Excite 等关于详细描述、布局规划、主体遗漏与属性绑定的研究。完整来源见 `references/sources.md`。

