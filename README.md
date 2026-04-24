# Junk It ATX — Website

Static one-page site for Junk It ATX junk removal (Austin, TX).
Phone: (512) 497-1627 · Email: info@junkitatx.org

## Files

- `index.html` — the entire site. HTML, CSS, and JS all inline. No build step.

## Running locally

Just open `index.html` in a browser. That's it.

## Editing

Edit `index.html` in any text editor. Commit and push — Vercel redeploys automatically.

## Hooking up the quote form (one-time setup)

The quote form on the page is wired to **Formspree**, which forwards submissions to an email address. Right now the form `action` is a placeholder — **submissions won't arrive until a real Formspree form ID is set**.

To activate:

1. Go to https://formspree.io and sign up with the email where quote requests should land.
2. Create a new form. Formspree gives you a URL like `https://formspree.io/f/xvgpabcd`.
3. In `index.html`, find this line (around line 585):
   ```html
   <form id="quoteForm" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
4. Replace `YOUR_FORM_ID` with the ID Formspree gave you (e.g. `xvgpabcd`).
5. Commit and push. Every quote request is now emailed to whoever owns the Formspree account.

Free tier: 50 submissions/month.

## Deploying

Hosted on Vercel. Every push to `main` on GitHub auto-deploys to production.

### Pointing a custom domain (e.g. junkitatx.com)

When the real domain is ready:

1. Go to the Vercel project → Settings → Domains → Add Domain.
2. Enter the domain (e.g. `junkitatx.com`).
3. Vercel shows the DNS records to add (usually an `A` record pointing to `76.76.21.21` and a `CNAME` for `www`).
4. At the domain registrar (GoDaddy, Namecheap, Wix domain settings, etc.), update the DNS records to match.
5. Vercel provisions an SSL cert automatically. Usually live within minutes, sometimes up to 24 hours for DNS propagation.

If the domain is currently on Wix and being handed off: the owner either transfers the domain out of Wix, or keeps it at Wix and just changes the DNS records there to point at Vercel. No need to move the domain itself.
