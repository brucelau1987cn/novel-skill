---
name: commercial-web-fiction-writing
description: Plan and revise Chinese commercial web fiction.
version: 0.2.0
author: Bruce Lau (brucelau1987cn), Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [web-fiction, chinese-novel, hooks, openings, revision, qimao, engines]
    category: creative
    related_skills: []
---

# Commercial Web Fiction Writing

## Purpose

Produce Chinese web fiction that makes a clear reader promise, creates sustained expectation, and can support a long-form story. Treat market fit, platform fit, story architecture, emotional value, and prose execution as one system.

## Default Workflow

1. Identify the target platform, audience, category, and expected emotional experience.
2. State in one sentence each: protagonist's core goal, deep motive, and unique selling point.
3. Classify the project as traditional, hot, distinctive, or sensitive/high-risk. For inexperienced authors, favor a familiar mainstream category with micro-innovation or a supported platform contest.
4. Study the target platform's hot list, new-book list, and category list. Read representative works beyond the opening and extract the full framework, recurring conventions, pacing, and reader contract. When studying the first 15–20 chapters, load `references/early-serial-arc-research.md`; verify the true readable boundary per work, then analyze chapters 1–3, 4–10, and 11–20 as engine-relay windows rather than retelling every chapter.
5. Define the long-term hook, current-stage task, opposition, and planned payoff nodes before drafting. For goal-driven work, split the long-term goal into necessary short-term tasks and specify full rewards, deadlines, obstacles, reversals, and transitions.
6. Identify the primary story engine: emotional/relationship flow or external plot/task flow. They may reinforce each other, but one should organize the narrative unless the author can sustain a deliberate balance. For the first six chapters, also pick **one** opening engine from `references/opening-engine-catalog-first-six.md` (female/ancient tracks) or `references/male-opening-engines.md` (male tracks). Do not run three opening engines at full load.
7. Align title, blurb, tags, opening, main plot, and chapter hooks around the same promise.
8. Draft the opening through conflict, crisis, choice, or relationship change. Reveal setting through action rather than static explanation. Inside chapter 1, make the old state fail and force a new choice.
9. Review every scene and paragraph for necessity, focus, emotional concentration, character consistency, and continuity of expectation. When a conflict recurs, change information, relationship, resource, map, or cost.
10. Translate vague editorial feedback into observable defects and concrete revision operations.
11. For long-form work, maintain a story bible, character/voice cards, timeline, hook/foreshadowing ledger, and information-gap ledger. Use a three-chapter review loop and broader ten-chapter/volume reviews. Treat 1–3 / 4–10 / 11–20 as elastic engine-relay windows.
12. Before delivery, reread the actual prose for continuity and story completeness, then perform a separate de-AI language pass. A keyword scan alone is not sufficient.
13. Verify that hooks are tracked and eventually paid off, while new expectations begin before old ones fully close. Pleasure units should restore decision rights, not only deliver face-slapping.

## Default Prose and Delivery Gate

For Chinese commercial web-fiction drafting, load and apply `references/prose-voice-and-final-quality-gate.md` before drafting or revising prose. Its requirements include:

- no stock AI transitions, summary fillers, textbook list framing, or polished mechanical parallelism;
- deliberately varied paragraph rhythm without turning single-sentence paragraphs into another template;
- concrete action, bodily response, object handling, and pressure-tested choice instead of abstract emotional labels;
- exact, forceful verbs and viewpoint-bound figurative language;
- a clearly subjective narrative filter rather than sterile neutrality;
- a final reread for time, space, knowledge, character state, causality, payoff, hooks, and banned/template language.

For IAA/free-ad-supported or wireless-flow fiction, also load `references/iaa-wireless-chapter-design.md`. Default to 2,000-2,500 characters per chapter, treat below 1,500 and above 3,000 as warnings, and never pad or sever a complete scene merely to hit a number.

## Core Rules

- The main plot follows `goal -> obstacle -> action -> consequence`; for a payoff unit, use `goal -> action -> obstacle -> reversal -> success/consequence` and plant the reversal before calling it back.
- The protagonist must make choices, trigger events, and bear consequences; do not let supporting characters carry the decisive story functions.
- Character behavior must follow established background, desire, knowledge, temperament, and limits. Change requires a visible trigger, resistance, choice, cost, and sustained proof; never lower intelligence or morality merely to prolong the plot.
- Every subplot, character, and setting element must advance the main plot, shape the protagonist, strengthen conflict, reveal essential information, or satisfy the genre's core expectation.
- Prefer action, pressure-tested choices, key dialogue, and physical detail over direct emotional labels or explanatory narration.
- Keep the opening and early-middle sections anchored to the protagonist's viewpoint. Use supporting viewpoints only when the information or emotion is indispensable, brief, and focused.
- Build climaxes through concentrated pressure, crisis, and expectation. At payoff, write the intended pleasure or pain fully rather than rushing past it.
- Maintain the genre and tonal promise. Do not pivot into a different core experience after attracting readers with another one.
- Commercial writing requires iteration and completion. Do not abandon a project solely because of one weak test or short-term data point without diagnosing the cause.

## Hook System

Use hooks at five levels:

- Title: wins the correct click by combining category convention, core attraction, and novelty.
- Blurb and tags: select the audience and establish the precise promise.
- Opening: creates an immediate crisis or disruption and demonstrates the promised experience.
- Main plot: sustains a pull with enough room for delayed payoff and repeated escalation.
- Chapter: completes the current action but leaves a consequence, reversal, clue, threat, or question unresolved.

A good expectation often lets readers anticipate the emotionally satisfying result while hiding the exact route to it. Control information among reader, protagonist, allies, and antagonists to create this gap.

## Revision Operations

Label each issue with an action:

- `删`: no meaningful function.
- `缩`: useful but overlong or repetitive.
- `移`: useful information appears at the wrong time.
- `强化`: the core conflict, emotion, choice, or payoff is underwritten.
- `重建`: goal, motive, causality, viewpoint, or reader promise is structurally broken.

For each finding, report: location, observable problem, reader impact, revision action, and desired result. Avoid unsupported verdicts such as “节奏慢” or “人物扁平.”

## Qimao Live Research

When a task depends on current Qimao charts, public novels, openings, chapter lengths, contests, signing rules, or platform presentation, inspect the live source rather than relying on remembered examples. Load `references/qimao-live-reading-and-research.md`. Public chart and chapter research normally does not require login; only use phone + SMS authentication for genuinely account-only tasks, with the user controlling the one-time code and with no credential retention.

When the user pastes a forensic capture (Stream / HAR / curl log / journalctl dump) of the live site, treat it as evidence of what they saw, not as live credentials. Parse only the public shape — URLs, header keys, base64 device-fingerprinting bodies, and metadata of any token (issuer, exp claim, user-bound prefix) — never extract or replay `Cookie:` / `qimao-token` / `author-token`. Treat `author-token` (the user-bound `user:hex` value) as a password: do not echo, do not pass through shell arguments, and do not include it in any tool that does not strictly need it. For token lifetime checks, decode the JWT payload offline and report only coarse status (`expired=true/false`, remaining seconds) — never the raw claims. If continued authenticated access is required, ask the user to add a fresh SSH key, or to set a new cookie in their own browser, rather than reusing what they pasted.

When the user asks for "read what's readable on a chart and turn it into techniques," also load `references/chart-research-technique-extraction.md`. It encodes the per-book boundary protocol, the `下一章` walk, the evidence-ledger schema, the cross-sample synthesis order, and the male-vs-female cross-axis. It is the working companion to this section (which governs access, credentials, and copyright).

## References

- See `references/market-and-topic-selection.md` for category, platform, and topic-selection strategy.
- See `references/qimao-live-reading-and-research.md` for live Qimao chart sampling, public chapter reading, evidence ledgers, login boundaries, and copyright-safe analysis.
- See `references/chart-research-technique-extraction.md` for the per-book boundary protocol, the `下一章` walk, the evidence-ledger schema, cross-sample synthesis order, and the male-vs-female cross-axis. Use it whenever the task is "read what's readable on a chart and turn it into writing techniques."
- See `references/early-serial-arc-research.md` for evidence-safe 15–20 chapter comparative study, engine relay, five-variable progression, promise debt, payoff rotation, protagonist agency, and ability/resource ledgers.
- See `references/mechanism-based-close-reading.md` for contiguous comparative analysis of competence-to-plot conversion, public/hidden resource ledgers, rule lifecycles, information gaps, tone mixing, map continuity, payoffs, chapter endings, and recurring structural risks.
- See `references/evidence-calibrated-opening-patterns.md` for cross-sample opening hypotheses: the three-chapter gear shift, decision-right payoffs, emotional evidence objects, reciprocal power mechanisms, and evidence limits.
- See `references/hooks-and-reader-expectation.md` for the complete hook and information-gap system.
- See `references/opening-and-signing.md` for editor-facing opening and signing criteria.
- See `references/focus-and-revision-diagnostics.md` for focus checks and rejection-feedback translation.
- See `references/goal-driven-plot-and-conflict.md` for nested goals, payoff design, urgency, reversals, and competitive-conflict variables.
- See `references/character-and-emotional-arcs.md` for stable characterization, emotional vs plot flow, pursuit-and-regret romance, and credible villain softening/redemption.
- See `references/prose-voice-and-final-quality-gate.md` for the mandatory de-AI prose contract, subjective viewpoint, continuity checks, and final delivery gate.
- See `references/iaa-wireless-chapter-design.md` for the 2,000-2,500 chapter range, internal pacing map, and honest chapter-end retention hooks.
- See `references/long-form-project-control.md` for story-bible files, ledgers, three-chapter loops, volume reviews, and evidence discipline around platform claims.
- See `references/opening-engine-catalog-first-six.md` for the first-six-chapter opening-engine catalog (seven tracks), selection tree, skeletons, and acceptance checks.
- See `references/male-opening-engines.md` for male-channel openings: money-first historical, prison-return, and vessel-cast upgrade patterns.
