# tryontrend.com

The marketing site for **TryOnTrend**, live virtual try-on for Shopify. Static HTML, CSS and a few lines of JavaScript: no build step, no dependencies.

## Pages

| Path | File | What's on it |
| --- | --- | --- |
| `/` | `index.html` | Hero, how it works, the two try-on modes, merchant features, analytics, privacy, pricing, FAQ |
| `/support/` | `support/index.html` | Contact, setup guide, troubleshooting |
| `/privacy/` | `privacy/index.html` | Privacy policy (use this URL in the Shopify App Store listing) |
| `/terms/` | `terms/index.html` | Terms of service |
| 404 | `404.html` | Not-found page (Vercel serves it automatically) |

Shared files: `assets/css/site.css`, `assets/js/site.js` (mobile menu, header border, footer year), `assets/favicon.svg`, and images in `assets/img/` (`og.jpg` is the 1200×630 social share image).

The header and footer are repeated in every page, so change them in all five files. Facts on the site (plans, prices, allowances, the 14-day revenue window, data retention) mirror the TryOnTrend app; update both together.

## Things to check before launch

- **App Store link:** every "Install on Shopify" button points to `https://apps.shopify.com/tryontrend`. Update it if the listing URL is different once the app is published.
- **Support email:** the site (and the app's Help page) use `developeragentic@gmail.com` because tryontrend.com has no email set up yet. Once domain email works, switch to `support@tryontrend.com` everywhere.
- **Legal pages:** the privacy policy and terms describe how the app actually works, but have them reviewed for your business. Add your legal entity name and address if required where you operate.

## Preview locally

Pages use root-relative links (`/assets/...`), so serve the folder rather than opening the file:

```shell
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy with Vercel

1. Import this repository into Vercel. Framework preset: **Other**. Leave the build command empty; the output directory is the repository root.
2. Add the domain `tryontrend.com` (and `www.tryontrend.com`, redirecting to it) under **Settings → Domains**, then point the DNS records at GoDaddy to Vercel as shown there.

`vercel.json` turns on clean URLs and adds security headers (CSP, HSTS, frame and referrer policies) and caching for `/assets/`. `robots.txt` and `sitemap.xml` are at the root.
