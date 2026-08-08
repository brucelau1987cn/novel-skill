# novel-skill

**English** | [中文](./README.zh-CN.md)

Hermes-compatible **optional skill** for planning, drafting, diagnosing, and revising **Chinese commercial web fiction** (网文).

Skill name: `commercial-web-fiction-writing`  
Author: Bruce Lau ([brucelau1987cn](https://github.com/brucelau1987cn)) + Hermes Agent  
License: MIT

## What it does

Treats market fit, platform fit, story architecture, emotional value, and prose execution as **one system**:

| Stage | Capability |
|---|---|
| Topic selection | Platform taste, hot/cold tracks, newcomer-safe picks, micro-innovation |
| Packaging | Title, blurb, tags, promise alignment |
| Opening / first 3 chapters | Sell-point, conflict, emotion, logic, signing-oriented openings |
| Structure | Long hooks / short hooks, nested goals, escalation |
| Character & romance | Stable characterization, pursuit-and-regret arcs, redemption boundaries |
| Chapter production | IAA / free-ad chapter range (≈2000–2500 chars), honest chapter-end hooks |
| Diagnosis | Rejection feedback → `删/缩/移/强化/重建` revision ops |
| Long-form control | Story bible, voice cards, timeline, foreshadowing & info-gap ledgers |
| Live research | Public chart/chapter sampling (Qimao-oriented protocol), mechanism extraction (no copying) |
| Prose gate | De-AI language pass, subjective viewpoint, continuity + payoff checks |

## Layout (Hermes optional-skill shape)

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

This mirrors Hermes Agent's `optional-skills/<category>/<name>/` convention so the package can later be proposed upstream under `optional-skills/creative/`.

## Install into Hermes Agent

### Option A — manual copy (works today)

```bash
# from a clone of this repo
mkdir -p ~/.hermes/skills/creative
cp -R commercial-web-fiction-writing ~/.hermes/skills/creative/
```

Then start a **new** Hermes session (skill loaders are cached at session start) and ask it to load:

```text
skill_view(name='commercial-web-fiction-writing')
```

### Option B — future official path

If / when this skill is accepted into the Hermes Agent tree as an optional skill:

```bash
hermes skills install official/creative/commercial-web-fiction-writing
```

(Exact install command depends on the Hermes version you run; prefer the live Hermes docs.)

## When to use

Load this skill when the task involves any of:

- 选题 / 书名 / 简介 / 标签
- 开篇、前三章、大纲、章纲
- 钩子、节奏、爽点/虐点
- 审稿、拒稿意见解析
- 长篇稳定连载与项目台账
- 公开榜单/章节的可迁移写法研究

**Don't use for:** pure literary workshop critique with no commercial/serial constraints; non-Chinese fiction unless you deliberately adapt the contracts.

## Core rules (one screen)

1. **One reader promise** across title → blurb → tags → opening → main plot → chapter hooks.
2. Main plot: `goal → obstacle → action → consequence` (payoff unit may expand with a pre-planted reversal).
3. Hooks: plant early, pay slowly, re-tease, **always cash out**; open dense, multi-line parallel, cut chapters before the reveal.
4. First 3 chapters (platform-observed pattern): old state fails → action proves change → long-term task engages.
5. Pleasure often = **regaining decision rights**, not only face-slapping; prefer emotional evidence objects over labels.
6. Character behavior follows background, desire, knowledge, temperament, limits. Change needs trigger, resistance, cost, sustained proof.
7. Before delivery: continuity / causality / payoff check, then a separate de-AI language pass.

## Compliance & research boundaries

- **Do not copy, paraphrase-wash, or recombine signature scenes, prop chains, or unique causal sequences from source novels.** Extract transferable **mechanisms** only.
- Public chart and free-chapter research normally needs **no login**. If an account-only action is truly required, the user controls the phone + SMS code; never store phone numbers, OTPs, cookies, or user-bound tokens.
- User-pasted HAR / Stream / curl captures are **forensic evidence of what the user saw**, not live credentials. Parse public shape only; never extract or replay `Cookie` / platform tokens.
- Chart ranks and platform policies are **time-sensitive**. Always re-check the live source and attach the check date.

## Upstream contribution note

This repo is the **public standalone** form. A future PR into [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) (or the current official tree) should place the skill at:

```text
optional-skills/creative/commercial-web-fiction-writing/
```

and follow the repo hardline authoring standards (description ≤ 60 chars, human-first author credit, tests, docs regen, no machine-local paths). This package already targets those constraints.

## Version

- `0.1.0` — initial public release of the working Hermes user-local skill, sanitized for open distribution.

## License

MIT — see [LICENSE](./LICENSE).
