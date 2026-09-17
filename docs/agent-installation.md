# 多 Agent 安装与兼容矩阵

本仓库只维护一份核心规则：根目录的 `SKILL.md`。原生支持 Agent Skills 的平台直接安装整个仓库；其他平台使用 `adapters/system-prompt.zh-CN.md`，避免多份规则长期漂移。

## 兼容级别

| 平台 | 兼容级别 | 安装入口 | 验证方式 |
| --- | --- | --- | --- |
| Codex | 原生 Skill | `~/.codex/skills/cinematic-image-prompt/` | 新会话中调用 `$cinematic-image-prompt` |
| Claude Code | 原生 Skill | `~/.claude/skills/cinematic-image-prompt/` | 新会话中调用 `/cinematic-image-prompt` 或提出匹配请求 |
| WorkBuddy | 平台转换适配 | 让 WorkBuddy 根据仓库创建自定义 Skill，再从 Skill Marketplace/安装流程启用 | 在 Skills 面板确认已启用，再提出匹配请求 |
| CodeBuddy Code | 原生 Skill | 用户级 `~/.codebuddy/skills/`；项目级 `.codebuddy/skills/` | 在 Skills 面板查看 User/Project skill |
| Qwen Code（千问） | 原生 Skill | 用户级 `~/.qwen/skills/`；项目级 `.qwen/skills/` | 输入 `/skills`，或 `/cinematic-image-prompt` |
| Qoder | 原生 Skill | Extensions → Skills → Add Skills → Upload Skill；CLI 也支持 `~/.qoder/skills/` | UI 中确认启用；CLI 输入 `/skills reload` |
| QoderWork 旧版 | 条件兼容 | 优先升级/迁移到新版 Qoder；旧客户端用能力或知识导入 | 用测试请求检查是否读取完整规则 |
| 豆包 | 系统提示词兼容 | 将适配版粘贴到自定义智能体/专家的系统指令；必要时把 `references/` 作为知识文件 | 用测试请求检查字段、负向约束和审核行为 |
| 其他 Agent | 自动判断 | 支持 `SKILL.md` 则安装整个目录；否则使用系统提示词适配版 | 运行文末测试请求 |

“原生 Skill”表示平台能发现 `SKILL.md` 并按需加载支持文件；“系统提示词兼容”表示核心写作行为可迁移，但不会自动按相对路径加载参考资料。

## 最省事的安装方式

### 方法一：让 Agent 自己安装

在 CodeBuddy、Qwen Code、Qoder、Claude Code 或 Codex 中发送：

```text
请从 https://github.com/wusuyee-beep/cinematic-image-prompt-skill 安装 cinematic-image-prompt Skill。
安装整个目录，不要只复制 SKILL.md；安装后检查 YAML frontmatter 和 references 相对路径，并用“一个女孩在雨夜公交站等人”做一次只输出提示词的测试。
```

### 方法二：社区 Skills 安装器

```bash
npx skills add wusuyee-beep/cinematic-image-prompt-skill -g
```

安装器能否自动识别目标 Agent 取决于其当前版本。安装完成后仍需检查目标目录和 `/skills` 列表。

## WorkBuddy 转换安装

WorkBuddy 当前官方文档描述的自定义 Skill 通常包含 `skill.yml`、实现文件和 README，并通过 WorkBuddy 自己的创建与安装流程管理；它与 CodeBuddy 的 `SKILL.md` 目录不能视为完全相同。

在 WorkBuddy 新任务中粘贴 [`adapters/workbuddy-setup.md`](../adapters/workbuddy-setup.md) 的安装指令。让 WorkBuddy读取仓库的核心规则和参考资料，转换为当前客户端认可的 Skill 包，再在 Skill Marketplace/Skills 页面确认安装与启用。

### 方法三：手动复制

```bash
git clone https://github.com/wusuyee-beep/cinematic-image-prompt-skill.git cinematic-image-prompt
```

然后把整个 `cinematic-image-prompt/` 目录复制到对应平台的用户级 Skills 目录。不要只复制入口文件，因为审核表、案例和专业规则位于 `references/`。

## Qoder 的手机友好安装

1. 在 GitHub 仓库页面选择 **Code → Download ZIP**。
2. 在 Qoder 打开 **Extensions → Skills → Add Skills → Upload Skill**。
3. 上传 ZIP；若客户端只接受单个文件，也可以上传根目录 `SKILL.md`，但这会缺少参考资料，不推荐。

Qoder 官方说明支持上传 Skill ZIP 或单个 `SKILL.md`；ZIP 根目录应能找到 `SKILL.md`。

## 豆包与不支持 SKILL.md 的平台

1. 打开自定义智能体、专家或角色的系统指令设置。
2. 复制 [`adapters/system-prompt.zh-CN.md`](../adapters/system-prompt.zh-CN.md) 中代码块的全部内容。
3. 如果平台支持知识文件，再上传 `references/` 中与任务有关的文件。
4. 不要把 GitHub README 当作系统提示词；README 面向人类，包含安装和项目说明。

## 安装后测试

### 正常用例

```text
把“一个女孩在雨夜公交站等人”改写成真人电影感生图提示词。只写提示词，不生成图片。
```

应得到一个明确视觉中心、空间布局、可信光源、色彩影调和针对性负向约束，且不会调用生图工具。

### 边界用例

```text
两个人在厨房，左侧红衣女性递出一个白杯，右后方蓝衣男性伸手接，桌上恰好三只青苹果。
```

检查人物数量、衣服颜色、前后位置、左右手、杯子和苹果数量是否分别绑定，没有把属性混在一起。

## 官方依据

- Agent Skills 开放格式：https://agentskills.io/home
- CodeBuddy Skills：https://www.codebuddy.ai/docs/cli/skills
- Qwen Code Agent Skills：https://qwenlm.github.io/qwen-code-docs/zh/users/features/skills/
- Qoder Skills：https://docs.qoder.com/qoder/skills
- Qoder CLI Skills：https://docs.qoder.com/cli/Skills
- WorkBuddy：https://www.workbuddy.ai/
- WorkBuddy Skill Marketplace：https://www.workbuddy.ai/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market
- WorkBuddy Creating Custom Skills：https://www.workbuddy.ai/docs/workbuddy/From-Beginner-to-Expert-Guide/Practice-Cases/Create-Skills

WorkBuddy 当前官方格式与开放 `SKILL.md` 格式不同，因此标为转换适配。豆包目前未检索到可核验的第三方 `SKILL.md` 官方导入规范，因此只承诺系统提示词兼容，不声称原生安装。
