# novel-skill

[English](./README.md) | **中文**

面向 [Hermes Agent](https://github.com/NousResearch/hermes-agent) 的 **optional skill**：用于**中国商业网文**的选题、开篇、结构、章节生产、审稿诊断与长篇连载控制。

- Skill 名：`commercial-web-fiction-writing`
- 作者：Bruce Lau ([brucelau1987cn](https://github.com/brucelau1987cn)) + Hermes Agent
- 许可证：MIT

## 能做什么

把市场适配、平台口味、故事架构、情绪价值、文笔执行当成**同一套系统**处理：

| 阶段 | 能力 |
|---|---|
| 选题 | 平台口味、冷热赛道、新人安全选题、微创新 |
| 包装 | 书名、简介、标签、读者承诺对齐 |
| 开篇 / 前三章 | 卖点、冲突、情绪、逻辑、抢签向开篇 |
| 结构 | 大钩子 / 小钩子、嵌套目标、剧情升级 |
| 人物与感情 | 人物稳定、追妻/后悔线、洗白边界 |
| 章节生产 | IAA / 无线流章节篇幅（约 2000–2500 字）、诚实的章末钩子 |
| 诊断改稿 | 拒稿意见 → `删/缩/移/强化/重建` |
| 长篇控制 | 故事圣经、人物语音卡、时间线、伏笔与信息差台账 |
| 实证调研 | 公开榜单/章节采样（偏七猫协议）、只提炼机制不抄文 |
| 文风闸门 | 去 AI 痕迹、主观视角、衔接与兑现复检 |

## 目录结构（Hermes optional-skill 形态）

```text
novel-skill/
├── README.md
├── README.zh-CN.md
├── LICENSE
└── commercial-web-fiction-writing/
    ├── SKILL.md
    └── references/
        ├── market-and-topic-selection.md
        ├── hooks-and-reader-expectation.md
        ├── opening-and-signing.md
        ├── focus-and-revision-diagnostics.md
        ├── goal-driven-plot-and-conflict.md
        ├── character-and-emotional-arcs.md
        ├── prose-voice-and-final-quality-gate.md
        ├── iaa-wireless-chapter-design.md
        ├── long-form-project-control.md
        ├── qimao-live-reading-and-research.md
        ├── chart-research-technique-extraction.md
        ├── early-serial-arc-research.md
        ├── mechanism-based-close-reading.md
        └── evidence-calibrated-opening-patterns.md
```

该结构对齐 Hermes 的 `optional-skills/<category>/<name>/` 约定，便于后续向上游 `optional-skills/creative/` 提案。

## 安装到 Hermes Agent

### 方式 A：手动复制（当前即可用）

```bash
# 在本仓库根目录执行
mkdir -p ~/.hermes/skills/creative
cp -R commercial-web-fiction-writing ~/.hermes/skills/creative/
```

然后**新开** Hermes 会话（skill 加载器在会话启动时缓存），再加载：

```text
skill_view(name='commercial-web-fiction-writing')
```

### 方式 B：未来官方路径

若该 skill 被收入 Hermes Agent 官方 optional 树：

```bash
hermes skills install official/creative/commercial-web-fiction-writing
```

（以你本机 Hermes 版本与官方文档为准。）

## 什么时候用

出现以下任务时加载本 skill：

- 选题 / 书名 / 简介 / 标签
- 开篇、前三章、大纲、章纲
- 钩子、节奏、爽点 / 虐点
- 审稿、拒稿意见解析
- 长篇稳定连载与项目台账
- 公开榜单 / 章节的可迁移写法研究

**不适合：** 无商业/连载约束的纯文学工作坊批评；非中文小说（除非你主动改写契约）。

## 核心规则（一屏版）

1. **同一条读者承诺**贯穿：书名 → 简介 → 标签 → 开篇 → 主线 → 章末钩子。
2. 主线：`目标 → 障碍 → 行动 → 后果`（爽点单元可扩展为预埋反转后再回收）。
3. 钩子：早埋、慢收、反复撩、**必须兑现**；开篇密抛，多线并行，章末卡在揭晓前。
4. 前三章（平台观测模式）：旧状态失效 → 行动证明改变 → 接入长期任务。
5. 爽点常等于**夺回决策权**，不只是打脸；优先用可触摸的情绪物证，少贴抽象情绪标签。
6. 人物行为服从背景、欲望、信息、性格、限制；改变需要触发、抵抗、代价、持续证明。
7. 交付前：先查衔接 / 因果 / 兑现，再单独做去 AI 语言复检。

## 合规与调研边界

- **禁止**搬运、洗稿、复刻标志性场景、完整道具链或独特因果链。只提炼可迁移**机制**。
- 公开榜单与免费章节研究通常**无需登录**。若确需账号操作，由用户控制手机号与短信验证码；不得存储手机号、OTP、Cookie 或用户绑定 token。
- 用户粘贴的 HAR / Stream / curl 捕获是**取证材料**（证明用户看到了什么），不是可重放凭证。只解析公开结构，不抽取、不重放 Cookie / 平台 token。
- 榜单位次与平台政策会变。每次以**实时页面**为准，并标注检查日期。

## 上游贡献说明

本仓库是**独立公开版**。若向 [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent)（或当前官方树）提交 PR，建议路径为：

```text
optional-skills/creative/commercial-web-fiction-writing/
```

并遵守官方硬线规范（description ≤ 60 字符、作者先写人、测试、文档生成、无机器本地路径）。本包已按这些约束整理。

## 版本

- `v0.1.0` — 首个公开发布：工作版 Hermes 用户 skill 脱敏开源

## 许可证

MIT — 见 [LICENSE](./LICENSE)。
