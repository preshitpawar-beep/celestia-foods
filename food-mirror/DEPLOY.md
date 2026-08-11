# Celestia Food & Spices — mirrored site (Option A)

This folder is an **exact, byte-for-byte copy** of the live food & spices site that is
currently served at `celestiagt.com` (a Next.js static export originally hosted on
Firebase). Every page and asset was downloaded directly from the live site.

- Pages: `/`, `/about-us`, `/contact-us`, `/products`, `/products/rice`,
  `/products/jaggery`, `/products/fruits`, `/products/spices`
- All JS/CSS is in `_next/static/…` (downloaded, HTTP 200 verified)
- Product **images** are served from the original external CDN (imagekit.io) and are
  left untouched — they keep working with no action needed.
- `vercel.json` enables clean URLs so `/about-us` serves `about-us.html`, etc.

## Goal
Serve this at **foods.celestiagt.com** on your own Vercel account, independent of the
Firebase site you can't access.

## Deploy (no command line needed)
1. Zip this `food-mirror` folder.
2. Go to https://vercel.com/new → drag-and-drop the folder (or "Deploy" an empty
   project and upload). No build step — it's a static site. Framework preset: "Other".
3. Vercel gives you a preview URL like `celestia-food.vercel.app`. Open it and confirm
   it looks identical to the current site.

## Point the subdomain (GoDaddy)
1. In the Vercel project → Settings → Domains → add `foods.celestiagt.com`.
2. Vercel shows a CNAME target (usually `cname.vercel-dns.com`).
3. In GoDaddy → celestiagt.com → DNS → add record:
   - Type: `CNAME`  |  Name: `foods`  |  Value: `cname.vercel-dns.com`  |  TTL: default
4. Wait for it to verify (minutes to an hour). HTTPS is issued automatically by Vercel.

## Notes
- Contact form: the original "Submit" button posted to the old site's backend, which we
  don't control. On the mirror it may not deliver mail. The page still shows the phone,
  WhatsApp (7755997122), and email (harsh.jaiswal@celestiagt.com) links, which work.
  A working form can be wired up later (e.g. Formspree, or the nodemailer setup already
  in the engineering repo).
- This is a frozen snapshot. To edit products/prices later, that's the "Option B"
  clean rebuild we discussed
