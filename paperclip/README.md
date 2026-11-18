# Mouge AI team (Paperclip)

Instruction files for the Mouge Perfume agent team. Create one Paperclip agent per folder and set its instructions path to that folder's `AGENTS.md`.

| Agent | File | Owns |
| --- | --- | --- |
| Web Developer | `agents/web-developer/AGENTS.md` | Site code: `index.html`, `privacy.html`, `_headers` |
| SEO & Performance | `agents/seo-performance/AGENTS.md` | Metadata, speed, accessibility, search |
| Copywriter / Brand | `agents/copywriter/AGENTS.md` | English and Arabic copy, brand voice |
| QA Reviewer | `agents/qa-reviewer/AGENTS.md` | Reviews every change before it ships |

## How work flows
1. A task is assigned to the owning agent (developer, SEO or copywriter).
2. The agent opens a pull request and creates a review task for the QA Reviewer, blocking its own task on it.
3. QA posts a verdict on the review task and marks it `done`.
4. The owning agent fixes findings, then hands the PR to a human to merge. Agents never merge.

## Shared project facts (all agents)
- Static site on Cloudflare Pages: repo root is the output, no build step.
- The repo is **public**. Never commit credentials, API keys or customer data.
- `index.html` is ~1 MB because images are embedded as `data:` URIs. Edit it with targeted changes, never full rewrites.
- `_headers` sets a strict Content-Security-Policy. The only inline script is allowed by a `sha256-` hash, so **any change to that `<script>` must update the hash in `_headers`** or the page's JavaScript stops working.
- The signup form posts to FormSubmit (`formsubmit.co`). Keep the unchecked consent box, the honeypot and the CAPTCHA.
- `privacy.html` is bilingual (English and Arabic). Keep both languages in sync.
