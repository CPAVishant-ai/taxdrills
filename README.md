# TaxDrills — deploy guide

Static site. No build step, no framework, nothing to install.

## Deploy to Vercel (5 minutes)
1. Create a free account at vercel.com (sign in with GitHub is easiest).
2. Option A — drag & drop: go to vercel.com/new, choose "Deploy without Git",
   and drag this whole folder in. Done.
   Option B — Git (better long-term): push this folder to a GitHub repo,
   then "Import Project" in Vercel. Every git push auto-deploys.
3. Your site is live at your-project.vercel.app. Add a custom domain
   (e.g. taxcraft.valim.ai) in Project Settings -> Domains.

## Visitor analytics (already wired)
index.html includes the Vercel Web Analytics script tag.
Enable it: Vercel dashboard -> your project -> Analytics -> Enable.
You'll see visitors, page views, referrers, and countries. Cookie-free,
so no consent banner needed for analytics alone.

## Ads at 100+ regular users
1. Apply at adsense.google.com with your live domain (custom domain
   strongly recommended over .vercel.app for approval).
2. After approval, paste the AdSense <script> into <head> of index.html
   (marked with a comment) and uncomment the two `adslot` divs
   (one on the home page, one on the results screen).
3. AdSense requires a privacy policy: the footer Privacy section is a
   starting point — expand it to mention ad cookies when ads go live.

## Updating tax-year numbers (do this every January)
All year-dependent values live near the top of the <script> in index.html:
SALT_CAP, STD_MFJ, CTC, MILE constants, plus typein questions that state
a year. Search for "2026" to find every one of them.

## Adding questions
Add objects to the FIXED array (typein / match / order / sort) or new
generator functions to GENS. Each item needs: t (topic id), tier (1-3),
and an expl (the teaching sentence shown after answering).
