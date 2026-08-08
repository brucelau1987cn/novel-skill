# Chart Research → Technique Extraction Protocol

Use this when the task is "read what's readable on a platform chart and turn it into a writing-technique ledger" (read top female/male hot-chart and new-book-chart works, extract techniques, update the writing manual). Distinct from `qimao-live-reading-and-research.md` (which governs access/credential/copyright rules). Both should be loaded together for Qimao work.

## 1. Sample Selection

- Cover at least 3 genre quadrants so the comparative axis is meaningful. Default mix for Qimao: 现言追妻 + 古言宅斗 + 玄幻/玄学爽文 + 年代重生 + 种田经营 + 无限流/规则文. For male charts substitute 都市高武 + 战神/神医 + 赘婿/重生 + 鉴宝/年代 + 玄幻/系统流.
- Mix mature long-form and recent new-book samples so observed patterns are not just "what the platform once rewarded" but "what it is rewarding now."
- Note each sample's chart position, age, sign-state, and current chapter count alongside the chapters read. These shape whether a finding is structural or trend-driven.

## 2. Boundary Detection (do this before writing any analysis)

Treat "readable" as a strict per-chapter check, not a per-work claim. The three evidence sources that *do not* prove the chapter is unlocked:

- HTTP 200. A 200 from `https://www.qimao.com/shuku/<book>-<chapter>/` means a page rendered, not that the chapter text is present.
- A chapter heading (`<h2>第N章 …</h2>`). Headings are visible on the login-wall stub page.
- A `下一章` link. The next link is rendered on the stub, pointing to the next chapter ID even when the current one is locked.

The three signals that *do* prove the chapter is unlocked and read for research:

1. The literal phrase `我已是会员，立即登录` is **absent** from the page text.
2. The `chapter-detail-article` container has substantive `<p>` content (typically >1,500 characters of clean text for Qimao IAA chapters).
3. At least one protagonist name (or other named entity specific to the work) appears in that text.

Record the boundary per work as: `last_unlocked=N, first_locked=M (reason: wall marker present, or empty article, or both)`. Never claim "read up to chapter X" if the chapter X article was empty.

## 3. Endpoint Map (Qimao, observed)

- **Mobile H5 API** `GET /qimaoapi/api/h5/v1/book/chapter-content-list?book_id=<id>&start=<n>&limit=<n>` — returns the first free slice only. For Qimao this is consistently **6 chapters** regardless of `start`/`limit`. Use it as a quick structural check, not a long read.
- **Mobile work page** `m.qimao.com/shuku/<id>/?hasNavBar=false&full_screen=3` — embeds the first 6 chapters inline in the SSR HTML; same boundary as the API.
- **Desktop chapter page** `www.qimao.com/shuku/<book>-<chapter-id>/` — exposes a longer, **book-specific** trial. The boundary is not the same as the mobile/API boundary. Sample-observed desktop trial lengths (Qimao, 2026-07-18): 《盖世神医》 1–59 unlocked, 60 = first locked; 《封总》 1–20, 21 = first locked; 《朱门春闺》 1–20, 21 = first locked; 《皇叔》 1–18, 19 = first locked; 《领证日》 1–19, 20 = first locked; 《西北种粮仓》 1–15, 16 = first locked. The pattern "20-ish" is not a platform rule; treat each work as a separate probe.
- **Desktop work page HTML** (`/shuku/<id>/`) does **not** embed the full chapter list. Full catalogue is not publicly enumerable without authenticated API access.

## 4. The "follow 下一章" protocol

- Never construct chapter URLs by appending a guessed integer to the work ID. Chapter IDs are not sequential.
- Begin from the public "开始阅读" entry point or from a chapter URL you already know is unlocked, then walk by reading the `下一章` href out of each page.
- One `上一页` (previous page) often appears next to a `下一章` link; use only the `下一章` href.
- Stop the walk at the first page that fails the boundary check in §2. Record the first locked chapter ID — not the last unlocked one — as the true boundary.

## 5. Capture Protocol (what to keep, what not to keep)

For each unlocked chapter, capture only the **evidence ledger** needed to support claims:

- `chapter` (1-indexed)
- `title` (full, as displayed)
- `chars` (clean-text length after stripping tags/scripts)
- `paragraphs` (count of `<p>`)
- `dialogue_ratio` (characters inside `“ ”` or `『 』` ÷ total)
- `entity_mentions` (counts of the main protagonist, key partner, key antagonist)
- `opening_snippet` (~60 chars, drop the boilerplate "本书授权七猫进行电子制作与发行" if present)
- `closing_snippet` (~60–80 chars)
- `chapter_end_kind` (硬切 / 闭合 + 行动预告 / 关系判断 / 情绪余韵 / 新信息 / 人物介入)

Do **not** keep: full chapter text, the raw HTML, raw `<p>` arrays, or any token/cookie values. The evidence ledger is sufficient to back up every claim in the analysis. When the technique is "this is a 三连击 opening," you need titles + opening snippets, not the chapter body.

Persist ledgers as a single JSON file per research session (e.g. `qimao-chart-ledger-2026-MM-DD.json`) so a follow-up session can re-analyze without re-fetching.

## 6. Cross-Sample Synthesis

The goal is not a per-work summary. It is a set of **reusable writing rules** that hold across samples. Build them in this order:

1. **Engine relay** (1–3, 4–10, 11–20 windows): what changes between windows, what is the second engine, when does the first close.
2. **Five-variable progression** (information / relationship / resource / map / cost): whenever the same conflict recurs, what is the variable that changed.
3. **Payoff rotation** (`D / R / A / S / K` = decision / relationship / ability / resource / cognition): tag each chapter's payoff and check for one-type-only patterns.
4. **Promise debt** (title → preview → first verification → stage payoff → full payoff): each title-and-preview promise is a debt; track when each is paid.
5. **Protagonist four rights** (find / choose / act / bear): for each decisive beat, the protagonist holds all four, the male lead assists, the magic assists, the system does not carry the function.

If a finding appears in only one work, label it `single-sample` and do not promote it to a general rule. Promotion to a rule requires at least two samples in different genres, or one sample with explicit second-source confirmation in the editor/七猫 course material the user has shared.

## 7. Male vs Female Channel (cross-axis)

Add a male/female comparison only when the chart mix includes both channels. Observable differences (sample as of 2026-07-18, drawn from live public chart reads of both channels):

- **Chapter length**: male 1.95–2.6k, female 2.0–2.5k — both within IAA range; male skews tighter.
- **Chapter titles**: male short, hard, cycle among 招数 / 美女 / 事件 every 5–8 chapters (functions as a level-progress bar); female longer, cycle among 关系判断 / 情绪词 / 外部任务.
- **Chapter endings**: male 95%+ close on a `。` or a `”`, using "protagonist has decided to do X" as the carry-over; female commonly hard-cuts mid-sentence or on a relationship judgment.
- **Dialogue vs interiority**: male ≈ 1/4 to 1/3 dialogue, 15-char-or-less command-style taglines common; female ≈ 1/3 to 2/5, with extended interiority.
- **First-chapter density**: male often packs "betrayal + suppression + awakening" in chapter 1; female usually breaks the old state in chapter 1 but defers ability/resource/new-relationship until chapters 4–10.
- **Payoff composition**: male bundles ability-payoff + antagonist-punishment + flirtation-promise into one beat; female separates decision-right, relationship, and dignity/cognition payoffs into independent beats.

## 8. User-Evidence Priority (correction learned this session)

When the user pastes live evidence (capture, command output, screenshot text), treat it as **primary**. The most common failure mode in this domain has been self-scans that contradict user evidence, where the agent repeats the self-scan conclusion anyway. Rules:

- If the user's pasted evidence describes a state (`unit found`, `service active`, `chapter readable`), it overrides your local scan until you can re-verify.
- Re-verify before repeating. A single re-scan after a contradiction is cheap; repeating the wrong conclusion is expensive.
- When the user specifies a host (`I'm on 180.152.19.204`) and your scan shows a different state, treat the host identity as the variable — confirm you are SSH'd into the right machine before drawing any conclusion about what's installed there.
- If a "browser says X, CLI says not-X" split appears (this is exactly what happened with Qimao's paywall stub), name both views explicitly: "browser: 我已是会员, 立即登录 marker present; CLI: 0 `<p>` content, no wall marker." The reader can then judge the situation without you arbitrating it.

## 9. Output Shape

When the user asks for chart reading + technique extraction, the deliverable is:

1. A **per-work structural read** (1–3, 4–10, 11–boundary) grounded in the evidence ledger, not free recall.
2. A **cross-sample synthesis** with reusable rules.
3. A **risks** section that names specific things *not* to copy (e.g., extreme antagonist passivity in 追妻文, no-cost space in 重生文, manager-driven rules in 怪谈文).
4. A **diff** that the user can read in one pass: which existing writing-manual rules to add, which to qualify, which to leave.

Do not produce a long per-chapter recap. The evidence ledger already has the chapter-level data; the report's job is the cross-cutting rules, not the per-chapter summary.
