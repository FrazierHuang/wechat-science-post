---
name: wechat-science-post
description: Draft, revise, humanize, and format Chinese WeChat public-account articles for scientific literature sharing, environmental health commentary, product-safety explainers, and browser-comment-driven edits. Use when the user asks to write or polish a 公众号推文, convert a paper into a WeChat article, make an article less AI-like, adjust HTML/Markdown layout, respond to in-app browser comments, add evidence-chain critique, prepare titles, summaries, image notes, disclaimers, or source lists for science communication posts.
---

# WeChat Science Post

## Core Workflow

1. Identify the article type: literature share, professional explainer, controversy analysis, or short update.
2. Read the current artifact first when a local HTML/Markdown file or browser page is available. Preserve the existing layout unless the user asks for a redesign.
3. Anchor the article on the evidence chain: sample/source, method, result, exposure or mechanism, uncertainty, and what conclusion is or is not supported.
4. Write in a professional WeChat voice: clear, specific, and readable, without sounding like a report template.
5. Edit the actual file when the user asks for changes. After edits, search for banned patterns and verify the changed section.

## Style Rules

Follow `references/style-guide.md` for detailed phrasing and structure rules.

Default preferences:

- Use Chinese for public-account body text unless the user asks otherwise.
- Keep technical keywords in English when the user asks for source-faithful literature sharing.
- Add Chinese translated titles for papers when the user asks for article information.
- Prefer concrete section titles such as `一个检测数字，还不够` over generic titles such as `研究讨论` or `核心内容`.
- Avoid rigid numbered headings unless the article is explicitly a literature-method/result summary.
- Avoid the sentence pattern `不是……而是……`; rewrite into a direct positive statement.
- Do not overstate risk. Distinguish hazard, detection, total content, migration, exposure dose, and health risk.
- When discussing public controversies, critique claims and evidence chains, not personal identities.

## WeChat HTML Handling

When editing existing WeChat HTML in the workspace:

1. Locate the target section with `rg` before editing.
2. Use `apply_patch` for manual edits.
3. Keep the current CSS and section rhythm unless the user asks for a layout change.
4. After editing, run a focused check:

```bash
rg -n "不是.+而是|原文认为|作者主要|AI|TODO|一定有害|毒纸尿裤|骗子|造谣" <file>
```

5. If the page is open in the in-app browser, tell the user to refresh only after confirming the file was written.

## Literature Post Structure

For paper-based posts, use this order when the user does not specify another template:

1. Title with journal and topic, platform-safe and not clickbait.
2. Article information: English title, Chinese title, authors, journal, date, DOI.
3. Why this paper matters.
4. Study design and methods.
5. Main results.
6. Mechanism or interpretation.
7. Limitations and evidence boundary.
8. Take-home message.
9. Source/copyright note, including `如有侵权，请联系删除` when adapted figures or screenshots are used.

## Controversy Explainer Structure

For product-safety or public-health controversies:

1. Start from the concrete claim that is circulating.
2. Separate what is known, what is inferred, and what remains missing.
3. Explain the technical point with the same event when possible, rather than unrelated examples.
4. Use unit conversion carefully. If a value is not verified, explain the conversion generically instead of inventing a number.
5. End with practical questions readers can ask: batch, material layer, method, limit of quantification, migration test, exposure estimate, and regulatory response.

## Source Discipline

- Use web verification for current controversies, news, standards, and any claim likely to have changed.
- Use primary sources for scientific papers, standards, or technical claims when possible.
- If only secondary sources are available, label the evidence boundary in the article.
- Do not fabricate brand names, measured values, DOI, publication dates, limits, or legal standards.
