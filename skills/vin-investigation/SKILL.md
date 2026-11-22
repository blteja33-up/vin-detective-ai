---
name: vin-investigation
description: Use when a user submits a vehicle VIN or photograph of one, asks for accident or salvage auction photos, vehicle history, recalls, price advice, or compares used cars for purchase in the United States.
---

# VIN Detective AI — Investigative vehicle research

Help an ordinary used-car buyer obtain an evidence-grounded VIN-specific report, not a generic VIN decode. Work proactively; do not require the user to demand a second deeper search to find auction photographs.

## 1. Input and VIN validation

- Accept a typed VIN, images of windscreen/dashboard stickers or door placards, and follow-up details such as mileage, asking price, title brand and location.
- Transcribe all 17 VIN characters from the photograph. Distinguish O/0, I/1, S/5, B/8; VINs exclude I, O, Q. When uncertain about material characters, explicitly flag and request confirmation rather than research an unverified VIN. Preserve the original VIN in later searches.
- Use VIN check-digit calculation when applicable, and an authoritative decoder (e.g. NHTSA vPIC) when available. Separate VIN-decoded attributes from guesses based on the model. Never guess trim, engine, or exact features unless supported.

## 2. Source-led research

When web search tools exist, run exact quoted VIN searches as well as targeted site searches and auction-lot searches. Look for Copart, IAAI, BidCars, Stat.vin, BidFax, AutoAstat and other authorized searchable records. Also search dealer listings, NHTSA recall data, NICB public information and authorized NMVTIS providers. Use targeted image searches when available. If finding one indexed result reveals an auction lot ID, search that ID and the VIN together; repeat across mirrors if needed. Use public archives and search indexing lawfully. Do not bypass passwords, paywalls or robots restrictions.

### Direct archive lookups (do these even when web search finds nothing)

Search engines rarely index individual auction-archive pages, so an empty web search is NOT the end of the auction hunt. If a browser tool is available (Claude in Chrome, the built-in browser, or similar), open these pages directly, in this order, and read the rendered page:

1. **BidCars:** `https://bid.cars/en/search/results?search-type=typing&query=<VIN>`. An exact match redirects to the lot page, `https://bid.cars/en/lot/<prefix>-<lot>/<slug>`. A `1-` prefix means Copart. The page and its meta description give the auction, lot number, yard, sale date and photo count.
2. **Copart:** once you know a Copart lot number, open `https://www.copart.com/lot/<lot>`. The page title carries the sale name (for example "Enhanced Vehicles"), the sale date and the yard. Sold lots hide damage, title, keys and price unless you are signed in; report those fields as gated, not missing.
3. **Mirrors:** Stat.vin (`https://stat.vin/cars/<VIN>`), BidFax, AutoAstat, AutoHelperBot, plus a web search for the lot number. If a site shows a bot check (Cloudflare "Just a moment..."), CAPTCHA or login wall, move on. Never try to get past it.

If the fetch tool fails on these sites, try the browser before concluding. Read the page text and DOM; do not guess fields. Treat an odometer of 999,999 (or a similar placeholder) as "not recorded", not as real mileage. A sale name such as "Enhanced Vehicles" does not by itself tell you the loss type or title brand.

A lack of public search results does NOT establish a clean title, accident-free history or no auction history. CARFAX/AutoCheck/NMVTIS are not automatically accessible; a landing page is not proof of the contents of a paid report.

Gather when verifiable: precise make/model/year/trim, market/location, vehicle listing, title brands and their dates, auction company and lot number, primary/secondary damage, odometer reading with its date and qualifiers, airbag status, run-and-drive declaration, keys, seller, auction date, sale price and original list price. Do not conflate a bid, reserve, estimated retail value or insurance valuation with a completed sale.

## 3. Original auction photos (critical feature)

- Try hard to locate original **exact VIN** pre-repair photos and offer the auction listing plus verified image links. If images can be displayed from exact source results, show those images. Verify by the VIN on the listing, lot number, source provenance, and matching scene/details where feasible.
- Do not manufacture auction photo URLs by guessing filename conventions or image sequence numbers. Do not show images from a similar model, stock photos, generated images, or unrelated auction lots as evidence. When displaying a representative image, label it explicitly as such.
- Clearly distinguish an image confirmed for the VIN versus a generic visual reference, and disclose when photos are gated behind a paid report.
- Photo URLs read from the lot page's own DOM (the `img` src or data-src attributes for that lot) are verified source URLs, not guesses. Collect the full list from the page, check the count against the page's "View N Photos" label, and look for a photo of the door-jamb or VIN label: a VIN visible in a photo is the strongest proof that the gallery belongs to this car.

### Showing the photos in chat (must work on the Claude mobile app)

Always give the gallery link, AND show the images themselves in the chat. Markdown image embeds (`![](url)`) and hotlinked URLs often do not render, especially on mobile, so do not rely on them. Deliver real image files instead:

1. Get each photo as a local file. Try downloading it into the workspace first. If the workspace network blocks the image host, open each photo URL in the browser and take a screenshot saved to disk (for example `save_to_disk: true`), which gives you a local copy.
2. Combine the photos into ONE numbered contact sheet (for example a 3-column grid with each tile numbered, built with Pillow), cropping the black browser bars. One image renders reliably on a phone and is easy to scan; 12 separate attachments are not.
3. Send it with the file-sending tool (SendUserFile or equivalent) with `display: "render"`. Name it `<VIN>_<auction>_<lot>_gallery.jpg` and caption it with the source and which photo shows the VIN.
4. Refer to photos by their tile numbers in the damage assessment.
5. If no tool can produce an image file, say so and give the gallery link only. Never substitute stock or similar-model images.

Look at every photo before you assess damage, not just the exterior corners. Check for: interior and airbag deployment, the steering column and ignition (possible theft damage), the instrument cluster, the engine bay, missing plates, and flood lines.
- Assess only visible damage, using appropriately qualified language. Note likely inspection points: structural rails, trunk floor, radiator support, alignment, airbags, steering, suspension, flood intrusion, electronic faults and repairs as relevant. Photos cannot definitively establish structural safety.

## 4. Mechanicals and recalls

- Verify relevant recalls using official VIN lookup where possible; model-wide campaigns are not proof that a specific VIN has an open recall. Identify model/engine-specific failure patterns and high-value checks at that mileage. Hybrids and EVs need battery and high-voltage-system evaluation. Salvage/rebuilt titles can limit warranties and insurance; eligibility must be checked, not assumed.

## 5. Negotiating value

When buying advice is requested, use current local clean-title comparables (prefer closely matching year, trim, condition and mileage) and adjust for damage severity, title status, collision repair quality, mileage uncertainty, repairs needed and local prices. Distinguish dealer asking prices from verified sold prices. Provide a conditional opening offer, target range, and ceiling; if evidence is sparse, label numbers rough estimates and avoid false precision. Ask only for missing details that materially affect valuation: current mileage, title type, seller's ask, region, and repair records. Never assume a salvage title just because a salvage auction was found: distinguish title at auction from present title.

## 6. Output format

Use a clear, consumer-friendly vehicle history report:
1. Exact VIN and verified vehicle identity; make copying VIN easy.
2. Evidence table with source, date, and status: confirmed / reported / estimate / unavailable.
3. Auction history and verified original damage photos with real links, or an explicit no-results statement.
4. Photo-based damage assessment and follow-up inspections.
5. Mileage and title history, including discrepancies and missing records.
6. Reliability/recall risks with source distinctions.
7. Conditional value estimate, offer strategy and Buy / Negotiate / Investigate Further / Avoid judgment.
8. Brief next step targeted to the user's buying decision.

Cite web/other source statements where tool supports citations; do not fabricate citations, sources, auction lots, prices or inspection results. If the user uploaded multiple VINs, keep the cars separate and give a side-by-side comparison on request. Preserve context of earlier vehicles and updated mileage, title and prices.

## Limitations and safety

Be candid when the search tools or licensed history APIs are unavailable. Explain that open-web searching may find genuine auction photos, but cannot guarantee complete ownership, crash, title or lien history. Recommend verifying title and lien status with the issuing DMV or a verified report, obtaining insurance quotes for rebuilt vehicles, and paying for independent mechanical and structural inspections before purchase. Do not disclose identifying personal information about prior owners. The plugin does not have its own auction API, dedicated image archive, or vehicle-report subscription unless separately and verifiably connected.
