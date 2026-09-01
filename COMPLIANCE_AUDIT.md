# Alberton Battery Mart — Legal & Advertising Compliance Audit

**Audit date:** 1 September 2026  
**Legal frame:** CPA 68 of 2008 ss 23, 29, 30, 41 · ARB Code s II cls 4.1, 4.2, 6, 7, 7.1.6 · Trade Marks Act 194 of 1993 / passing off · Google Ads reseller exception · ECTA basics  

**Sources audited**
1. This repository: `index.html` (GitHub `Franksmittt/abm`, still live at https://abm-khaki.vercel.app/).
2. Production website: https://www.albertonbatterymart.co.za (Next.js app; **source is not in this repo**).

**Scope note (read this first).**  
This GitHub repo is a 2025 single-page HTML site. Production is a separate multi-page Next.js application (also previewed at https://abm2-jade.vercel.app/). Hostile scrutiny will look at **whatever Google and customers actually see**. Findings below therefore cover both surfaces. Remediations committed in this PR can only change `index.html`. Production copy must be patched in the live Next.js codebase.

---

## CRITICAL

Anything a hostile competitor (Global Batteries / Battery Centre) could report to Google, the ARB, or sue over: trademark misuse, false affiliation, unsubstantiated superlatives/comparatives, disparagement, or ads that the landing page cannot support.

### C1. Two live sites, contradictory claims (CPA s41 + ARB 4.1/4.2)

A customer or complainant who compares https://abm-khaki.vercel.app/ with https://www.albertonbatterymart.co.za will find opposite statements on the same brand.

| Claim | This repo (`index.html`) | Live site |
| --- | --- | --- |
| Mobile callout price | Completely free | Homepage FAQ: callout **has a service fee**; `/services/mobile-battery-replacement/alberton` FAQ: free within 10 km with purchase, **R150** outside |
| Saturday hours | 08:00–**13:00** | 08:00–**12:00** (footer, contact, schema) |
| Brands | Raylite & Willard only | Willard, Exide, Enertec, Power Plus, Eco Plus |
| Email | `admin@albaertonbatterymart.co.za` (typo) | `admin@albertonbatterymart.co.za` / FAQ also uses `info@albertonbatterymart.co.za` |

**Recommended:** Point the Vercel alias for this repo at production, or 301-redirect `abm-khaki.vercel.app` to `www.albertonbatterymart.co.za`. Until then, bring this HTML into line with production (done in this PR for `index.html`).

### C2. “Official / certified / authorised stockist” — false affiliation (CPA s41; ARB 4.1)

User instruction: unless a written distribution agreement exists, use “Stockists of Willard, Exide…”.

**This repo — `index.html`**

| Line | Exact text |
| --- | --- |
| 33 (JSON-LD `description`) | `Certified Raylite & Willard stockist.` |
| 357 | `OEM Certified Raylite and Willard Batteries.` |
| 421 | `OEM Certified Power` |
| 726 | `We are certified stockists for Raylite and Willard, South Africa's most trusted OEM (Original Equipment Manufacturer) battery brands.` |
| 798 | `OEM-certified products` |
| 701 | `Certified Technician in Action` |

**Live production**

| URL | Exact text |
| --- | --- |
| `/` FAQ + FAQPage JSON-LD | `We officially stock Willard, Enertec, Exide, and high-quality generic batteries for all vehicle makes.` |
| `/about` | `As official stockists of **Willard, Exide, and Enertec**` |
| `/` WebPage JSON-LD `description` | `Fast, certified mobile battery replacement service in Alberton…` |
| `/services/mobile-battery-replacement/alberton` H1 lead | `Certified mobile fitment for cars, SUVs, 4x4s, and trucks…` |
| `/services/free-battery-testing/alberton` | `Certified technicians delivering free battery, starter, and alternator diagnostics…` |

**Recommended replacement (use everywhere):**  
`We stock Willard, Exide, Enertec, Power Plus, Eco Plus and Raylite batteries.`  
Do **not** use official, authorised, certified stockist, OEM certified, or approved dealer unless the written appointment is on file.

### C3. Unsubstantiated superlatives (ARB 4.1; CPA s41)

No dated price survey, market study, or response-time log is published.

**This repo — `index.html`**

| Line | Exact text |
| --- | --- |
| 359 | `The Best Price in Town, Guaranteed by 5-Star Service.` |
| 574 | `Alberton's Fastest Mobile Battery Service` |
| 577 | `Our hyper-local callout service means we get to you faster across Alberton.` |
| 747 | `we offer Alberton's fastest callout service.` |

**Live production**

| URL | Exact text |
| --- | --- |
| `/` | `4.8/5 local customer rating` — no source, date, or Google review count. `/reviews` itself says “Do not fabricate reviews or ratings”. |
| `/` | `We have the area's widest selection in stock, ready to go.` |
| `/about` | `to be the **#1 trusted battery expert in Alberton**` |
| `/blog/battery-on-call-vs-true-local-service` | `We get to Meyersdal, Alberton Central, and surrounding areas faster than any national service.` |
| Blog index | `We are Alberton's only non-dealer specialists with the tools to do it right.` (Ford Ranger coding post, 26 Dec 2025) |

**Recommended replacements**
- Hero: `Competitive Alberton prices. Ask us to beat a genuine local quote on the same brand and size.`
- Speed: `Typical Alberton arrival 45–60 minutes during trading hours, from our New Redruth store.`
- Rating: quote the live Google Business Profile figure with the review count and a “as at [date]” stamp, or remove it.
- Selection: `171 listed lines across Willard, Exide, Enertec, Power Plus and Eco Plus — confirm stock when you call.`
- Drop `#1`, `only`, `fastest`, `widest`, `best in town` as **business** claims. Customer review quotes that say “best price” may stay if they are genuine Google reviews.

### C4. Google Ads reseller exception — this landing page fails

Ads use Willard, Exide, Enertec, Power Plus, Eco Plus under the reseller exception. That exception requires the **landing page** to clearly show those brands for sale (names + prices or a catalogue).

**This repo (`index.html`):** no product cards, no prices, no Exide / Enertec / Power Plus / Eco Plus. Schema `makesOffered` is only `Raylite`, `Willard`. If any ad still lands here (or on `abm-khaki.vercel.app`), a trademark owner can complain and Google can suspend the ads.

**Live production — this part is CLEAN:**
- `/products/brand/willard` — 9 Willard products with prices (e.g. Willard 646 **R 1 900.00**).
- `/products/brand/exide` — 51 Exide lines (priced and P.O.A.).
- `/products/brand/enertec` — 34 Enertec motorcycle lines with prices (from **R 340.00**).
- `/products/brand/power-plus` — 41 products; cheapest listed **R 1 150.00** (Power Plus 615 / 616 / 616B / U1-250).
- `/products/brand/eco-plus` — 36 products; cheapest listed **R 1 050.00** (Eco Plus 615 / 616 / 616B).
- Size hubs `/{646,652,658,668,628,619}-car-battery` list named SKUs + fitted prices.

**Recommended:** Never point brand-name ads at this HTML. Production product URLs are the correct landers. This PR adds a visible brand+price block to `index.html` so the page is not a dead lander if it still receives traffic.

### C5. Ad price claims vs site evidence

Ads: “Power Plus From R1,150” and “Eco Plus From R1,050”.

| Surface | Finding |
| --- | --- |
| Live `/products/brand/power-plus` | Matches: Power Plus 615/616/616B/U1-250 at **R 1 150.00**. |
| Live `/products/brand/eco-plus` | Matches: Eco Plus 615/616/616B at **R 1 050.00**. |
| Live header strip | `Power Plus from R1,150 \| Eco Plus from R1,050` — **no “from” conditions** (size, scrap exchange, VAT, date). |
| This repo | Prices **absent**. Ad would be unsubstantiated if it landed here. |

**Recommended header line:**  
`Power Plus from R1,150 and Eco Plus from R1,050 (incl. VAT, scrap exchange required, selected 12V sizes, stock dependent). Prices as at September 2026 — confirm before dispatch.`

Ads: “Alberton's Best Battery Prices” / “Cheaper Than Voortrekker Rd” / “beats the cheapest batteries on Voortrekker Rd”.

**Neither surface publishes a dated, like-for-like competitor price table.** Live `/disclosure` even says: `we do not guarantee we are the cheapest in every case.` That is honest — and it **undercuts** the current ad superlative.

**Recommended ad/site pairing (keep the competitive punch, make it defensible):**  
Site: a dated “Alberton price check” table (our fitted price vs a named Voortrekker Rd quote on the same Willard/Exide size, date, screenshot/invoice held on file).  
Ad: `Alberton fitted prices — ask us to beat a genuine Voortrekker Rd quote on the same battery.`  
Do not run “Alberton’s best” / “beats the cheapest on Voortrekker Rd” until that file exists.

### C6. “Battery Centre” / competitor names

**This repo:** no hits for `battery centre/center`, `global batteries`, `atlas battery`, `first battery`, `battery clinic`. Business name is consistently **Alberton Battery Mart**. No competitor logos.

**Live `/disclosure`** (lawful if kept descriptive):  
`Names such as Global Batteries, Battery Centre, First Battery Centre, and other third-party brands mentioned on this page are trademarks of their respective owners. We use them only where necessary to identify the market or for factual comparison.`

**Live `/about` and footer:** identity is “Alberton Battery Mart” / “Independent retailer — see Disclosure.” **CLEAN.**

**Watchpoint:** Google still has an older snippet for `/blog/mobile-fitment-vs-in-store-service` as `Don't waste time driving to a battery centre.` Current on-page title/body uses `franchise battery shop`. Confirm the `<title>`, H1, meta, slug, and sitemap no longer contain “battery centre”. Never use that phrase as a self-description (`your local battery centre`).

**Live `/blog/battery-on-call-vs-true-local-service`:** H1 `"Battery on Call" vs. True Local Service`. “Battery on Call” is a Willard service mark. Comparative use can be lawful; the body then disparages national dispatch (`script-reader in another city`, `whatever single brand they are paid to push`). That is ARB cl 6 / 7.1.6 risk.

**Recommended body rewrite (keep the local merit):**  
`National “battery on call” networks dispatch from a central queue. We dispatch from 28 St Columb Rd, New Redruth, with Willard, Exide, Enertec, Power Plus and Eco Plus on the van. You speak to the Alberton workshop, not a national call centre.`

### C7. Callout “free” vs paid — ads and site contradict each other (CPA s23/s41; ARB 4.2)

Ads: “Free Callout” / “we come to you” / “pay only on success”.

| Surface | Exact text |
| --- | --- |
| `index.html` 7, 358, 426–427, 717–719 | `FREE callouts` / `Free Callout and Expert Fitment` / `No hidden costs, ever.` / `our mobile callout, expert diagnosis, and professional fitment are completely free. No hidden costs.` |
| Live `/` FAQ | `Our mobile callout includes a service fee for travel time and on-site assistance. However, the battery testing and fitment service itself are 100% free.` |
| Live `/services/mobile-battery-replacement/alberton` | `Within 10km of New Redruth the callout is free with battery purchase. For outer Alberton suburbs a small R150 travel fee may apply—confirmed during booking.` |
| Live `/` | `Pay on Success` / `Secure mobile payments are processed only after the battery is coded and your engine successfully starts.` |

If ads still say blanket “Free Callout”, that is a reportable mismatch with the live FAQ. “Pay on success” is fine if it is true; disclose that the battery is still payable on a successful start, and that a callout fee may apply outside 10 km.

**Recommended single policy (publish identically on ads, homepage FAQ, service page, schema):**  
`In-store testing and fitment are free with battery purchase. Mobile callout is free within 10 km of 28 St Columb Rd when you buy the battery from us. Outside that radius a R150 travel fee is confirmed before dispatch. You pay after the engine starts.`

### C8. Homepage reviews look internally “Verified” (CPA s41; ARB 4.1)

Live `/` testimonials:

- `David C.` · Meyersdal · ★★★★★ · badge `Verified`  
- `Samantha P.` · Brackendowns · ★★★★★ · badge `Verified`  
- `Fleet Ops Mgr` · Alrode South · ★★★★★ · badge `Verified`

These are not linked to a Google review URL. `/reviews` and `/proof/toyota-hilux-battery-replacement-alberton` correctly say not to fabricate reviews. A “Verified” badge on anonymised quotes is a gift to a complainant.

This repo’s ticker uses named Google reviews (`House of Mack Nail Bar`, `Andre la Grange`, `Joanne Havenga`, `Pierre Coetzee`) with “via Google”. That form is safer **if** those reviews still exist on the GBP. They are duplicated in the DOM for the ticker animation (same four cards twice) — cosmetic, not a fake-count issue if not presented as eight distinct reviews.

**Recommended:** Replace homepage cards with current Google review embed/API, or quote full name + date + link. Remove the in-house “Verified” chip unless it means “copied from Google”.

### C9. No ECTA / CPA consumer pages on production

Live 404: `/privacy`, `/terms`, `/legal`, `/warranty`, `/returns`, `/privacy-policy`, `/terms-of-service`.  
No company registration number, VAT number, or returns process anywhere in the homepage HTML. Footer only: `Independent retailer — see Disclosure`.

This repo: same gap, plus the misspelt email.

**Recommended minimum footer/legal block:** business name, physical address, telephone, email, hours, VAT/registration if registered, warranty “as on invoice / manufacturer terms”, returns/cooling-off pointer, link to `/disclosure`.

---

## FIX SOON

Inaccurate, stale, or incomplete — fix before the next ad cycle, not as an emergency injunction risk.

### F1. Hours mismatch

User requirement: address and Mon–Sat hours identical on footer, contact, schema, GBP.

| Location | Hours |
| --- | --- |
| User brief | Mon–Sat (close time not specified) |
| Live footer, contact, schema, mobile page | Mon–Fri 08:00–17:00; **Sat 08:00–12:00**; Sun closed. Contact also: `Staff answer the shop line from 07:30 — store opens to the public at 08:00.` |
| `index.html` 65–69, 759–761, 818–819 | Sat **08:00–13:00** |
| `index.html` 71–76 | Sunday `opens: 00:00` / `closes: 00:00` (schema anti-pattern; omit closed days) |

Align this file and GBP to **Sat 12:00** unless the shop truly trades until 13:00 — in which case **change production**, not this file.

### F2. Address is consistent; geo is not

Address **28 St Columb Rd, New Redruth, Alberton, 1450** is consistent on live footer, contact, schema, and this file.

Live LocalBusiness JSON-LD: `latitude: -26.28291418340356`, `longitude: 28.12132331503201` — about **2.3 km south** of this file’s `-26.262524, 28.121908` and of the Google Maps embed (`-26.25817, 28.11933`). A wrong pin is a Maps / GBP integrity issue.

### F3. Warranty figures fight each other

| Surface | Claim |
| --- | --- |
| Live `/` hero | `Up to 36-Month Warranty` |
| Live WebPage JSON-LD | `24-month warranty` |
| Live FAQ | `up to 36 months on premium batteries (Willard EFB, Enertec AGM) and a minimum of 12 months on all standard automotive batteries` |
| Live `/646-car-battery` | `Up to 25-month warranty` in the rail; Willard 646 **25 mo**; Exide 646CE **24 mo**; Exide 646AGM **36 mo**; Eco Plus 646 **12 mo** |
| Product PDP e.g. `/products/id/110` | H2 `24-36 Month Warranty` plus body `25-month warranty when professionally fitted and registered` |
| `index.html` 431–432, 731–733 | `genuine, local, nationally supported warranty` with **no duration** |

**Recommended:** One rule — “Warranty is the manufacturer period printed on your invoice (commonly 12, 24, 25 or 36 months by range). We register it at fitment. Fitting the wrong technology (e.g. flooded in an AGM/EFB car) can void cover.” Hero: `Manufacturer warranty up to 36 months on selected ranges`.

### F4. Free testing / fitment / same-day / no appointment — mostly true, not fully consistent

Supported on live `/testing`, `/fitment`, `/contact`: free in-store 3-point test, no appointment during hours, same-day in-store fitment, mobile on request.

Gaps:
- Mobile testing is **not** always free of a callout fee (see C7).
- `index.html` title still says `Free Callout, Fitment & Testing` as if all three are always free.
- Fitment-free is tied to **purchase** on `/fitment` (`When you purchase a battery from our Alberton store, the fitment and testing service is entirely free`). Ads should say “free fitment with battery purchase”.

### F5. Mobile service exists — describe area and hours (do not kill the ads)

Live `/services/mobile-battery-replacement/alberton` is a proper service page: Alberton / Meyersdal / Brackenhurst, Mon–Fri 08:00–17:00, Sat 08:00–12:00, typical arrival within an hour, pay on site. **Do not pause the mobile ads.** Tighten:
- `60-Minute Average Response` on `/` vs `30-45 minutes` on `/services/mobile-battery-replacement/alberton-central` vs `45–60 minutes` on size hubs vs `often arriving within 30-60 minutes` in `index.html`. Pick **one** substantiated window: `Typical response 45–60 minutes inside Alberton during trading hours.`
- After-hours: `For urgent after-hours cases we do our best to assist` — too soft for an “average 60-minute” ad. Disclose `during trading hours` on the ad or the lander.

### F6. Stock claims 646 / 652 / 658 / 668 / AGM / EFB

Live size hubs list named SKUs as `In stock` with prices. `/products/all` says `Displaying all 171 products in stock.`

Risk: Exide catalogue lists dozens of lines as **P.O.A.** (and some as `0Ah`) while still saying they are “in stock”. CPA s29/s30: advertised goods must be genuinely available. P.O.A. + “in stock” on the same card is a complainant exhibit.

Power Plus / Eco Plus brand pages copy-paste Willard service blurbs: `On-site Willard swaps` / `Pair Willard 658/689 with fleet rotation plans.` Misleading as to what those pages sell.

Enertec brand intro sells `deep-cycle and lithium` / Land Rover dual-battery kits; the catalogue is **motorcycle** YTX/12N codes. Wrong category copy.

### F7. Prices, VAT, specials, scrap exchange

- No page states **VAT inclusive** (South African consumer prices must not surprise with VAT at the till — CPA s23).
- `Prices indicate complete in-store fitment and old battery core exchange` is good; header “from” prices omit it.
- `Scrap Required` / `Scrap exchange required` is a condition of the advertised price — keep it next to every price, including ad extensions.
- No dated “specials” with stock limits (good — do not invent urgency). Do not add “only 2 left” unless true.
- Size-hub FAQ `no hidden environmental fees` is acceptable positive framing. Avoid “traps / scams / rip-off”. **No current hit** for those disparagement words.

### F8. Comparative content vs Midas / Goldwagen / national chains

`/{size}-car-battery` FAQ:  
`Midas and Goldwagen usually sell shelf-price batteries without mobile fitment or charging-system diagnostics. Our fitted price includes on-site testing, professional installation, warranty registration, and old-battery disposal.`

This is a **permitted comparative of our merits** if true. Do not add “they overcharge / they trap you on trade-in”.

`/blog/honest-truth-about-sa-battery-brands`:  
`Most battery fitment centres are franchised, meaning they are paid to sell you one brand, regardless of whether it's the best fit for you.`  
“Fitment centres” is safer than “Battery Centre”, but “paid to sell you one brand, regardless” is disparagement of a class of competitors (ARB cl 6). Rewrite to our merit: `We are independent, so we can quote Willard, Exide, Enertec, Power Plus and Eco Plus on the same vehicle.`

### F9. Technical / OEM claims that need a file

- `Raylite is the OEM battery for 100% of SA car manufacturers` (blog, 25 Nov 2025) — hold the Metair/OEM letter or drop “100%”.
- `Willard remains the go-to OE battery for Hilux, Ranger…` (`/products/brand/willard`) — often false; many Toyota/Ford OE fits are Raylite/Motorcraft. Soften to `We supply Willard sizes commonly fitted to Hilux and Ranger in Alberton.`
- `index.html` 422: `the trusted original equipment manufacturers (OEM) for the world's leading car brands` — overbroad.
- Schema `https.schema.org` in this file (line 30) is **invalid** (`https://schema.org` required). Live schema is valid LocalBusiness + AutoPartsStore + AutoRepair.

### F10. Email, form, and contact hygiene

- `index.html` 37, 839: `admin@albaertonbatterymart.co.za` — undeliverable.
- Live FAQ CTA: `info@albertonbatterymart.co.za`; contact page: `admin@albertonbatterymart.co.za`. Pick one and use it in schema, footer, ads, GBP.
- `index.html` lead form has no `action` — quotes go nowhere (CPA/ECTA: don’t collect personal info you can’t process; also a conversion hole).

### F11. Colour / trade dress

Accent `#d10e00` on black is generic automotive red. No Battery Centre / Global Batteries / Atlas logos in this repo. Live brand pages use product photos named for the battery, not competitor storefronts. **No trade-dress hit in this audit.** Keep it that way.

---

## CLEAN

Confirmed-compliant or already in good shape. Do not “soften” these.

1. **Business name.** “Alberton Battery Mart” in titles, OG `og:site_name`, schema `name`, header, footer, live Organization JSON-LD. No “Battery Centre” as a self-name in current crawl.
2. **Physical address.** 28 St Columb Rd, New Redruth, Alberton, 1450 on live footer, contact, schema, this file, maps embed.
3. **Independence disclosure.** Live `/disclosure` plus footer `Independent retailer — see Disclosure.` Correct passing-off hygiene. Keep it.
4. **Reseller catalogues on production.** Willard / Exide / Enertec / Power Plus / Eco Plus are visibly for sale with names and prices. Google Ads brand bidding can rest on `/products/brand/{willard,exide,enertec,power-plus,eco-plus}` and the size hubs.
5. **Ad from-prices on production.** Power Plus from R1,150 and Eco Plus from R1,050 are real SKUs, not invented.
6. **Size stock landers.** 646 / 652 / 658 / 668 / 628 / 619 hubs list in-stock named products, fitted prices, scrap exchange, free fitment, AGM/EFB options.
7. **Free in-store testing.** `/testing` and `/fitment` state a free 3-point test and free fitment **with purchase**, no appointment for walk-ins. Keep; disclose the purchase condition on ads.
8. **Mobile service is real.** `/services/mobile-battery-replacement/alberton` describes area, hours, process, payment, coding. Ads for mobile replacement should land here, not on the old HTML.
9. **Lawful location messaging.** “Stuck … on Voortrekker Road? Our mobile team is minutes away” (`/local/alberton-central`) is geographic, not passing-off. “Skip Voortrekker Rd — we’re at 28 St Columb Rd” is equally lawful. Keep it.
10. **No disparagement keywords.** No current `scam`, `rip-off`, `traps`, `dishonest` hits. Keep it that way.
11. **This repo competitor scan.** Zero hits for battery centre/center, Global Batteries, Atlas, First Battery, Battery Clinic.
12. **Review-request page intent.** `/reviews` tells staff not to script fake reviews. Good. Do not let the homepage “Verified” cards undo that.
13. **Comparative brand guides** (Willard vs Exide vs Raylite) are lawful if they stay informational, name Alberton Battery Mart as the seller, and do not present ABM as a Battery Centre / Global Batteries outlet.
14. **Phone numbers.** 010 109 6211 and WhatsApp 082 304 6926 are consistent across surfaces.

---

## Ad claim checklist (what to do to each live ad)

| Live ad claim | Site support today | Action |
| --- | --- | --- |
| Alberton's Best Battery Prices / cheaper than Voortrekker Rd | **Unsubstantiated.** Disclosure says you are not always cheapest. | Change ad to beat-a-quote / fitted-price message **or** publish a dated comparison table with evidence on file. |
| Power Plus from R1,150 / Eco Plus from R1,050 | **Supported** on production brand pages. Missing on this HTML. | Point ads at `/products/brand/power-plus` and `/products/brand/eco-plus`. Add “incl. VAT, scrap exchange, selected sizes”. |
| Official Willard / Authorised stockist | **Do not use.** Site currently says “officially stock” / “official stockists”. | Ads and site: `Stockists of Willard, Exide, Enertec, Power Plus & Eco Plus`. |
| Free battery testing | **Supported** in-store and with fitment. | Keep. Say “in-store / with fitment”. |
| Free fitment | **Supported with purchase.** | Keep. Say “free fitment when you buy the battery from us”. |
| Same-day / fitted while you wait / no appointment | **Supported** for walk-ins during hours. | Keep. Mobile still needs a call. |
| Mobile replacement / we come to you | **Supported.** | Land on `/services/mobile-battery-replacement/alberton`. |
| 60-minute average response | **Inconsistent windows; no log published.** | `Typical 45–60 min in Alberton during trading hours` or publish a 90-day average. |
| Pay only on success | **Supported** on homepage step 3. | Keep; disclose callout fee outside 10 km. |
| 646/652/658/668/AGM/EFB in stock | **Supported** on size hubs **if stock is real.** | Refresh P.O.A. Exide lines; don’t mark unavailable SKUs in stock. |
| Address / Mon–Sat hours | Address yes. Sat close **12:00** on production, **13:00** here. | One hours set everywhere including GBP. |

---

## What this PR changes (this repo only)

`index.html` is brought into line with the production policy that already exists, without inventing affiliation or superlatives:

- Independent battery **shop / specialists** naming; no “certified/official stockist”.
- Stockists of Willard, Exide, Enertec, Power Plus, Eco Plus and Raylite, with visible from-prices for the ad brands.
- Callout / testing / fitment conditions aligned to the live 10 km / R150 rule.
- Hours Sat 08:00–12:00; schema, email, VAT, warranty and disclosure hygiene.
- Location merit kept: New Redruth vs Voortrekker Rd, mobile from 28 St Columb Rd.

Production Next.js copy listed under CRITICAL / FIX SOON still needs a separate patch in the live codebase.
