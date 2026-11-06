# Hub verification and product-source notes

Checked November 6, 2026, from the box (America/Chicago). No storefront or social-media settings were changed, and no new spend was incurred.

## Catalog counts

| Arena | Products | Store / format buttons |
|---|---:|---:|
| Livestock | 3 | 9 |
| Coins / Collection | 2 | 4 |
| Firearm records | 1 | 2 |
| Vehicle & Motorcycle | 2 | 10 |
| Boat & Trailer | 1 | 5 |
| Dog & Health | 2 | 8 |
| Budget & Tax | 1 | 3 |
| Estate & Household | 1 | 0 |
| Field logs | 1 | 1 |
| Bundles (RV & Travel) | 1 | 1 |
| RV & Camping (stopped, existing offers) | 5 | 7 |
| **Total** | **20** | **50** |

Buttons are counted per destination (a store's digital-download listing and each print format when distinct). Bundles are counted separately as products. Every external store link has `utm_source=xbio`, `utm_medium=hub`, `utm_campaign=hub`, and `utm_content=<product>-<store>`.

## URL checks

`reports/link-checks.json` records exact URLs, timestamps and curl statuses. All 50 destinations are unique with UTM tags.

| Store | Buttons | Result |
|---|---:|---|
| Gumroad | 14 | 200 for all 14 exact UTM-tagged URLs. No 404s. |
| Amazon | 12 | 200 for all 12 exact direct-ASIN URLs. Includes documented bound RV `B0H52Y6PGL`. |
| Etsy | 15 | 403 from the box for all 15 exact UTM-tagged listing URLs; expected Etsy bot restriction, not an asserted listing failure. |
| Payhip | 9 | 403 from box curl for the storefront with each distinct UTM content value. The public reading tool successfully loaded the storefront with UTM tags and displayed all nine corresponding digital products: Cattle, Horse, Coin, Vehicle, Motorcycle, Powerboat, Dog, Migraine, Irregular Income. No Firearm link. |

No link returned 404. Two provisional Amazon ISBN-search routes for Dog and Firearm returned 503 and were removed. Only documented destinations were kept.

## Sources and print formats

- KDP publication reports and title records under `/home/box/kdp-research/catalog/`, current operations summaries under `/home/box/kdp-research/ops/`.
- Horse paperback `B0HP821GHB` independently matched by ISBN/title/author in a public Amazon search and agrees with Big Boss's current status.
- Vehicle, Powerboat and Motorcycle 6×9 editions come from the hardcover report and weekly publication records.
- Migraine 6×9 editions come from the Oct 25 / Nov 1 reports.
- RV Trip Operations `B0H52Y6PGL` is confirmed by `catalog/titles/B0H52Y6PGL/title.json`, 51 pages, paperback.
- Cattle paperback `B0HNH8Y54W` is confirmed by live publication and order records. The 8.5×11 trim is not a small range-bag format.
- Dog and Firearm are documented as retail-listed in the Nov 8 run sheet, but their ASINs are not captured in those files. Their digital options remain linked; no guessed ASINs or fragile search links are used.

## Coming soon (no linked format)

1. Coin Collection Inventory paperback — scheduled for Nov 8 in the current Nov 6 queue; no published ASIN on file.
2. Dog Health & Vaccination Record hardcover — draft-only, conditional on Nov 8 publication gate; no ASIN on file.
3. Household Records & Executor Handoff paperback — scheduled for Nov 8 in the current Nov 6 queue; no published ASIN on file.

Business Mileage and Rental Property are named as future print editions in the format explainer, not counted as product cards, coming-soon offers, or purchasable formats. They are still publication-queue items without published ASINs.

## Missing ASINs / unresolved records

- Personal Firearm Inventory paperback: KDP ID `EECHYHA5S0Q`, ISBN `9798166913777`; ASIN absent from available files.
- Dog Health & Vaccination Record paperback: KDP ID `AH1Q3F8QW4W`, ISBN `9798166918314`; ASIN absent from available files.
- Dog Health & Vaccination Record hardcover: KDP draft ISBN `9798166921666`; no published ASIN on file.
- Coin and Household paperbacks are planned in a future queue, not yet assigned confirmed ASINs.
- Business Mileage and Rental Property paperback/hardcover ASINs do not exist in these files; no scheduled-store link is asserted.
- Cattle and Horse do not have confirmed hardcover editions; existing 8.5×11 layouts would need a separate reflow, not a cheap upload.
- Payhip product permalinks could not be extracted through the public tools (storefront readable; product URL tokens are not exposed). Buttons label the storefront step explicitly instead of inventing paths.

## Gaps that could be filled cheaply, subject to owner approval

No listings or stores were changed. The PDFs and covers already exist for these candidates:

- Clone four RV-only PDF listings to Gumroad using a single existing canonical product link per title: RV Maintenance, Campground Review, RV Packing, RV Trip Planner. Split part-supported RV products are not linked into Payhip's whole-store button.
- Complete the Payhip RV set if deliberately reopening that avenue; current hub uses only whole-product Payhip support to avoid implying unavailable individual product coverage.
- Add the two non-RV Gumroad bundles (Homestead & Animals; Collector & Records) to the free Payhip storefront with existing assets. Keep Firearm off Payhip and retain RV lower on the hub.
- Add the RV & Travel Records Bundle to Payhip alongside those two non-RV bundles. The three already-live Gumroad bundles have confirmed listing links under `/workspace/briefs/big-boss-status.md`.
- Capture Payhip product permalinks in a future approved listing pass and replace explicit whole-store buttons with direct product URLs. This changes destinations only, not the hub design.
- Estate/Household and Business Mileage print editions already have prepared packages but need normal publication, QA and ASIN capture before linking. Business Mileage and Rental Property records are future print editions only.
- If appropriate, prepare a stylus-friendly fillable PDF as a separate delivery format only for titles whose current files are printable-only; do not imply those PDFs are fillable today.

## Technical QA

- Live Playwright/headless-Chromium QA: root returned 200; at a 390px-wide viewport the full page has 20 cards, 50 buttons and no horizontal overflow (`scrollWidth == 390`). `mobile-screenshot.png` is a full-page screenshot of that deployed URL (10,593px tall).
- Live `assets/style.css` and `assets/trailway-gravel.webp` return 200; screenshot image assertion confirms all images loaded.
- All nine distinct UTM-tagged Payhip storefront URLs loaded through the public reading tool and showed their intended titles. The box curl 403 is an access restriction, not a missing page.
- `reports/live-verification.json` has the HTTP, viewport, image, count and deployment checks.
- Static HTML and CSS only; no JavaScript frameworks, page scripts, font downloads, embeds or analytics.
- Local favicon and optimized WebP brand art (~37 KB).
- Owner-selected gravel-road art: `/workspace/products/x-profile/pfp-1-gravel.jpg`.
- Source scan finds no restricted owner/private-brand strings in HTML, CSS, JSON, Markdown, text, XML or scripts in the public root; Git is excluded because object compression is binary. Commit author is Trailway Systems at its public store address.
