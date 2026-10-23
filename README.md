# Hanees Hazli — digital business card

A single-page "tap card": a self-contained digital business card for an NFC tag
or QR code. Save-contact (vCard), Share, on-page QR, quick WhatsApp/Instagram/
email actions, Cal.com booking, and a list of links.

Live: https://hanees.site

## Files

| File | What it is |
| --- | --- |
| `public/index.html` | The whole card — markup, styles and script in one file |
| `public/portrait.jpg` | The portrait at the top of the card |
| `public/og-card.png` | 1200×630 preview image used by WhatsApp, X and friends |

## Editing

Everything you'd normally change lives in one `CONFIG` block in `public/index.html`
(search for `EDIT ONLY THIS BLOCK`) — name, role, phone, email, booking link,
quick actions and the social list. A value left as `""` simply doesn't render.

The portrait can be a short vertical video instead of a still: set
`portrait.video` to e.g. `"portrait.mp4"`, drop the file next to `public/index.html`,
and keep `portrait.image` as the fallback.

## Deploying

Hosted on Cloudflare (Workers static assets, the current Cloudflare Pages
platform). Everything under `public/` is served at the site root; nothing
outside it is. To publish a change:

```bash
npx wrangler deploy
```

The card is served on the custom domain `hanees.site` (set under `routes` in
`wrangler.jsonc`). If you move it to another domain, update that route and the
absolute `og:image` and `og:url` URLs in the `<head>` to match — social unfurlers need
absolute URLs, and a stale host means no preview image.

When testing a link in WhatsApp, add `?v=2` (then `?v=3`, …) to bust its
preview cache.
