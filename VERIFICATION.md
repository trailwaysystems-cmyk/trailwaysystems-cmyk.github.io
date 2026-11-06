# Hub verification and product-source notes

Checked November 6, 2026, from the box (America/Chicago). No storefront or social-media settings were changed, and no new spend was incurred.

## Catalog counts

| Arena | Products | Store / format buttons |
|---|---:|---:|
| Livestock | 3 | 9 |
| Coins / Collection | 2 | 4 |
| Firearm records | 1 | 3 |
| Vehicle & Motorcycle | 2 | 10 |
| Boat & Trailer | 1 | 5 |
| Dog & Health | 2 | 9 |
| Budget & Tax | 1 | 3 |
| Estate & Household | 1 | 0 |
| Field logs | 1 | 1 |
| Bundles (RV & Travel) | 1 | 1 |
| RV & Camping (stopped, existing offers) | 5 | 7 |
| **Total** | **20** | **52** |

Buttons are counted per destination (a store's digital-download listing and each print format when distinct). Bundles are counted separately as products. Every external store link has `utm_source=xbio`, `utm_medium=hub`, `utm_campaign=hub`, and `utm_content=<product>-<store>`.

## URL checks

`reports/link-checks.json` records exact URLs, timestamps and curl statuses. All 52 destinations are unique with UTM tags. Two added paperback buttons use `utm_content=firearm-amazon-pb` and `utm_content=dog-amazon-pb`.

| Store | Buttons | Result |
|---|---:|---|
| Gumroad | 14 | 200 for all 14 exact UTM-tagged URLs. No 404s. |
| Amazon | 14 | 200 for all 14 exact direct-ASIN URLs in the full curl sweep. Includes new Firearm `B0HQ1FT7QT`, Dog `B0HQ16GNRR` and documented bound RV `B0H52Y6PGL`. |
| Etsy | 15 | 403 from the box for all 15 exact UTM-tagged listing URLs; expected Etsy bot restriction, not an asserted listing failure. |
| Payhip | 9 | 403 from box curl for the storefront with each distinct UTM content value. The public reading tool successfully loaded the storefront with UTM tags and displayed all nine corresponding digital products: Cattle, Horse, Coin, Vehicle, Motorcycle, Powerboat, Dog, Migraine, Irregular Income. No Firearm link. |

No link returned 404. Two provisional Amazon ISBN-search routes for Dog and Firearm returned 503 and were removed earlier. Only documented direct destinations were kept.

Amazon title evidence for this addition: Dog passed curl with HTTP 200 and a title beginning `Dog Health & Vaccination Record: Vaccines & Rabies Tags...` and including Trailway Systems and ISBN `9798166918314`. Firearm returned HTTP 200 on retries but curl repeatedly received a short interstitial titled only `Amazon.com`; one earlier attempt returned a transient 503. A separate public fetch of the exact Firearm `/dp/B0HQ1FT7QT` URL returned the product page titled `Personal Firearm Inventory: Insurance, Appraisal & Estate Record with Master Index, 100 Item Pages, Accessory Serial Log and Beneficiary Instructions`, Trailway Systems, Paperback, ASIN `B0HQ1FT7QT`. Thus its title is confirmed by the public reader, not misrepresented as a successful curl title check. No other Amazon title was newly tested.

## Sources and print formats

- KDP publication reports and title records under `/home/box/kdp-research/catalog/`, current operations summaries under `/home/box/kdp-research/ops/`.
- Horse paperback `B0HP821GHB` independently matched by ISBN/title/author in a public Amazon search and agrees with Big Boss's current status.
- Vehicle, Powerboat and Motorcycle 6×9 editions come from the hardcover report and weekly publication records.
- Migraine 6×9 editions come from the Oct 25 / Nov 1 reports.
- RV Trip Operations `B0H52Y6PGL` is confirmed by `catalog/titles/B0H52Y6PGL/title.json`, 51 pages, paperback.
- Cattle paperback `B0HNH8Y54W` is confirmed by live publication and order records. The 8.5×11 trim is not a small range-bag format.
- Firearm paperback `B0HQ1FT7QT` and Dog paperback `B0HQ16GNRR` were supplied from the Nov 8 operations report and matched to their existing KDP identifiers/ISBNs (`9798166913777` and `9798166918314`). Direct buttons were added; no search links or guessed ASINs remain.
- Firearm copy remains record keeping only: personal inventory, serial-number, insurance, appraisal and estate records. Its button is Etsy, Gumroad and Amazon only; no Payhip or firearm-transaction wording.
- The previous `Amazon paperback is listed / direct link pending ASIN verification` note was removed from Dog; Firearm had no remaining pending note in the HTML.

## Coming soon (no linked format)

1. Coin Collection Inventory paperback — scheduled for Nov 8 in the current Nov 6 queue; no published ASIN on file.
2. Dog Health & Vaccination Record hardcover — draft-only, conditional on Nov 8 publication gate; no ASIN on file.
3. Household Records & Executor Handoff paperback — scheduled for Nov 8 in the current Nov 6 queue; no published ASIN on file.

Business Mileage and Rental Property are named as future print editions in the format explainer, not counted as product cards, coming-soon offers, or purchasable formats. They are still publication-queue items without published ASINs.

## Missing ASINs / unresolved records

The two Firearm and Dog paperback ASINs are now resolved above; neither remains missing.
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

- Headless-Chromium live mobile QA at 390px wide is recorded in `reports/live-verification.json` after the new deployment; `mobile-screenshot.png` is the refreshed full-page image of the deployed URL. Source DOM audit is 20 cards and 52 buttons; live counts and width are asserted below.
- Live `assets/style.css` and `assets/trailway-gravel.webp` return 200; screenshot image assertion confirms all images loaded.
- All nine distinct UTM-tagged Payhip storefront URLs loaded through the public reading tool and showed their intended titles. The box curl 403 is an access restriction, not a missing page.
- Tagline changed to `Less guesswork. Better records.` in the visible hero, `<title>`, description, Open Graph title/description and new Twitter card/title/description tags. `git grep` confirms no retired wording in tracked text. Live curl verification is recorded after Pages deployment.
- `reports/live-verification.json` has the HTTP, viewport, image, count and deployment checks.
- Static HTML and CSS only; no JavaScript frameworks, page scripts, font downloads, embeds or analytics.
- Local favicon and optimized WebP brand art (~37 KB).
- Owner-selected gravel-road art: `/workspace/products/x-profile/pfp-1-gravel.jpg`.
- Source scan finds no restricted owner/private-brand strings in HTML, CSS, JSON, Markdown, text, XML or scripts in the public root; Git is excluded because object compression is binary. Commit author is Trailway Systems at its public store address.

## This release

Changed November 6, 2026: 20 products remain; total store/format buttons increased from 50 to 52. Firearm now has 3 buttons; Dog & Health has 9. Coin paperback, Household paperback and Dog hardcover still have no links and remain coming soon.
