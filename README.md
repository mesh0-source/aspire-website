# Aspire Research & Consulting — Website

Static site for **aspireresearchconsulting.com**, built for free hosting on GitHub Pages.

## What's in this repo

```
index.html          Home
about.html           About Aspire
services.html        Services & pricing (on-site summary of the full Service Catalog)
our-work.html        Portfolio samples + process
contact.html         Contact page
404.html             Custom "page not found"
CNAME                Tells GitHub Pages to serve this site on your custom domain
assets/css/main.css  Shared styles (brand colors, nav, footer, buttons, etc.)
assets/docs/         Downloadable client-facing documents (Service Catalog,
                     Capability Statement, and the 5 portfolio samples)
```

Internal operations documents (Client Proposal, Service Agreement, Invoice,
Intake Form, NDA, Project Brief, Project Delivery templates) are **not**
included here — those are working documents for use with clients directly,
not public site content.

## 1. Push this to GitHub

1. Create a new **public** repository on GitHub — any name works (e.g. `aspire-website`).
   (It does *not* need to be named `<username>.github.io` — that naming convention
   is only required if you want the site at the bare `github.io` URL. Since you're
   using a custom domain, any repo name is fine.)
2. From this folder, initialize and push:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

## 2. Turn on GitHub Pages

1. In the repo, go to **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Save.
4. Under **Custom domain**, enter `aspireresearchconsulting.com` and save.
   (This will double-check the `CNAME` file already in this repo — GitHub may
   rewrite it, which is fine.)

## 3. Point your domain at GitHub Pages

At your domain registrar (wherever `aspireresearchconsulting.com` is registered),
update DNS records:

**Apex domain (`aspireresearchconsulting.com`)** — add four **A** records, all
pointing to GitHub Pages' IP addresses:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**www subdomain** (optional but recommended, so `www.aspireresearchconsulting.com`
also works) — add a **CNAME** record:

```
www   →   <your-username>.github.io
```

DNS changes can take anywhere from a few minutes to ~24 hours to propagate.

## 4. Enable HTTPS

Once DNS has propagated (GitHub will show a green checkmark next to your
custom domain in **Settings → Pages**), check **Enforce HTTPS**. GitHub issues
a free SSL certificate automatically — this step just can't be completed until
DNS is pointing correctly.

## Updating the site later

Any push to `main` redeploys automatically — usually live within a minute or two.

To swap in a real logo, replace the text wordmark in the `<header class="site-nav">`
block on each page with an `<img>` tag pointing to a logo file placed in
`assets/img/`.

To update pricing or service details, edit `services.html` directly, and/or
replace `assets/docs/Aspire_Service_Catalog.docx` with an updated version
(keep the same filename so existing links keep working).

## Contact form note

GitHub Pages only serves static files — there's no server to process form
submissions. The Contact page uses a `mailto:` link, which opens the visitor's
own email client. If you'd like an embedded form instead, a free third-party
form backend (e.g. Formspree) can be wired in later without changing hosting.
