# EB-5 page: improvement brief
Page: https://enterlinepartners.com/en/eb-5/  ·  Based on the page text you pasted (2026-10-06) and the Search Console export (6 months to 2026-09-30).
Not assessable from pasted text: title tag, meta description, canonical, hreflang, schema, image alt/size, Core Web Vitals. Send the page source or open the domain to the sandbox to check these.

## 1. Search position
4,297 impressions, 5 clicks, 0.12% CTR, average position 16.9 (page 2). Related queries: `eb5 vietnam` (14.4), `eb-5 consulting firms` (7.6), `eb5 services` (24), Vietnamese "tư vấn eb5" queries (10–33).

## 2. Findings, by priority

### Critical
1. **Menu links go nowhere.** "U.S. FAMILY VISAS", "BUSINESS AND EMPLOYMENT VISAS" and "EB-5 Visa" all link to `/en/eb-5/#`. Crawlers and visitors cannot reach CR-1, K-1 or EB-3 from the menu, and the site's link value is not passed on. Point each to a real page or a real dropdown with crawlable links.
2. **The page never speaks to Vietnamese investors,** the audience in your search data. "Vietnam" appears only in the office address and the consulate line. Add a Vietnam-specific section (see section 4).
3. **Main button goes to the wrong place.** "Request More Information" links to `/en/about-us/`. Link it to the contact form on this page or the contact page. Add Zalo and WhatsApp next to the phone number.

### High
4. **Possible factual or wording problems to verify before the next edit:**
   - "No minimum ... age ... requirement": investor petitions normally require an adult. Check against USCIS guidance.
   - "Children admitted to public universities at the same tuition as U.S. residents": in-state tuition depends on each state's residency rules. Soften or remove.
   - "unmatched by other immigration attorneys": comparative claim, likely restricted by lawyer-advertising rules. Remove.
   - Copyright line says 2018–2025 while the page shows September 2026 posts.
5. **The "projects we represented investors in" list (36 names)** adds little for a reader and may raise client-confidentiality and endorsement questions, including for projects with public problems. Have a partner review it. Replace with a short summary ("investors in more than 35 regional centers", if accurate) and a link to a vetted page. It also pulls in off-target searches: about 1,900 impressions on "evaluate ... CMB ..." queries with zero clicks.
6. **Testimonials are almost all family visas** (CR-1, K-1) and are duplicated in the page text. Show EB-5 testimonials first, or label them by visa type, and remove the duplicated block. Do not mark them up as ratings (see schema).
7. **Duplicate paragraph.** The "management requirement" point is said twice in a row. Merge into one.
8. **Thin on the points investors search for:** costs, timeline, risk, source of funds in detail, regional center status and the current priority date for Vietnam. The FAQ questions exist, but check the answers are in the page HTML and not loaded only after a click.

### Medium
9. **Only two in-body links,** and one (I-829) goes to a COVID-era post. Add the links in section 5.
10. **No "last reviewed" date or reviewer line.** Add "Reviewed by David Enterline, Esq., [date]".
11. **Headings:** repeated "EB-5 Immigrant Investor Visa" (H1 and H2), lowercase "hear from enterline & partners clients", "Visa eB-5 projects". Use one H1 and descriptive H2s.
12. **Both offices need clear contact details** in a visible block (Ho Chi Minh City and Manila), matching your Google Business Profile.

## 3. New title, meta description, H1
| Element | Proposal | Chars |
|---|---|---|
| Title | EB-5 Visa for Vietnamese Investors \| Enterline & Partners | 57 |
| Meta | Licensed U.S. EB-5 attorneys in Ho Chi Minh City and Manila. Requirements, $800,000 / $1,050,000 thresholds, timeline and source of funds explained. | 148 |
| H1 | EB-5 Immigrant Investor Visa for Vietnamese and Asian Investors | |

## 4. Suggested page outline (about 1,800–2,200 words)
1. **Intro answer (80–100 words):** what EB-5 is, the two thresholds, 10 jobs, and who the firm is. Keep your existing opening, minus the duplicate paragraph.
2. **Quick facts box:** thresholds, jobs, at-risk capital, lawful source of funds, conditional residence of two years, I-829.
3. **EB-5 for Vietnamese investors (new, 250–350 words):** the Vietnam waiting list in the latest Visa Bulletin [insert current status and date], moving funds out of Vietnam and documenting them, consular processing in Ho Chi Minh City. Link to the existing Vietnamese-investor article and `/eb-5-vi/`. Verify every statement.
4. **Direct vs regional center** (keep, fix the "Entrepreneurial" label).
5. **Step-by-step process** with the I-526E, visa or adjustment, and I-829 timeline.
6. **Source of funds** (200 words, link to the existing source-of-funds article).
7. **Costs and fees:** what the firm's fee covers, in general terms, and a link to current USCIS fees.
8. **Risks:** capital at risk, project and regional center due diligence, program-status changes. This builds trust.
9. **Why us:** David Enterline's experience, offices, AILA membership. Add a named, dated proof point only if the firm can document it.
10. **FAQ** (keep your 12 and add Vietnam-specific ones: "Can I use funds from Vietnam?", "How long is the wait for Vietnamese investors?").
11. **Related news and contact form.**

## 5. Internal links to add (existing posts)
- `/en/what-is-the-eb-5-reform-and-integrity-act-of-2022/`
- `/en/how-long-do-i-have-to-wait-for-my-eb-5-petition-to-be-approved/`
- `/en/what-are-lawful-source-of-funds-and-path-of-funds-for-an-eb-5-immigrant-investor/`
- `/en/when-can-i-receive-back-my-capital-from-my-eb-5-investment/`
- `/en/green-card-through-investment-is-the-eb-5-visa-worth-it-for-vietnamese-investors/`
- `/en/what-is-concurrent-filing-of-eb-5-petitions-and-applications-for-adjustment-of-status/`
- `/en/establishment-of-an-eb-5-regional-center/`
- Vietnamese: `/eb-5-vi/` (also with hreflang)
Update the I-829 link to a current I-829 article.

## 6. Schema (add as JSON-LD)
Do not add FAQPage markup for rich results (retired May 2026). Do not add AggregateRating from on-site testimonials. Fill the bracketed values before use.
```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "LegalService",
      "@id": "https://enterlinepartners.com/#firm",
      "name": "Enterline & Partners",
      "url": "https://enterlinepartners.com/",
      "telephone": "+84933301488",
      "email": "info@enterlinepartners.com",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "Level 6 & 7, The Friendship Tower, 31 Le Duan",
        "addressLocality": "Ho Chi Minh City",
        "addressCountry": "VN"
      },
      "areaServed": ["Vietnam", "Philippines", "Taiwan"],
      "sameAs": ["[Google Business Profile URL]", "[LinkedIn URL]"]
    },
    {
      "@type": "Person",
      "@id": "https://enterlinepartners.com/#david-enterline",
      "name": "David Enterline",
      "jobTitle": "Managing Partner",
      "worksFor": {"@id": "https://enterlinepartners.com/#firm"}
    },
    {
      "@type": "WebPage",
      "@id": "https://enterlinepartners.com/en/eb-5/",
      "name": "EB-5 Visa for Vietnamese Investors",
      "inLanguage": "en",
      "dateModified": "[YYYY-MM-DD]",
      "reviewedBy": {"@id": "https://enterlinepartners.com/#david-enterline"},
      "about": {"@type": "Service", "name": "EB-5 immigrant investor visa legal services", "provider": {"@id": "https://enterlinepartners.com/#firm"}}
    }
  ]
}
```

## 7. Measure
Track in Search Console after 4–8 weeks: position and CTR for `/en/eb-5/`, `eb5 vietnam`, `eb-5 consulting firms`, and the Vietnamese "tư vấn eb5" queries. Realistic goal: page 1 (position 10 or better) for the Vietnam-focused phrases. Plain "eb-5" is dominated by USCIS and large directories.
