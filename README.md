# Nevins Home Improvement website

A one-page site for Nevins Home Improvement LLC (Tecumseh, MI). Plain HTML and CSS, no build step, no framework.

- `index.html`: the whole page (styles and script are inside it)
- `thank-you.html`: where people land after sending the quote form
- `screenshot-*.png`: preview images, safe to delete

## 1. Put it online (GitHub + Cloudflare Pages, free)

1. Create a GitHub repo (for example `nevins-home-improvement`) and upload these files to it.
2. In Cloudflare, go to **Workers & Pages > Create > Pages > Connect to Git**, pick the repo.
3. Build settings: **Framework preset: None**, **Build command: (leave empty)**, **Output directory: `/`**. Deploy.
4. In the Pages project, open **Custom domains** and add `nevinshomeimprovement.com` (and `www.`). The domain must be registered first; if it is on Cloudflare, DNS is set up for you.

Every change pushed to the repo goes live in about a minute.

## 2. Make the quote form send email (Web3Forms, free)

1. Go to https://web3forms.com, enter **Chris's email address**, and it emails back an **access key**.
2. In `index.html`, replace `WEB3FORMS_ACCESS_KEY_TODO` with that key.
3. Send a test from the live site and check Chris's inbox (and spam folder the first time).

The access key is meant to be public; it only lets the form send to Chris's address.

## 3. Spam protection (Cloudflare Turnstile, free)

1. In Cloudflare, go to **Turnstile > Add widget**, domain `nevinshomeimprovement.com`, mode **Managed**.
2. In `index.html`, replace `TURNSTILE_SITEKEY_TODO` in the settings at the top of the script near the bottom of the file with the **site key** (the form picks it up from there).
3. Give the **secret key** to Web3Forms in its dashboard so it can check the token. Check the Web3Forms docs for where Turnstile goes and whether your plan includes it; if it does not, the hidden honeypot field still blocks most bots.

Until the placeholder is replaced, the Turnstile box stays hidden and its script never loads.

## 4. Facebook / Meta pixel (for the ads)

1. In Meta Events Manager, create or pick a pixel and copy its **Pixel ID** (a long number).
2. Replace `META_PIXEL_ID_TODO` in **both** `index.html` and `thank-you.html`.
3. What it tracks: `PageView` on every page, `Contact` when someone taps a phone number, `Lead` when the quote form is sent. Use **Lead** as the ad campaign's conversion event.

Until the placeholder is replaced, the pixel does not load at all.

## 5. How Chris edits the site with Claude

1. Sign in at https://claude.ai and connect GitHub (**Settings > Connectors > GitHub**), giving it access to this repo. Or use Claude Code on the web at https://claude.ai/code, which can edit the repo and push the change.
2. Ask in plain English, for example:
   - "In my website repo, change the hours to Monday to Saturday, 8 to 5."
   - "Add these three photos to the project gallery in place of the placeholder tiles." (attach the photos)
   - "Add a review from Mike T. that says ..."
3. Claude makes the change and commits it to GitHub. Cloudflare publishes it automatically.

Rules worth keeping when editing: never add a review someone did not actually write, keep the license number in the footer, and keep photos under about 300 KB each (Claude can resize them) so the page stays fast.

## TODO list for Chris

- [ ] **Photos.** Send real project photos (bathrooms first, then kitchens, tile, floors, decks) and one photo of you on a job. They replace the labeled placeholder tiles. Look for `PHOTOS GO HERE` and `PHOTO OF CHRIS` comments in `index.html`.
- [ ] **Service area.** Which towns do you serve? The list currently says Tecumseh, Lenawee County, Southeast Michigan.
- [ ] **Hours.** Listings disagree (Mon to Fri 8 to 5 vs Mon to Sat 8 to 5).
- [ ] **Email** for the Web3Forms key (where quote requests go).
- [ ] **Confirm before we say it on the site:** insured? free estimates? any warranty on work? still doing 99% of work in-house including electrical, plumbing and ductwork? Nothing like this is on the page until you confirm.
- [ ] **Street address:** publish one or not? (Listings show both 311 W Logan St and 100 E Logan St.) Service-area-only is normal for remodelers and is what the page does now.
- [ ] **Founding year:** the page says "since 2003" and "20+ years." BBB says 2002. Confirm.
- [ ] **More reviews:** the page uses four Yelp quotes word for word. Send any others you want shown (with the reviewer's name as it appears).
- [ ] **Domain:** register `nevinshomeimprovement.com` (or tell us the one you want; it is set as the canonical URL in `index.html`).
- [ ] Web3Forms key, Turnstile site key, Meta pixel ID (steps above).
