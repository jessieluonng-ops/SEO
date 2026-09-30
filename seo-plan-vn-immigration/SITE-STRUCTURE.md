# Site Structure

```
/                              Home: who, where, top services, WhatsApp/Zalo CTA, reviews
/services/
  work-permit-vietnam/
  temporary-residence-card-trc/
  business-visa-vietnam/
  investor-visa-dt/
  visa-extension-vietnam/
  spouse-family-residence/
  permanent-residence-vietnam/
  company-sponsored-visas-for-employers/
/locations/
  ho-chi-minh-city/            (only for real offices / genuinely served)
  hanoi/
  da-nang/                     (add only with real presence; max 3–5 total, well under the 30-page warning)
/nationality/                  optional, only where requirements differ
  us-citizens/ uk-citizens/ korean-citizens/ ...
/resources/                    hub
  visa-requirements-by-country/
  document-checklists/
  processing-times-and-fees/
  immigration-law-updates/     dated, freshness signal
  faq/
/blog/                         informational long-tail
/team/
  lawyer-name/                 Person + credentials, bar membership, languages
/about/ (incl. /editorial-policy, /how-we-review)
/reviews/
/contact/
/vi/                           mirror of core pages, natively written, hreflang-linked
```

## URL rules
Lowercase, hyphenated, no dates in evergreen URLs, no parameters. One canonical per page. `hreflang` `en` ↔ `vi` (+ `x-default`).

## Internal linking
- Every service page links to: its checklist, its FAQ, the relevant location page, the lawyer profile, 2–3 related services.
- Every blog/resource links up to the matching service page with descriptive anchors ("apply for a Vietnam work permit"), not "click here".
- Home and footer link to all service pages. Breadcrumbs everywhere.

## Sitemap
XML sitemap split: pages, resources/blog, vi. Only indexable 200 URLs, accurate `lastmod` (real content changes only). Exclude thin tag/search pages. Submit in GSC and Bing.

## Schema plan
| Page | Schema |
|---|---|
| Home / Contact | `LegalService` (LocalBusiness subtype) + `Organization`, `WebSite`, geo, openingHours, areaServed, sameAs |
| Service | `Service` (provider → LegalService), `FAQPage` only if content is visible; `BreadcrumbList` |
| Lawyer | `Person` (+ `ProfilePage`), `hasCredential`, `worksFor`, `knowsLanguage` |
| Article/Resource | `Article` with author `Person`, `datePublished`, `dateModified`, reviewer |
| Reviews | Only real, first-party-visible reviews; never self-serving markup that violates Google policy |
