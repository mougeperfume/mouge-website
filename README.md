# Mouge Perfume website

Static site for the Mouge Perfume invitation launch. This repository is public and contains the website source; do not store credentials or private customer data here.

## Files
- `index.html` — invitation landing page and signup form
- `privacy.html` — bilingual privacy notice
- `_headers` — Cloudflare Pages security headers

## Cloudflare Pages
This is a static site. Use the repository root as the output directory and no build command.

## Before inviting visitors
The form sends opt-in submissions to `mougeperfumes@gmail.com` through FormSubmit. Activate FormSubmit from the confirmation message sent to that mailbox after deployment, then verify delivery using an email address you control. No real signup was sent during preparation. The form includes an unchecked consent checkbox, a honeypot, and FormSubmit's default CAPTCHA protection.
