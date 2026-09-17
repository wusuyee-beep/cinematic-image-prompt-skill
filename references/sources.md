# 资料依据

## 专业视听语言与摄影

- Blain Brown, *Cinematography: Theory and Practice*. 涵盖构图、光线、色彩、曝光、镜头、景深与视觉叙事。https://books.google.com/books?id=uyMYMbjheqgC
- Bruce Block, *The Visual Story*. 以空间、线条、形状、明暗、色彩、运动与节奏建立视觉结构，并用对比/相近组织强度。https://www.routledge.com/The-Visual-Story-Creating-the-Visual-Structure-of-Film-TV-and-Digital/Block/p/book/9781138014152
- Joseph V. Mascelli, *The Five C's of Cinematography*. 核心为 camera angles、continuity、cutting、close-ups、composition；本 skill 仅迁移适用于静态画面的机位与构图原则。https://books.google.com/books?id=0gBMAQAAIAAJ
- Kodak, *The Essential Reference Guide for Filmmakers*. 摄影机、测光、光线、曝光与胶片技术参考。https://www.kodak.com/en/motion/page/essential-reference-guide-for-filmmakers/

## 生图模型与提示实践

- Google Cloud, *Prompt and image attribute guide*. 建议从主体、背景/语境和风格开始，通过迭代逐步增加有效细节。https://cloud.google.com/vertex-ai/generative-ai/docs/image/img-gen-prompt-guide
- Google Cloud, *A developer's guide to Imagen 3*. 官方实践强调主体安排、光线、角度/镜头和风格等明确描述。https://cloud.google.com/blog/products/ai-machine-learning/a-developers-guide-to-imagen-3-on-vertex-ai
- Onoe et al., *DOCCI: Descriptions of Connected and Contrasting Images*, ECCV 2024. 细粒度描述覆盖空间关系、计数、文字渲染和相似图差异。https://research.google/pubs/docci-descriptions-of-connected-and-contrasting-images/
- Feng et al., *LayoutGPT: Compositional Visual Planning and Generation with Large Language Models*, NeurIPS 2023. 支持先进行布局规划再生成复杂画面。https://proceedings.neurips.cc/paper_files/paper/2023/hash/3a7f9e485845dac27423375c934cb4db-Abstract-Conference.html
- Chefer et al., *Attend-and-Excite*, SIGGRAPH 2023. 指出主体遗漏与属性绑定错误是文本生图的常见失败。https://arxiv.org/abs/2301.13826

## 使用边界

教材中的镜头语言是创作语法，不是情绪词典。模型厂商的提示建议也不是跨模型保证。本 skill 将二者转化为可观察、可验证的画面约束，并通过交付前审核减少冲突。

