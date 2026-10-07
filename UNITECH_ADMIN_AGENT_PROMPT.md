# Add a Unitech pricelist tab in the admin back office

You are working in `Franksmittt/alberton_battery_mart` (the Next.js site behind albertonbatterymart.co.za). The public catalogue and `main` must stay as they are until a pull request is merged.

## Safety

- Branch off current `main`. Do not commit to `main`.
- Open a pull request. Do not merge it.
- Do not add these parts to `data/products.json`, the public catalogue, sitemaps, product pages, or Vercel Blob.
- Do not change existing selling prices.
- Do not change admin login or `ADMIN_PASSWORD`.
- These lines are back office only. Datasheets have not arrived, so nothing here is published.

## What to build

On `/admin`, add a tab named **Unitech** next to the existing catalogue price manager.

- **Catalogue** keeps the current price manager.
- **Unitech** shows this supplier pricelist. It is read-only. There is no Save button, because saving must not write these parts to the live site.

Suggested files:

- `src/lib/unitech-pricing.ts` — pricing math
- `src/data/unitech-pricelist.ts` — the 38 lines below
- `src/components/admin/UnitechPricelist.tsx` — the table
- `src/app/admin/page.tsx` — Catalogue and Unitech tabs
- `scripts/assert-unitech-pricing.ts` and an `assert:unitech-pricing` script in `package.json`

Admin is already `noindex`. Keep it that way.

## Pricing rule

Use **PRICE 5 PLUS** only. That column is the supplier cost **ex VAT**. Ignore **PRICE 25 PLUS**.

For each part:

1. Cost incl. VAT = ex VAT × 1.15
2. Price at 20% gross profit = cost incl. VAT ÷ 0.80
3. Round to the nearest R50. A tie rounds up.
4. If that nearest R50 leaves gross profit under 20%, add R50 until gross profit is at least 20%.
5. Profit incl. VAT = selling price − cost incl. VAT
6. Gross profit = profit incl. VAT ÷ selling price

Worked example, part `612A 24`:

- Ex VAT R 1 010.00
- Cost incl. VAT R 1 161.50
- R 1 161.50 ÷ 0.80 = R 1 451.88
- Nearest R50 is R 1 450.00, which is about 19.9% gross profit
- Raise it to **R 1 500.00**
- Profit incl. VAT **R 338.50**
- Gross profit **22.6%**

Do the math in integer cents so floating point does not move a price off a R50 step. Every selling price must be a multiple of R50, and every line must be at or above 20% gross profit.

## Table columns

- Part number
- Warranty
- Ex VAT (5+)
- Cost incl. VAT
- Selling price
- GP
- Profit incl. VAT

When a price was raised to hold 20%, show that the nearest R50 was lower. State on the tab that this list is not on the website and that PRICE 25 PLUS is not used.

Money format matches the rest of the admin: `R 1 010.00`.

## Supplier lines

Warranty is in months. The amount is PRICE 5 PLUS, ex VAT.

| Part number | Warranty | Ex VAT |
| --- | --- | --- |
| 612A 24 | 25 | R 1010.00 |
| 615A 24 With lip | 25 | R 820.00 |
| 615A 24 Without lip | 25 | R 820.00 |
| 616AP 24 With lip | 25 | R 820.00 |
| 616A 24 Without lip | 25 | R 820.00 |
| 618AP 24 | 25 | R 850.00 |
| 621 24 | 25 | R 1050.00 |
| 622 24 | 25 | R 1050.00 |
| 628A 24 | 25 | R 950.00 |
| 630A 24 | 25 | R 880.00 |
| 631A 24 | 25 | R 880.00 |
| 636A 24 | 25 | R 895.00 |
| 638A 24 | 25 | R 1350.00 |
| 639A 24 | 25 | R 1350.00 |
| 646A 24 | 25 | R 1080.00 |
| 646AGM 24 | 25 | R 2050.00 |
| 647A 24 | 25 | R 1250.00 |
| 650A 24 | 25 | R 1750.00 |
| 650 CR 24 | 25 | R 1370.00 |
| 650 AM 24 90A/H | 25 | R 1750.00 |
| 652A 24 | 25 | R 1175.00 |
| 652A AGM | 25 | R 2350.00 |
| 657A 24 | 25 | R 1250.00 |
| 658A 24 | 25 | R 1750.00 |
| 658A AGM 24 | 25 | R 2900.00 |
| 659A 24 | 25 | R 1650.00 |
| 668A 24 | 25 | R 1580.00 |
| 668A AGM 24 | 25 | R 2530.00 |
| 669 A 24 | 25 | R 1580.00 |
| 674 SAB POST | 18 | R 1850.00 |
| 674 SAS SCREW | 18 | R 1850.00 |
| 674 SAD DUAL | 18 | R 1850.00 |
| 682 AB | 18 | R 2150.00 |
| 683 AB | 18 | R 2150.00 |
| 688 AB | 18 | R 3150.00 |
| 689 AB | 18 | R 2450.00 |
| 695 AB | 18 | R 3300.00 |
| 696 AB | 18 | R 2825.00 |

There are 38 lines. Part numbers must match this spelling, including spaces.

## Check before you open the PR

- `612A 24` sells at R 1 500.00 with profit R 338.50, not R 1 450.00.
- `615A 24 With lip` sells at R 1 200.00 and does not need a lift.
- All 38 lines are at or above 20% gross profit.
- A search of the public site source shows none of these new part numbers added to the live catalogue.
- The pull request targets `main` and is left unmerged.
