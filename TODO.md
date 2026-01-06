# TODO

## Stage A: Repo Scaffold + Config + Layout + Libs + SEO Endpoints + DevContainer + Tooling

- [ ] Initialize Next.js project with App Router
- [ ] Set up TypeScript configuration (`tsconfig.json`)
- [ ] Configure Tailwind CSS (`tailwind.config.ts`, `postcss.config.js`)
- [ ] Set up ESLint configuration
- [ ] Create `.devcontainer/devcontainer.json`
- [ ] Create `src/config/site.ts` with all required interfaces and types:
  - [ ] `BookingEmbedConfig`
  - [ ] `AnalyticsConfig`
  - [ ] `SpamProtectionConfig`
  - [ ] `CopyBlocks`
  - [ ] `PackagedOffer`
  - [ ] `Segment`
  - [ ] `ProcessStep`
  - [ ] `CaseStudy`
  - [ ] `TeamMember`
  - [ ] `Resource`
  - [ ] `QualificationField`
  - [ ] `QualificationFormConfig`
  - [ ] `SiteConfig`
  - [ ] Export `siteConfig` with `TODO:INPUT` placeholders
- [ ] Create `src/app/layout.tsx`
- [ ] Create `src/app/globals.css`
- [ ] Create `src/lib/tracking.ts`
- [ ] Create `src/lib/analytics.ts`
- [ ] Create `src/lib/schema.ts`
- [ ] Create `src/lib/seo.ts`
- [ ] Create `src/lib/rateLimit.ts`
- [ ] Create `src/lib/utils.ts`
- [ ] Create `src/app/robots.ts` (include `Sitemap: ${baseUrl}/sitemap.xml`)
- [ ] Create `src/app/sitemap.ts`
- [ ] Create `README.md`

## Stage B: Components/Sections + Pages/Routes

### Components

- [ ] `src/components/Header.tsx`
- [ ] `src/components/Footer.tsx`
- [ ] `src/components/StickyCTA.tsx` (sticky "Book Consult" on every page)
- [ ] `src/components/JsonLd.tsx`
- [ ] `src/components/NAP.tsx`
- [ ] `src/components/ContactMethods.tsx`
- [ ] `src/components/QualificationForm.tsx`
- [ ] `src/components/SchedulerEmbed.tsx`
- [ ] `src/components/ProofStack.tsx`
- [ ] `src/components/Testimonials.tsx`
- [ ] `src/components/FAQ.tsx`
- [ ] `src/components/ServiceCards.tsx`
- [ ] `src/components/CaseStudyCards.tsx`
- [ ] `src/components/TeamGrid.tsx`

### Section Components

- [ ] `src/components/sections/HeroSection.tsx`
- [ ] `src/components/sections/WhoWeHelpSection.tsx`
- [ ] `src/components/sections/ServicesSection.tsx`
- [ ] `src/components/sections/ProofSection.tsx`
- [ ] `src/components/sections/ProcessSection.tsx`
- [ ] `src/components/sections/CaseStudiesPreviewSection.tsx`
- [ ] `src/components/sections/FAQSection.tsx`
- [ ] `src/components/sections/CTASection.tsx`

### Pages/Routes

- [ ] `src/app/page.tsx` (Home) — sections in order:
  1. HeroSection
  2. WhoWeHelpSection
  3. ServicesSection
  4. ProofSection
  5. ProcessSection
  6. CaseStudiesPreviewSection
  7. FAQSection
  8. CTASection
- [ ] `src/app/services/page.tsx` (Packaged offers)
- [ ] `src/app/who-we-serve/page.tsx` (Industries/segments)
- [ ] `src/app/process/page.tsx`
- [ ] `src/app/case-studies/page.tsx`
- [ ] `src/app/case-studies/[slug]/page.tsx`
- [ ] `src/app/team/page.tsx`
- [ ] `src/app/resources/page.tsx`
- [ ] `src/app/resources/[slug]/page.tsx`
- [ ] `src/app/book/page.tsx` (Qualification + scheduling)
- [ ] `src/app/contact/page.tsx`
- [ ] `src/app/testimonials/page.tsx`
- [ ] `src/app/policies/page.tsx`
- [ ] `src/app/privacy/page.tsx`
- [ ] `src/app/terms/page.tsx`
- [ ] `src/app/not-found.tsx`

### API Routes

- [ ] `src/app/api/lead/route.ts`:
  - [ ] Honeypot field + rejection
  - [ ] In-memory rate limiting per IP (TODO:PROD seam)
  - [ ] Input sanitization
  - [ ] Turnstile verification (if enabled)
  - [ ] Webhook forwarding (if configured)

## Stage C: QA Checklist + Final Notes

### Quality Bar (Must Pass)

- [ ] `npm run dev` — no errors
- [ ] `npm run build` — no errors
- [ ] `npm run lint` — no errors
- [ ] No runtime errors
- [ ] No lorem ipsum — use explicit `TODO:INPUT` for unknown values

### UX Rules Verification

- [ ] Mobile-first design
- [ ] Sticky primary CTA = "Book Consult" on every page
- [ ] Secondary CTA on mobile sticky bar: "Call" or "Contact"
- [ ] Sticky bar does NOT cover content (global bottom padding)
- [ ] `/book` page: Qualification form above fold
- [ ] `/book` page: Scheduler/link shown after successful submit

### Design Acceptance Criteria

- [ ] Consistent container + section spacing (py-12/py-16)
- [ ] Typography hierarchy: hero 3xl–5xl, readable body
- [ ] Buttons: primary + secondary with hover + focus-visible
- [ ] Cards: consistent radius + subtle border/shadow

### SEO Verification

- [ ] Canonical URLs via Metadata API
- [ ] `robots.ts` includes sitemap reference
- [ ] `sitemap.ts` includes all pages + dynamic slugs
- [ ] No thin filler pages

### Analytics Events

- [ ] `cta_book_click`
- [ ] `phone_click`
- [ ] `qualification_submit`
- [ ] `qualification_success`
- [ ] `qualification_error`
- [ ] `scheduler_loaded`

### Schema (JSON-LD)

- [ ] Organization (Home)
- [ ] LocalBusiness (Contact)
- [ ] BreadcrumbList (internal pages)
- [ ] FAQPage (where FAQs render)

### Code Commentary

- [ ] 1–2 line header per file: purpose
- [ ] Short "why" comments for non-obvious logic
- [ ] TODOs explicit: `TODO:INPUT` or `TODO:PROD`
