# Qimao Live Reading and Market Research

Use this reference when the task requires current Qimao charts, title/blurb research, opening analysis, chapter sampling, or platform-rule verification.

## Access Pattern

1. Open `https://www.qimao.com/` and inspect the live home page before relying on old notes.
2. Public pages normally expose current category links, female/male hot charts, new-book charts, title/author entries, work pages, and readable chapter text.
3. Open the work page, then use `开始阅读`, `目录`, and `下一章` to inspect public chapters. Capture the displayed chapter title, chapter word count, update time, and text structure when relevant.
4. Prefer public access. Login is unnecessary for ordinary chart and public-chapter research.
5. If account-only behavior is genuinely required, Qimao web login uses a phone number plus SMS one-time code. The user must control the phone and provide the current code. Never store the phone number or OTP in memory/facts, never bypass verification, and never request login merely for convenience.

## Research Sequence

For a target category, sample both current hot works and recent new works:

- chart position and category;
- title formula and emotional promise;
- blurb, tags, protagonist, and stated premise;
- first three chapters: entry event, protagonist visibility, core conflict, emotional contract, hook, chapter length, and ending cut;
- selected middle chapters: goal continuity, relationship/plot movement, hook rotation, and repeated mechanisms;
- a late or current chapter: long-line stability, character consistency, and whether the opening promise still governs the story.

Do not infer a whole novel from chapter one alone. If a full-book claim is needed, read a representative structural sample or the relevant range.

## Analysis Ledger

For each sampled work, record:

| Field | Evidence |
|---|---|
| Title/category/chart | Live page and date checked |
| Reader promise | Title + blurb + opening |
| Primary engine | Emotional flow or plot flow |
| Long hook | Specific unresolved expectation |
| Opening event | What changes the protagonist's state |
| Chapter payoff | What the reader receives before the cut |
| Chapter-end hook | Crisis, reversal, clue, relationship turn, etc. |
| Distinctive element | Actual difference, not just keywords |
| Risks | Promise mismatch, repetition, weak agency, logic, etc. |

Separate observed evidence from interpretation. Current chart position and platform policy are time-sensitive facts; attach the check date and avoid turning them into permanent universal rules.

## Contiguous Multi-Chapter Close Reading

When the user requests a chapter-number-grounded reading of a contiguous range such as the first 20 chapters, do not substitute a representative sample.

1. Start from the supplied canonical chapter URL and follow each rendered `下一章` link. Do not manufacture later URLs from chapter numbers: timestamp-like URL segments can change between chapters.
2. Verify every page by its displayed chapter heading. Maintain `chapter number/title -> canonical URL` before interpreting the prose.
3. For each chapter, record a compact state-transition row:
   - opening relationship or task state;
   - event and causal consequence;
   - protagonist choice and decision right gained/lost;
   - relationship-state change;
   - emotional object or setting and what action it carries;
   - who knows what;
   - chapter payoff;
   - exact ending action/question and hook type;
   - repeated mechanism, if any.
4. Read in structural blocks such as `1-3`, `4-10`, and `11-20`, but preserve chapter-level evidence inside each block. This supports both local close reading and larger rhythm diagnosis.
5. Track promises as a ledger: `promise placed -> first action -> partial payoff -> delayed obstruction -> stage payoff -> successor hook`. A stated intention is not fulfillment until the character makes an observable choice that changes cost, access, duty, space, or relationship.
6. Track recurring objects across chapters. An object becomes structural evidence when it is created, allocated, withheld, discarded, transferred, or reinterpreted; note each return rather than analyzing only its first appearance.
7. Diagnose repetition by mechanism, not vocabulary. Examples include repeated withdrawal followed by surprise, repeated misunderstanding without new knowledge, or repeated provocation followed by the same restraint. State whether each recurrence escalates, reverses, pays off, or merely replays.
8. Compare works by engine and constraints, not surface props. End with transferable mechanisms, explicit differences, and elements that cannot be copied because they depend on a signature causal chain, period institution, character extremity, or unique object combination.
9. Cite real chapter numbers and short necessary textual evidence. Summarize the rest in original language; never assemble a substitute copy of the chapters.

For rendered pages whose prose is absent from generic extraction, inspect the public chapter DOM. If reading several chapters in page context, fetch the current chapter, parse its article container, take the actual `下一章` URL, and continue serially. Batch only after the canonical sequence is known; verify headings and stop on an empty article rather than silently treating it as a chapter.

## Copyright and Output Boundaries

- Read and analyze lawfully accessible pages.
- Quote only short passages necessary to support analysis.
- Do not reproduce full chapters or compile a substitute copy of the work.
- Summarize structure, techniques, pacing, and reader effects in original language.
- Use competitor research to learn category conventions, not to copy unique expression, character combinations, or complete causal chains.

## Practical Pitfalls

- A click may appear not to navigate when the title has multiple links; inspect the anchor URL and navigate directly to the work page when needed.
- Do not infer chapter order from a batch result's array positions. A work page may embed the full first chapter plus page metadata, followed by a separate clean first-chapter item; counting both shifts every later chapter. Verify the displayed chapter heading and URL, deduplicate by chapter identity, then follow each chapter's `next` link to establish the true sequence.
- When extracted work-page content includes scripts or is truncated, parse structured fields first to inspect URLs and `next` links rather than treating the entire blob as prose. Use the public chapter page's rendered DOM to verify the chapter heading, word count, and text. For the blurb, inspect the rendered work-page text around `简介` and stop before `第1章`.
- Before analysis, maintain a compact source ledger containing `work title -> blurb -> chapter number/title -> canonical URL -> opening event -> ending sentence/action`. This prevents duplicate chapters and keeps observations separate from interpretation.
- Probe a current/latest chapter separately before claiming long-form coverage. Public opening chapters may be readable while current chapters show a membership/login wall. When blocked, label conclusions as packaging/opening evidence only and keep middle/late-book stability under `待验证`; do not treat login-wall metadata as evidence about the prose.
- Treat mobile catalogue VIP markers, the mobile H5 chapter-content API, and desktop web trial coverage as separate boundaries. The mobile H5 endpoint `/qimaoapi/api/h5/v1/book/chapter-content-list?book_id=<id>` may return only the initial free chapters while desktop `下一章` pages expose a longer, book-specific trial. Verify each desired chapter from its rendered `chapter-detail-article` container and confirm that the text belongs to the target work; HTTP 200, a visible chapter title, generic `<p>` tags, or recommendation previews do not prove that the chapter is unlocked.
- Follow canonical `下一章` URLs rather than constructing chapter IDs: IDs are not reliably sequential. Stop at the first page whose target chapter article is empty or whose text belongs to another recommended work, and record the actual per-book boundary.
- Login and public reading are separate questions. Verify public chapter access before initiating SMS authentication. Never echo or persist captured cookies/tokens; use them only for the current authorization check and report structural status rather than credential values.

## User-evidence vs self-scan (correction pattern)

When the user pastes live evidence (Stream / HAR / curl capture, terminal output, screenshot text) and your local scan disagrees, the user evidence wins by default. The most common failure pattern in this domain has been: agent self-scans return "not installed / not present", agent repeats that conclusion in subsequent turns even after the user pastes evidence showing it *is* installed. Rules:

- If the user's pasted evidence describes a state (`unit found`, `service active`, `chapter readable`, `chapter heading visible`), it overrides your local scan until you re-verify.
- Re-verify before repeating. A single re-scan after a contradiction is cheap; repeating the wrong conclusion is expensive.
- When the user specifies a host identity (`I'm on 180.152.19.204`) and your scan shows a different state, the host identity is the variable. Confirm you are SSH'd into the right machine before drawing any conclusion about what's installed there.
- If a "browser says X, CLI says not-X" split appears (Qimao's paywall stub: browser shows `我已是会员，立即登录`, CLI shows empty `<p>` with no wall marker), name both views explicitly instead of arbitrating. The reader can judge the situation without you choosing sides.
- A user-pasted capture (Stream / HAR / curl log) of the Qimao site is a *forensic* artifact, not live credentials. Treat it as evidence of *what the user saw*; do not extract `Cookie:` / `qimao-token` / `author-token` for replay. Typical files contain: a `Cookie:` header (with `qimao-token` partially redacted as `eyJhbG...qxtV`), an `author-token` (often left in cleartext as `user:hex` — a user-bound token, equivalent to a password), and a `drs.wtzw.com/frontend` POST whose body is base64 device-fingerprinting. Parse only the public shape: URLs, header keys, request bodies in summarized form, and the *metadata* of any token (issuer, exp claim, user-bound prefix) — not the token values. Replaying the pasted `Cookie` crosses the trust boundary the user set when they shared the file. If continued authenticated access is genuinely needed, ask the user to add a fresh SSH key to the target host, or to set a new cookie in their own browser, rather than reusing what they pasted.
- Private user-bound tokens like `author-token` are passwords. Never echo them, never include them in shell arguments (process listings, terminal scrollback, shared subagent contexts can all leak them), and never pass them to a tool that does not strictly require them. The same `[REDACT]` discipline that applies to phone numbers, OTPs, and platform cookies extends to anything scoped to a user identity.
- When verifying token lifetime, decode the JWT payload offline to read `iat` / `exp` claims. Never paste the raw JWT or its decoded claims anywhere that will be re-displayed — keep the claim values internal to the diagnostic and only report `expired=true/false` plus a coarse "remaining seconds" number.
- Homepage charts, policies, contest notices, and signing terms change. Inspect the original live source each time rather than treating session memory as current evidence.
