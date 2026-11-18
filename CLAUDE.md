# Mouge Perfume website

## Project facts
- Static site on Cloudflare Pages: repo root is the output, no build step. Merging to `main` deploys.
- The repo is **public**. Never commit credentials, API keys or customer data.
- `index.html` is ~1 MB because images are embedded as `data:` URIs. Make targeted edits, never full rewrites.
- `_headers` sets a strict Content-Security-Policy. The only inline `<script>` is allowed by a `sha256-` hash, so **any change to that script must update the hash in `_headers`** or the page's JavaScript stops working:
  `printf '%s' "<exact script body>" | openssl dgst -sha256 -binary | base64`
- Any new external host (font, analytics, API) must be added to the matching CSP directive in `_headers`.
- The signup form posts to FormSubmit (`formsubmit.co`). Keep the unchecked consent box, the honeypot and the CAPTCHA. Never submit real signups.
- `privacy.html` is bilingual (English and Arabic). Keep both in sync; Arabic content uses `lang="ar"` and `dir="rtl"`.
- Preserve the existing design, layout and animations unless a change is explicitly requested.

## AI team (Claude Code agents in `.claude/agents/`)
- `web-developer` — builds and fixes site code.
- `seo-performance` — metadata, speed, accessibility, search.
- `copywriter` — English/Arabic copy and brand voice.
- `qa-reviewer` — reviews changes; read-only.
After any code change, run `qa-reviewer` before committing.
