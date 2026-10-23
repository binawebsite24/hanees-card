# Hanees Hazli — digital business card

A single-page "tap card": a self-contained digital business card for an NFC tag
or QR code. Save-contact (vCard), Share, on-page QR, quick WhatsApp/Instagram/
email actions, Cal.com booking, and a list of links.

Live: https://hanees-card.pages.dev

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole card — markup, styles and script in one file |
| `portrait.jpg` | The portrait at the top of the card |
| `og-card.png` | 1200×630 preview image used by WhatsApp, X and friends |

## Editing

Everything you'd normally change lives in one `CONFIG` block in `index.html`
(search for `EDIT ONLY THIS BLOCK`) — name, role, phone, email, booking link,
quick actions and the social list. A value left as `""` simply doesn't render.

The portrait can be a short vertical video instead of a still: set
`portrait.video` to e.g. `"portrait.mp4"`, drop the file next to `index.html`,
and keep `portrait.image` as the fallback.

## Deploying

Hosted on Cloudflare Pages. To publish a change:

```bash
npx wrangler pages deploy . --project-name hanees-card
```

If you move the card to a custom domain, update the absolute
`og:image` and `og:url` URLs in the `<head>` to match — social unfurlers need
absolute URLs, and a stale host means no preview image.

When testing a link in WhatsApp, add `?v=2` (then `?v=3`, …) to bust its
preview cache.
