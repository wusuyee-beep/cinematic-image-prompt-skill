# WorkBuddy 转换安装指令

把下面内容发送给 WorkBuddy。它的作用是让 WorkBuddy 使用当前客户端自己的 Skill 创建流程，将本仓库转换为它认可的 `skill.yml` 包，而不是假设它会直接读取其他 Agent 的目录。

```text
请根据这个公开仓库创建并安装一个 WorkBuddy 自定义 Skill：
https://github.com/wusuyee-beep/cinematic-image-prompt-skill

要求：
1. Skill 名称使用 cinematic-image-prompt，显示名使用“电影感生图提示词”。
2. 以根目录 SKILL.md 为核心行为规则；同时读取 references/prompt-architecture.md、visual-language.md、model-failures.md、review-rubric.md 和 examples.md。
3. 将这些内容转换为当前 WorkBuddy 版本认可的 skill.yml、实现文件和 README；不要修改原有方法，不要把案例人物的年龄、服装、颜色或构图变成全局限制。
4. 默认只输出中文图片提示词。只有用户明确说“生成图片”“直接出图”或“渲染”时才调用生图能力；不要用于视频运镜或时序提示词。
5. 安装前展示将要创建的文件和权限；不需要网络、终端或敏感数据权限时不要申请。
6. 安装后用“一个女孩在雨夜公交站等人，只写提示词，不生成图片”测试；再用“两个人在厨房，左侧红衣女性递白杯，右后方蓝衣男性接，桌上恰好三只青苹果”检查数量和属性绑定。
7. 若当前版本无法从 GitHub读取仓库，告诉我需要下载或上传哪些文件，不要静默省略 references。
```
