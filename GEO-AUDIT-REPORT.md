# GEO Audit Report: Enterline & Partners

**Audit Date:** 2026-09-29
**URL:** https://enterlinepartners.com/en/home/ (English homepage; canonical per the pasted HTML)
**Business Type:** Agency/Services (U.S. immigration law firm, YMYL) with Local-business signals (two offices)
**Pages Analyzed:** 1 (homepage HTML pasted by the requester)

> **Scope limit — read first.** The audit environment could not reach `enterlinepartners.com` (egress proxy denied the domain), so this audit covers **only the pasted homepage HTML**. Not checked: `robots.txt`, `sitemap.xml`, `llms.txt`, HTTP headers, any inner page (About, K-1, CR-1, EB-5, articles), real page speed, and all off-site brand presence (Reddit, Wikipedia, YouTube, LinkedIn content). Findings marked **[verify]** need a live check. The pasted HTML was rendered for a logged-in WordPress administrator (admin bar, nonces, plugin versions are visible), so it differs slightly from what crawlers see.

---

## Executive Summary

**Provisional on-page GEO Score: 58/100 (Poor, upper end)**, covering 70% of the scoring weight. **A full GEO score cannot be issued** because Brand Authority (20%) and Platform Optimization (10%) need off-site data. Depending on those two categories the full score would land between **40 and 70**.

The homepage has solid foundations: server-rendered content, `index, follow, max-snippet:-1`, hreflang for three languages, named attorneys, and FAQ answers that lead with concrete facts. The biggest gaps are structured-data quality (two conflicting LegalService entities, three different Ho Chi Minh City addresses, self-serving review markup), missing attorney credentials for a YMYL legal site, and unverified AI-crawler access (Wordfence is active, which can block bots regardless of robots.txt).

### Score Breakdown

| Category | Score | Weight | Weighted Score |
|---|---|---|---|
| AI Citability | 60/100 | 25% | 15.0 |
| Brand Authority | Not assessed | 20% | — |
| Content E-E-A-T | 58/100 | 20% | 11.6 |
| Technical GEO | 60/100 (on-page only) | 15% | 9.0 |
| Schema & Structured Data | 48/100 | 10% | 4.8 |
| Platform Optimization | Not assessed | 10% | — |
| **Provisional score (assessed categories, re-normalised over 70%)** | | | **58/100** |

Range for the full score: (4040 + 0…3000) / 100 = 40 to 70, depending on the two unassessed categories.

---

## Critical Issues (Fix Immediately)

None confirmed from the page itself. One potential critical item is unverified — see High #4.

## High Priority Issues

1. **Conflicting, duplicated structured data and inconsistent NAP.**
   - The live Rank Math graph (`#organization`, type `LegalService` + `Organization`) lists **only the Ho Chi Minh City office at "146C7 Nguyễn Văn Hưởng, Phường An Khánh"** with Vietnamese-language locality/country values (`addressCountry: "Việt Nam"` instead of `VN`). The Manila office is absent.
   - A **second, separate `LegalService` block** (no `@id`, so search engines treat it as a different entity) lists "146C7 Nguyen Van Huong St, Thao Dien Ward".
   - The visible footer lists **"Level 6 & 7, Friendship Tower, 31 Le Duan"**, the popup lists the same, and the mobile footer lists **"Suite 601, 6th Floor Saigon Tower, 29 Le Duan, Ben Nghe Ward"**.
   - A third, more complete JSON-LD object (both offices, `areaServed`, `serviceType`) is pasted **inside the `<style id="wp-custom-css">` block**, so it is treated as CSS and ignored by every parser.
   - **Fix:** confirm the true address(es), keep one `@graph` with one `LegalService` per office (`@id`-linked to one parent `Organization`), and delete the other blocks.
2. **Self-serving review markup.** The second block declares `aggregateRating` (5.0 / 18) and 18 `Review` items on the firm's own `LegalService` entity. Google does not treat self-authored reviews on LocalBusiness/Organization types as eligible for review snippets, and mismatched markup can erode trust. The `reviewBody` text is Vietnamese while the visible English testimonials differ. **Fix:** remove `aggregateRating`/`review` from the organization entity, or source them from a third-party platform (Google Business Profile, Avvo, Trustpilot) and mark up only content visible on the page.
3. **No verifiable attorney credentials (YMYL).** The homepage says "licensed U.S. immigration attorneys" but never names the bar jurisdiction(s), bar numbers, AILA membership or years admitted. Bios are truncated ("…"). No `Person` schema for David Enterline or Ryan Barshop. AI systems weigh this heavily for legal answers. **Fix:** add a credentials line to each bio card and `Person` (`jobTitle`, `alumniOf`, `memberOf`, `knowsAbout`, `sameAs`) linked to the organization via `employee`/`founder`.
4. **[verify] AI crawler access.** Wordfence is active (rate limiting / "Crawlers" rules can throttle or block GPTBot, ClaudeBot, PerplexityBot, Google-Extended even if `robots.txt` allows them). `robots.txt` was not visible. **Fix:** fetch `robots.txt` and test with AI user agents; review Wordfence *Rate Limiting → crawlers* and any host-level WAF/CDN bot rules.
5. **Brand/entity name inconsistency.** The page uses "Enterline & Partners", "Enterline and Partners", "Enterline Partners", "Enterline & Partners Consulting" and "Enterline and Partners Consulting". The FAQ itself contrasts law firms with "consulting firms", so the word *Consulting* in the header, footer, Facebook page name and copyright weakens the licensed-attorney positioning and splits the entity. **Fix:** pick one legal/trade name and use it everywhere (schema `name`, `alternateName` for variants).

## Medium Priority Issues

1. **FAQ not marked up.** Six substantive Q&As have no `FAQPage` JSON-LD. Also: numbering is wrong ("05." appears twice), and the cost answer contains no figures ("discussed during consultation"), so AI systems cannot quote it for the most common commercial query.
2. **Unsourced, undated facts.** Processing times (K-1 9–18 months, CR-1 12–24, EB-5 2–5 years, EB-3 5–6 years) and fee thresholds carry no source or "last reviewed" date. Add "Last reviewed: <date>" and cite USCIS/State Dept. Visa Bulletin pages.
3. **Stale freshness signals.** Footer reads "Copyright 2018 – 2025" (today is 2026). Twitter card metadata says "Written by: webadmin" and "Time to read: 11 minutes" on a homepage.
4. **Thin `sameAs`.** Only Facebook. The footer also links YouTube, LinkedIn (`/company/enterlinepartners`) and TikTok. Add those, plus Google Business Profile, Avvo/Justia/AILA profiles where they exist.
5. **Navigation duplicates and poor slugs.**
   - Mobile menu: "US Family Visas", "Business and Employment Visas" and "Other services" all link to `/en/home-2/`.
   - Desktop menu: "EB-2 Visa" and "EB-2 National Interest Waiver" share one URL.
   - "U.S. Tax Services" → `/en/elementor-12286/`; family visas hub → `/en/home-2/`. Descriptive slugs help both users and AI retrieval.
6. **Generic H1.** "U.S. Immigration Lawyers" has no geography; the title tag does. Consider "U.S. Immigration Lawyers in Vietnam and the Philippines".
7. **DOM debris in content.** The hero paragraph is wrapped in copied chat-UI markup (`font-claude-response`, `standard-markdown` …) and two content blocks embed hundreds of empty `jso-cursor-trail-shape` divs saved into the page body. Harmless to rankings but bloats HTML and can pollute extraction. Re-save those blocks as plain text.
8. **Outdated stack.** WordPress 6.6.9 with 13 pending updates, Elementor 3.33.2 vs Elementor Pro 3.30.1, 61 comments awaiting moderation.

## Low Priority Issues

- Title ≈ 70 characters and meta description ≈ 187 characters (both likely truncated; target ≤ 60 / ≤ 155).
- `og:image` is 622×401 (recommended ≥ 1200×630); its alt text "Our EB-5 Services" doesn't describe the image.
- hreflang lacks `x-default`; hreflang uses `zh` while the switcher uses `zh-TW`.
- Alt-text problems: `Enterlineparterns_logo` (typo), `logo`, `35 years`, and a Vietnamese alt on an English page ("Luật Sư Di Trú Mỹ Tại Việt Nam").
- Schema details: `openingHours` is formatted as "Monday,Tuesday… 09:00-17:00" (use `Mo-Fr 09:00-17:00` or `OpeningHoursSpecification`); logo is 40×45 (Google wants ≥ 112×112); no `geo`, `areaServed` or `priceRange` in the live graph; `sameAs`/`telephone` missing for the Manila office.
- Instagram icon in the header has no link.
- Duplicate element IDs (`form-field-email`, `form-field-name`, …) across the three forms.
- The featured YouTube video (`vCE9K0jhCzg`) is injected by JS; no `VideoObject` schema and no transcript on the page.

---

## Category Deep Dives

### AI Citability (60/100)
**Strong passages** (self-contained, answer-first, numeric):
- FAQ 01: "Yes. Enterline & Partners is founded and managed by licensed U.S. immigration attorneys, with offices in Ho Chi Minh City, Vietnam and Manila, Philippines…" — quotable as-is.
- FAQ 05: lists processing times per visa category as bullets — highly extractable.
- EB-5 tile: "The EB-5 visa grants U.S. residency to investors who invest $800K-$1.05M in a business creating 10 jobs." — concise, factual.

**Weak passages:**
- Hero: one ~60-word sentence that names services only generically.
- FAQ 04 (cost) gives no number or range.
- Visa tiles are one-liners without who/what/how long/cost.
- The page is mostly navigation, tiles and a testimonial carousel; the citable body copy is limited to the FAQ.

**Rewrite suggestion (FAQ 04):** "Fees depend on the visa category and case complexity. Enterline & Partners quotes a fixed fee in writing at the first consultation. For reference, a K-1 case typically involves [X] in attorney fees plus USCIS and consular fees of [Y]. Last reviewed [date]." (Fill with real figures.)

### Brand Authority (Not assessed)
Not possible without network access. Observed on-page signals only: Facebook, YouTube (@EnterlineAndPartnersConsulting), LinkedIn company page and TikTok linked in the footer; a "35 years" badge; peer-attorney testimonials (William White, Melissa Vincenty). To assess: Reddit (r/USCIS, r/vietnam, r/immigration), YouTube channel content, LinkedIn, EB-5 conference panel mentions, Avvo/Justia/AILA, Wikipedia/Wikidata.

### Content E-E-A-T (58/100)
- **Experience:** 18 named client testimonials; Ryan's Peace Corps 2003 background; David "in Asia since 1993".
- **Expertise:** named attorneys with specialties (EB-5; family consular processing), but truncated bios and no credentials.
- **Authoritativeness:** peer endorsements exist; no bar/AILA/awards evidence on the homepage.
- **Trust:** explicit no-guarantee statement (good, ethical); named offices and phone/email; but three HCMC addresses, inconsistent brand name, and stale copyright date.
- Recent blog headlines (Sept 2026) show ongoing publication, but bylines could not be checked (Twitter card shows "webadmin").

### Technical GEO (60/100, on-page only)
- ✅ Server-side rendered (WordPress + Elementor); testimonial and FAQ text is in the HTML.
- ✅ `robots` meta: `follow, index, max-snippet:-1, max-image-preview:large` — good for AI Overviews.
- ✅ Canonical and 3-language hreflang present; Rank Math `llms-txt` module is enabled **[verify `/llms.txt` output]**.
- ✅ GTM + GA4 configured.
- ⚠️ Heavy plugin stack (Elementor, Elementor Pro, Essential Addons, sticky header, chat plugin, Wordfence, cursor-trail effect). Admin-bar figure of 0.687 s / 151 queries is an uncached admin view, not a user metric.
- ⚠️ Outdated core/plugins, duplicate menu targets, slug quality (see above).
- ❓ `robots.txt`, sitemap, headers, Core Web Vitals, mobile rendering: not verified.

### Schema & Structured Data (48/100)
Types found: `LegalService` + `Organization`, `Place`, `WebSite` (with `SearchAction`), `ImageObject`, `WebPage` (Rank Math), plus a duplicate `LegalService` with `AggregateRating`/`Review`, plus a dead JSON-LD object inside CSS.
Missing: `Person` (attorneys), `FAQPage`, `Service`/`OfferCatalog` for K-1/CR-1/EB-5/EB-3/L-1A, `VideoObject`, per-office `LegalService` with `geo`, `BlogPosting` on articles **[verify]**.

**Consolidated template (fill every placeholder from verified facts — do not publish the guesses):**
```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://enterlinepartners.com/#organization",
      "name": "[ONE canonical firm name]",
      "alternateName": ["Enterline & Partners", "Enterline and Partners"],
      "url": "https://enterlinepartners.com/",
      "logo": "[≥112×112 logo URL]",
      "sameAs": [
        "https://www.facebook.com/enterlineandpartnersconsulting/",
        "https://www.linkedin.com/company/enterlinepartners",
        "https://youtube.com/@EnterlineAndPartnersConsulting",
        "https://www.tiktok.com/@enterlinepartnersvn"
      ],
      "founder": [{ "@id": "https://enterlinepartners.com/#david-enterline" }]
    },
    {
      "@type": "LegalService",
      "@id": "https://enterlinepartners.com/#office-hcmc",
      "parentOrganization": { "@id": "https://enterlinepartners.com/#organization" },
      "name": "[firm name] – Ho Chi Minh City",
      "telephone": "+84933301488",
      "email": "info@enterlinepartners.com",
      "address": { "@type": "PostalAddress", "streetAddress": "[VERIFIED ADDRESS]", "addressLocality": "Ho Chi Minh City", "addressCountry": "VN" },
      "openingHoursSpecification": [{ "@type": "OpeningHoursSpecification", "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"], "opens": "09:00", "closes": "17:00" }],
      "areaServed": ["VN", "PH"]
    },
    {
      "@type": "LegalService",
      "@id": "https://enterlinepartners.com/#office-manila",
      "parentOrganization": { "@id": "https://enterlinepartners.com/#organization" },
      "name": "[firm name] – Manila",
      "telephone": "+639175437926",
      "address": { "@type": "PostalAddress", "streetAddress": "LKG Tower, 37th Floor, 6801 Ayala Avenue", "addressLocality": "Makati City", "postalCode": "1226", "addressCountry": "PH" }
    },
    {
      "@type": "Person",
      "@id": "https://enterlinepartners.com/#david-enterline",
      "name": "David A. Enterline",
      "jobTitle": "Partner",
      "worksFor": { "@id": "https://enterlinepartners.com/#organization" },
      "knowsAbout": ["EB-5 Immigrant Investor Visa"],
      "memberOf": "[bar / AILA — fill in]"
    }
  ]
}
```

### Platform Optimization (Not assessed)
Needs live/off-site data. On-page readiness notes: Google AI Overviews — good (`max-snippet:-1`, FAQ-style content); Perplexity/ChatGPT — FAQ passages are quotable but need dates/sources; YouTube — channel exists, single embedded video, no transcript on page; Bing Copilot — no `IndexNow` evidence (Rank Math "instant-indexing" module is on, so likely available).

---

## Quick Wins (Implement This Week)

1. Decide the true HCMC address and make **schema, footer, popup and mobile footer match**; delete the duplicate `LegalService` block and the JSON-LD stuck inside `wp-custom-css`.
2. Remove self-authored `aggregateRating`/`review` from the organization markup (or source from a third-party platform).
3. Add bar admission / AILA / years-admitted lines to both attorney cards and publish `Person` schema.
4. Rewrite FAQ 04 with real fee ranges, fix the "05." numbering, add `FAQPage` JSON-LD and a "Last reviewed" date; update the footer copyright year.
5. Fetch `robots.txt` and `/llms.txt`, test AI user agents against Wordfence/host WAF rules, and add missing `sameAs` links (LinkedIn, YouTube, TikTok).

## 30-Day Action Plan

### Week 1: Entity consistency & crawler access
- [ ] Pick one legal/trade name; apply it in schema, header, footer, copyright, social profile names
- [ ] Reconcile the three HCMC addresses; add Manila to structured data
- [ ] Verify `robots.txt`, `llms.txt`, Wordfence bot rules, CDN/WAF
- [ ] Remove dead/duplicate JSON-LD

### Week 2: Credentials & trust
- [ ] Add bar/AILA credentials and full bios (About page + homepage cards)
- [ ] Publish `Person` schema; link `founder`/`employee`
- [ ] Replace self-serving review markup; add third-party review links

### Week 3: Citable content
- [ ] Add answer-first summaries (40–80 words) with figures and sources to K-1, CR-1, EB-5, EB-3 pages
- [ ] Add `FAQPage`/`Service` schema; add "Last reviewed" dates
- [ ] Add transcript + `VideoObject` for the featured YouTube video

### Week 4: Technical hygiene & measurement
- [ ] Fix duplicate menu targets and rename `/en/elementor-12286/` and `/en/home-2/` (301 redirects)
- [ ] Update WordPress/Elementor/plugins; clear comment queue
- [ ] Trim title/meta lengths; replace 622×401 OG image; fix alt text and hreflang `x-default`/`zh-TW`
- [ ] Re-run this audit against the live site (all pages, robots.txt, llms.txt, brand scan) and compute the full GEO score

---

## Appendix: Pages Analyzed

| URL | Title | GEO Issues |
|---|---|---|
| https://enterlinepartners.com/en/home/ | U.S. Immigration Lawyer in Vietnam & Philippines \| Enterline & Partners | 5 High, 8 Medium, 9 Low (see above) |

**Not fetched (network blocked):** `/robots.txt`, `/sitemap.xml`, `/llms.txt`, `/en/about-us/`, `/en/k-1/`, `/en/cr-1/`, `/en/eb-5/`, `/en/eb-3/`, `/en/faqs/`, `/en/news/` and all article pages.
